FROM php:7.0-apache

ADD site.conf /etc/apache2/sites-available/000-default.conf
ADD php.ini /usr/local/etc/php/php.ini
RUN a2enmod rewrite

RUN apt-get update && apt-get install -y zlib1g-dev git unzip

RUN pecl install xdebug
RUN docker-php-ext-install sockets zip

# composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
	&& php composer-setup.php --install-dir=/bin --filename=composer \
	&& php -r "unlink('composer-setup.php');"

RUN apt-get -y install nano mc

WORKDIR /var/www/html
