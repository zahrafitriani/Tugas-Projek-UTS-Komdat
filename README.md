# Halo selamat datang pada Tugas-Projek-UTS-Komdat

<h1 align="center"><img src="https://repository-images.githubusercontent.com/518134137/a79f79c4-ffe5-4750-ad58-4be748896b07"></h1>


# Navigasi :
[Tim Penulis](#tim-penulis) | [Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Simulasi](#simulasi-penggunaan) | [Review Apps](#review) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:

# Tim Penulis
[`^ kembali ke atas ^`](#)

**Tugas ini dibuat dengan penuh cinta oleh kelompok 6** :

| No. | Nama                               | NIM         |
| --- | ---------------------------------- | ----------- |
| 1   | Ismy Fana Fillah                   | G6401211001 |
| 2   | Muhammad Tegar Santoso             | G6401211086 |
| 3   | Stanislaus Brillant Kusuma Wijaya  | G6401211063 |
| 4   | Zahra Fitriani                     | G6401201038 |

Oiya dalam project kali ini, kami memilih untuk melakukan hosting terhadap :

sumber: (https://github.com/awesome-selfhosted/awesome-selfhosted#pastebins) -> "Hasty Paste"

# Sekilas Tentang
[`^ kembali ke atas ^`](#)
## Berkenalan dengan Hasty Paste
![](https://enchantedcode.co.uk/hasty-paste/assets/showcase.png)
Hasty Paste adalah tempat paste yang cepat atau paste bin yang ditulis dengan Python menggunakan Quart. Biasanya digunakan untuk berbagi log debug dan informasi sejenis untuk membantu para pengembang dalam memberikan dukungan teknis. Tidak diperlukan Database, dan semuanya disimpan sebagai flat file. Hasty Paste menggunakan minimal resource pada Network Attached Storage (NAS) yang kita miliki dan tidak diperlukan JavaScript.

## Mengapa Kami Memilih Hasty Paste?
1. Sering digunakan dalam kegiatan sehari-hari.
2. Ukuran aplikasi yang tidak terlalu besar.
3. Proses instalasi yang cukup sederhana dibandingkan beberapa aplikasi lainnya.
4. Menggunakan bahasa pemrograman python yang sudah umum.

## Fitur Utama Hasty paste
1. Salin dan Unduh Cepat (Paste and Download)      : Memungkinkan kita dengan cepat menempelkan teks dan menyimpannya untuk dibagikan.
2. Akses Publik! Tanpa Perlu Login (Share)         : Orang bisa mengaksesnya tanpa harus mendaftar atau masuk.

## Fitur lain dari Hasty Paste
1. *Random ID*    : Menghasilkan ID acak untuk setiap teks yang kita simpan. Juga, ada opsi ID yang lebih panjang untuk menjaga keamanan.
2. *Atur Durasi*  : Kita bisa membuat teks yang akan hilang setelah beberapa waktu.
3. *Dark mode*    : Tentu saja biar gak silau. 😎
4. *Hightlighter* : Jika kita menempelkan kode, ada pilihan untuk menyoroti sintaksnya agar lebih mudah dibaca.
5. *Tanpa JavaScript* : Berfungsi normal tanpa javascript!
6. *Ringan*  : Dirancang untuk kemudahan akses
7. *Developer Tools* : Memiliki API untuk para developer berinteraksi dengan aplikasi.
8. *Penyimpanan Costum* : Kita bisa memilih jenis sistem penyimpanan yang ingin kita gunakan, baik yang sudah ada atau yang disesuaikan.
9. *Penggunaan Cache* : Aplikasi ini menggunakan sistem cache untuk membuatnya berjalan lebih cepat dan efisien. (Internal & Redis)
10. *Ada Lighweigth Docker* : Ringan yang dapat kita gunakan, sehingga tidak membebani sistem terlalu banyak. (Alpine Linux)

# Instalasi
[`^ kembali ke atas ^`](#)
## Membuat Virtual Machine (Microsoft Azure)
1. Membuat akun microsoft azure dengan email ipb.ac.id
2. Claim student benefit ($100, 365 hari)
3. Membuat recource dan pilih "Ubuntu Server 20.04 LTS"
4. Ketika membuat resource akan diminta mengisi "username" dan "password"
5. Lakukan pengaturan pada bagian "Networking" untuk menambahkan "inbound port rule" pada port 8000 (sesuai port pada aplikasi yang ingin dideploy)

## Setup Docker di VPS
1. Connect ssh pada terminal dengan username dan password ketika membuat recource
    
    ```
    $ ssh compe@20.255.61.144
    compe@20.255.61.144's password: 
    ```

2. Meng-install beberapa package dan setup docker repository
    
    ```
    $ sudo apt update
    $ sudo apt install apt-transport-https ca-certificates curl software-properties-common
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
    $ sudo apt update
    ```

3. Meng-install Docker
    
    ```$ sudo apt install docker-ce```

4. Memberikan akses untuk menjalankan perintah docker ke user
    
    ```
    $ sudo usermod -aG docker  ${USER}
    $ su - ${USER}
    ```

## Buat dan Jalankan Container di VPS
1. Buat folder

    ```
    $ mkdir hasty-paste
    $ cd hasty-paste
    ```

2. Buat file docker-compose.yml
    
    Jalankan command berikut

    ```$ nano docker-compose.yml```
    
    Kemudian paste dengan isi sebagai berikut:
    ```
    version: "3"

    services:
      paste-bin:
        container_name: paste-bin
        image: ghcr.io/enchant97/hasty-paste:1
        restart: unless-stopped
        volumes:
          - data:/app/data
        ports:
          - 8000:8000
        environment:
          - "TIME_ZONE=Etc/GMT+7"

    volumes:
      data:
    ```
    
    Perhatikan bahwa service dijalankan pada port 8000

3. Jalankan Container
    
    ```$ docker compose up -d --build```

4. Service dapat diakses pada
   
   ```http://20.2.232.48:8000/```

# Simulasi Penggunaan
[`^ kembali ke atas ^`](#)

## 1. Buka link yang sudah dihosting
http://20.2.232.48:8000/
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/1227134b-2c6a-4738-930a-643d1d42fa5c)

## 2. Tekan tombol "New Paste"
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/f71b00cb-0fe5-4861-bfad-4430247472f6)

## 3. Lalu Muncul Seperti ini
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/ae20f636-4833-4cb0-9e20-f7aabf496d76)

## 4. Setelah itu langsung isikan saja pesan yang ingin di paste
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/c2550d6d-363e-48cb-a1e7-1913803b508e)

## 5. Jangan lupa atur "Title", "Expiry" dan "Syntax Highliter"
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/fdffc8bb-e9c3-46cf-bb6b-edf34de570ca)
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/6df823ed-9d0d-48f9-9a30-733d843ff245)

## 6. Tadaa! 🥳 paste sudah jadi dan dapat diunduh dengan tombol "Download" dan Share
![image](https://github.com/zahrafitriani/Tugas-Projek-UTS-Komdat/assets/80316854/3f95e302-40f5-4ddd-88de-ade646f52842)

### *Notes : Disana tombol share tidak bisa diclick karena kami menggunakan hosting gratis yang tidak mendapatkan "https" (not secure), namun paste bisa tetap diakses melalui link berikut :*
http://20.2.232.48:8000/yvZ13-iISJr








# Review 
[`^ kembali ke atas ^`](#)
## Membadingkan Hasty Pase dengan Pastebin dan bepasty

## Hasty Paste
Hasty Paste adalah aplikasi web paste bin berbasis Python (menggunakan Quart) yang dirancang untuk menjadi cepat dan minimalis. Diciptakan untuk mudah dijalankan tanpa membebani sumber daya dan tanpa menggunakan JavaScript berlebihan. Hasty Paste menggunakan sistem penyimpanan flat-file yang dapat didistribusikan.

**Kelebihan Hasty Paste**
1. Ringan dan sederhana.
2. Tidak memerlukan database.
3. Akses publik tanpa login.
4. ID acak untuk keamanan.
5. Tema gelap dan pilihan sorotan kode.
6. Tidak memerlukan JavaScript.
7. Antarmuka untuk pengembang dan pilihan penyimpanan yang fleksibel.

**Kekurangan Hasty Paste**
1. Tidak mendukung JavaScript.
2. Tidak ada dukungan database.

## Pastebin
Pastebin adalah situs web yang memungkinkan pengguna menyimpan teks secara online untuk memudahkan berbagi. Umumnya digunakan oleh para programmer untuk menyimpan potongan kode atau informasi konfigurasi. Pastebin memungkinkan pengguna membuat paste publik atau pribadi dengan dukungan penyorotan sintaks berbagai bahasa pemrograman.

**Kelebihan Pastebin**
1. Dukungan untuk berbagai bahasa pemrograman.
2. Pengguna dapat membuat paste publik atau pribadi.
3. Pengelompokan paste dalam daftar atau direktori.

**Kekurangan Pastebin**
1. Pendaftaran diperlukan untuk fitur penuh.
2. Tidak ada opsi paste yang berlaku terbatas waktu pada versi dasar.
3. Pembaruan antarmuka pengguna mungkin kurang responsif.

## Bepasty
Bepasty adalah situs web seperti pastebin untuk setiap jenis file seperti teks, gambar, audio, video, dokumen. Bepasty memiliki fitur untuk dapat mengunggah beberapa file sekaligus, hanya dengan drag and drop.

**Kelebihan Bepasty**
1. Open source.
2. Tersedia dalam berbagai platform.
3. Dapat mengenkripsi data clipboard.
4. Kostumisasi lebih lanjut.

**Kekurangan Bepasty**
1. Pengaturan dan konfigurasi tergolong rumit.
2. Memerlukan pengaturan awal.
3. Kompatibilitas terbatas.
   
## Perbandingan Hasty Paste dengan Pastebin
**Persamaan**
Keduanya merupakan suatu layanan paste bin yang memungkinkan pengguna menyimpan dan berbagi teks secara online

**Perbedaan**
1. Hasty Paste lebih fokus pada kesederhanaan, kecepatan, dan penggunaan minimal sumber daya.
2. Pastebin menawarkan lebih banyak fitur terkait bahasa pemrograman, penyimpanan pribadi, dan pengelompokan paste.

**Kesimpulan**
1. Hasty Paste is a fast and minimal paste bin.
2. Jika pengguna menginginkan solusi yang cepat, minimalis, dan tidak memerlukan banyak fitur tambahan, Hasty Paste mungkin menjadi pilihan yang baik.
3. Jika pengguna memerlukan lebih banyak opsi terkait bahasa pemrograman, penyimpanan pribadi, dan fitur organisasi, Pastebin mungkin lebih sesuai.


## Perbandingan Hasty Paste dengan bepasty
**Persamaan**
Kedua aplikasi ini adalah alat manajemen clipboard yang memungkinkan pengguna menyimpan dan mengakses history clipboard mereka.

**Perbedaan**
1. Hasty Paste adalah aplikasi yang tidak open source, sementara Be Pasty adalah open source.
2. Bepasty menekankan lebih banyak pada keamanan dan privasi, sementara Hasty Paste lebih sederhana dan mudah digunakan.

**Kesimpulan**
1. jika keamanan dan kustomisasi adalah prioritas, Bepasty menjadi pilihan yang lebih baik karena sifat open source-nya.
2. jika mencari solusi yang lebih sederhana dan mudah digunakan, Hasty Paste menjadi pilihan yang baik.

# Referensi
[`^ kembali ke atas ^`](#)
1. https://github.com/awesome-selfhosted/awesome-selfhosted#pastebins
2. https://enchantedcode.co.uk/hasty-paste/index.html
3. https://enchantedcode.co.uk/hasty-paste/index.html
4. https://jagoweb.com/docker--pengenalan-dan-cara-install-docker-pada-vps-ubuntu
5. https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal?tabs=ubuntu