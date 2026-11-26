# EventHub – Event Management + QR Check-in (Laravel 11/12)

## Instalasi
```bash
composer create-project laravel/laravel eventhub && cd eventhub
composer require simplesoftwareio/simple-qrcode barryvdh/laravel-dompdf maatwebsite/excel

# salin isi folder ini (app, bootstrap, database, resources, routes) ke dalam proyek, timpa file yang sama

# .env
#   APP_LOCALE=id
#   APP_TIMEZONE=Asia/Jakarta
#   DB_CONNECTION=sqlite  (atau mysql)
#   MAIL_MAILER=log       (dev: email tampil di storage/logs/laravel.log; produksi: smtp)

php artisan migrate --seed
php artisan storage:link
php artisan serve
# Scheduler (pengingat H-1 & sinkron status): php artisan schedule:work
```
Akun demo (password: `password`): admin@eventhub.test, panitia@eventhub.test, peserta@eventhub.test

## Catatan
- QR berisi `KODE|TANDA_TANGAN(HMAC)` → QR palsu ditolak saat scan.
- Email dengan QR bentuk PNG butuh ekstensi PHP `imagick`; tanpa itu email tetap memuat kode tiket + tautan ke tiket digital.
- Tiket berbayar: harga tercatat, belum ada payment gateway (bisa ditambah Midtrans/Xendit).
- Panitia hanya melihat/mengelola event miliknya; admin melihat semuanya.
