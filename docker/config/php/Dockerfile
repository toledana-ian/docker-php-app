FROM php:7-fpm-alpine

WORKDIR /var/www/application/

RUN apk update
RUN apk add build-base bash curl

RUN apk add libpq-dev
RUN apk add libxml2-dev
RUN apk add icu-dev

RUN docker-php-ext-install calendar
RUN docker-php-ext-install intl
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli
RUN docker-php-ext-enable pdo
RUN docker-php-ext-enable pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer
RUN alias composer='php /usr/bin/composer'

RUN composer self-update --2

CMD ["bash", "./docker/config/php/init.sh"]

EXPOSE 9000