# Portfolio Ade Ramadona — Versi Statis (HTML + Tailwind CSS + JS)

Ini adalah versi **statis** dari project Laravel `portfolio-laravel-ade-ramadona`,
dikonversi agar bisa langsung di-host di **GitHub Pages** (atau hosting statis
apa pun) tanpa perlu server PHP atau database. Styling memakai **Tailwind CSS v4**
yang sudah di-compile menjadi `tailwind.css`, jadi untuk sekadar hosting tidak
perlu menjalankan build.

Tampilan & konten dibuat seakurat mungkin berdasarkan data asli di project
Laravel kamu (seeder profile, experience, skills, projects) dan desain asli
(warna cyan/glassmorphism, font Orbitron/Rajdhani/JetBrains Mono, custom
cursor, particle background, typing effect, dll).

## Isi folder

```
index.html       → halaman utama (hero, flipbook, about, skills, experience, projects, education, contact)
tailwind.css     → HASIL compile Tailwind (jangan diedit manual; ini yang dibaca browser)
src/input.css    → sumber Tailwind: warna/font (theme), animasi, dan beberapa komponen kecil
main.js          → semua interaksi (tema, bahasa, flipbook, form kontak, dll)
avatar.jpg       → foto profil
package.json     → script build (opsional, hanya untuk mengubah desain)
```

> File lama `style.css` sudah tidak dipakai. Hapus dari repository kalau masih ada.

## Cara upload ke GitHub Pages

1. Upload `index.html`, `tailwind.css`, `main.js`, `avatar.jpg`, dan `README.md` ke root
   repository (Add file → Upload files), atau lewat git:
   ```bash
   git add .
   git commit -m "Update portofolio"
   git push
   ```
2. Di repository, buka **Settings → Pages**, pilih branch dan folder `/ (root)`, lalu **Save**.
3. Tunggu 1–2 menit, situs akan tersedia di:
   `https://USERNAME.github.io/portfolio-ade/`

## Mengubah desain (opsional, butuh Node.js)

Class Tailwind ditulis langsung di `index.html`. Setelah mengubahnya, compile ulang:

```bash
npm install        # sekali saja
npm run build      # menghasilkan tailwind.css baru
```

Lalu upload `index.html` dan `tailwind.css` yang baru. Jika hanya mengubah teks
(bukan class), tidak perlu build ulang.

## Catatan tentang perbedaan dari versi Laravel

Karena versi Laravel aslinya menggunakan database, dashboard admin, dan kirim
form kontak lewat backend, beberapa hal disesuaikan untuk versi statis ini:

- **Form kontak** tidak mengirim ke server (karena tidak ada backend). Saat
  disubmit, form akan membuka aplikasi email kamu (`mailto:`) dengan isi
  pesan yang sudah terisi otomatis. Kalau mau form yang benar-benar mengirim
  email tanpa backend sendiri, kamu bisa pakai layanan pihak ketiga seperti
  [Formspree](https://formspree.io) atau [Web3Forms](https://web3forms.com) —
  cukup ganti `action` pada elemen `<form id="contact-form">` di `index.html`.
- **Efek "buku" (flipbook)**: tombol "Lihat Profil" di hero membuka tampilan
  buku 7 halaman (cover, ringkasan profil, keahlian teknis, pengalaman kerja,
  proyek pribadi, pendidikan, kontak) dengan animasi membalik halaman 3D — dibuat
  murni dengan CSS 3D transform + vanilla JS (tanpa library/CDN eksternal),
  supaya selalu jalan dengan andal di GitHub Pages tanpa risiko gagal load.
  Navigasi: tombol ‹ › di pojok kanan atas, keyboard (←/→/Esc), atau swipe
  di HP.
- **Avatar foto profil**: foto asli kamu (`avatar.jpg`, hasil crop dari CV) sudah
  terpasang di cover hero dan cover flipbook — pastikan file `avatar.jpg` ikut
  diupload ke repo GitHub kamu di folder yang sama dengan `index.html`, atau
  foto tidak akan muncul.
- **Tombol "Download CV"** dihapus dari hero karena belum ada file CV yang
  diupload di project asli. Kalau sudah punya file CV (PDF), upload filenya
  ke repository lalu tambahkan tombol link ke file tersebut.
- **Multi-bahasa (ID/EN)** tetap berfungsi lewat tombol di kanan atas — semua
  teks diterjemahkan langsung di browser (JavaScript), tanpa perlu route
  Laravel.
- **Tema gelap/terang** tersimpan di browser (localStorage), sama seperti
  versi aslinya.

## Sumber konten

Semua isi (ringkasan profil, keahlian teknis, pengalaman kerja, proyek pribadi, dan
pendidikan) mengikuti **CV_Ade-Ramadona.pdf**. Jika CV diperbarui, ubah teks di
`index.html` pada section terkait, baik versi scroll maupun halaman flipbook-nya,
dan perbarui atribut `data-id` (Indonesia) dan `data-en` (Inggris).

## Mengedit konten

Semua teks dan data ada langsung di dalam `index.html` (tidak ada database).
Untuk mengubah pengalaman kerja, skill, atau proyek, cari section yang sesuai
di `index.html` (ditandai komentar seperti `<!-- ABOUT -->`, `<!-- EXPERIENCE -->`,
dst.) dan edit teksnya langsung.
