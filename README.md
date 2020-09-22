# Docker image of Wordpress php-fpm with LDAP support
This images stays up to date with the original one but with LDAP support

Forked from dalareo/docker-wordpress-ldap-support

````
FROM wordpress:php7.4-fpm

RUN set -x \
	&& apt-get update \
	&& apt-get install -y libldap2-dev \
	&& rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \
	&& docker-php-ext-install ldap \
	&& apt-get purge -y --auto-remove libldap2-dev
  ````
  
  To build the images just run:
  
  ````
  docker build -t [username]/[imagename] .
  ````
