<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>


## Laravel

Laravel merupakan framework PHP yang open-source dan berisi banyak modul dasar untuk mengoptimalkan kinerja PHP dalam pengembangan aplikasi web, apalagi PHP adalah bahasa pemrograman yang dinamis dan Laravel disini bisa bertindak untuk membuat web development lebih cepat, lebih aman, dan lebih simpel.

## Clone Project Di Server

Langkah 1 : Masuk ke direktori

```sh
cd /var/www/html
```
Langkah 2 : Clone repository

```sh
git clone https://github.com/saiful2030/ujian-online.git
```
masuk ke link https://github.com/settings/tokens 
kemudian klik button `generate new token`.
untuk `Note` silakan berikan nama token yang anda inginkan dan ini sifatnya bebas. Centang `repo`. Setelah itu klik button `generate Token`.

Langkah 3 : Clone repository dengan token

```sh
git clone https://username-kamu:token-kamu@github.com/saiful2030/ujian-online.git
```
silakan ganti :
1. `username-kamu` dengan username akun github
2. `token-kamu` dengan token hasil generate di atas

Langkah 4 : Konfigurasi Project

```sh
cd ujian-online
```
```sh
ls
```
```sh
composer install
```
```sh
Command 'composer' not found, but can be installed with:
apt install composer
```
```sh
apt install composer -y
```
```sh
composer install
```
```sh
cp .env.example .env
```
```sh
php artisan key:generate
```
```sh
sudo chown www-data: -R storage
```

Langkah 5 : Membuat Database

```sh
mysql -u root -p
```
```sh
mysql> CREATE DATABASE db_ujian_online;
```
```sh
mysql> SHOW DATABASES;
```
```sh
mysql> exit;
```
Langkah 6 : Konfigurasi Koneksi Database

silakan masuk ke dalam folder project kita yang di server, yang di direktorinya adalah `/var/www/html/ujian-online`
```sh
sudo nano .env
```
silakan ganti :
1. `APP_ENV` menjadi `APP_ENV=production`
2. `APP_DEBUD` menjadi `APP_DEBUG=false`
3. `DB_DATABASE` menjadi `DB_DATABASE=db_ujian_online`
4. `DB_PASSWORD` menjadi `sesuai password yang anda seting`

silakan simpan dengan `CTRL`+ `X` kemudian `Y` dan `ENTER`

```sh
php artisan migrate
```
```sh
php artisan db:seed --class=UserTableSeeder
```
Langkah 7 : Konfigurasi Vhodt Nginx

```sh
sudo nano /etc/nginx/sites-available/default
```
```sh
root /var/www/html;
```
```sh
root /var/www/html/ujian-online/public;
```
```sh
try_files $uri $uri/ =404;
```
```sh
try_files $uri $uri/ /index.php$is_args$args;
```

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
