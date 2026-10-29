# Fufuratu Visuals — VIP Card Verification

Paket website statis untuk mengelola kartu VIP, QR, dan catatan transaksi.

## Fitur
- Tambah/edit kartu VIP dengan nomor unik, pemilik, jenis, tanggal terbit, masa berlaku, status.
- QR unik per kartu dan cetak kartu fisik (dialog cetak browser).
- Verifikasi dengan scan QR (kamera) atau pencarian nama/nomor.
- Aturan diskon: potongan 20% untuk transaksi pertama per kartu per hari; transaksi selanjutnya tagihan penuh.
- Riwayat transaksi, pencarian/filter tanggal, ringkasan dashboard, ekspor CSV.
- Tampilan responsif dan logo Fufuratu Visuals.

## Unggah ke GitHub Pages
1. Ekstrak ZIP ini.
2. Masuk ke GitHub dan buat repository baru, misalnya `fufuratu-vip`.
3. Unggah semua isi folder ini ke root repository. Pastikan `index.html`, `app.js`, `style.css`, dan folder `assets` berada di root.
4. Buka **Settings → Pages**.
5. Pada **Build and deployment**, pilih **Deploy from a branch**.
6. Pilih branch `main` dan folder `/(root)`, lalu tekan **Save**.
7. Tunggu beberapa menit, lalu buka alamat GitHub Pages yang ditampilkan pada halaman Pages.

## Catatan penting sebelum dipakai sungguhan
Versi ini sengaja dibuat tanpa server supaya bisa langsung dipublikasikan di GitHub Pages. Data kartu dan transaksi disimpan di `localStorage` browser yang digunakan:
- Data tidak otomatis sinkron antarperangkat atau antar-browser.
- Menghapus data situs/browser dapat menghapus catatan; ekspor CSV secara rutin.
- Tidak ada login admin atau perlindungan data sisi server.
- Kode QR berisi nomor kartu, bukan bukti kriptografis atau validasi online.
- Jika dua kasir/perangkat perlu mencatat kartu yang sama, gunakan backend/database online dengan autentikasi dan validasi transaksi atomik sebelum operasional sungguhan.

## Library eksternal
QR generator dan scanner dimuat dari CDN saat website dibuka, sehingga fitur QR membutuhkan koneksi internet. Fitur scan memerlukan HTTPS dan izin kamera. GitHub Pages menyediakan HTTPS.

## Kebijakan diskon
Sistem memberi diskon 20% hanya jika kartu berstatus aktif, belum kedaluwarsa (jika tanggal berlaku diisi), dan belum mendapatkan diskon pada tanggal lokal perangkat yang sama. Jika sudah pernah mendapat diskon, transaksi tetap direkam dengan potongan Rp0 / tagihan penuh.
