FROM amazonlinux:2.0.20221210.0

RUN yum update -y && \
    yum install -y \
      shadow-utils \
      && \
    yum clean all

RUN groupadd --gid 998 nginx && \
    useradd --gid nginx --uid 999 nginx

RUN amazon-linux-extras install -y nginx1 && \
    yum clean all && \
    rm -rf /var/cache/yum/*

COPY etc/nginx/nginx.conf /etc/nginx/nginx.conf
COPY etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf
COPY etc/nginx/conf.d/default_ssl.conf /etc/nginx/conf.d/default_ssl.conf

# RUN ln -s /dev/stdout /var/log/nginx/access.log && \
#     ln -s /dev/stderr /var/log/nginx/error.log && \
#     ln -s /dev/stdout /var/log/nginx/access_ssl.log && \
#     ln -s /dev/stderr /var/log/nginx/error_ssl.log

CMD ["nginx", "-g", "daemon off;"]
