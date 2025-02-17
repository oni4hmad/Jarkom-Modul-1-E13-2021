# Praktikum Modul 1 20 September 2021

## Anggota Kelompok E13
05111940000090	Ihsannur Rahman Qalbi

05111940000003	Fairuz Hasna Rofifah

05111940000164	Ahmad Aunul Ma`bud

## 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!
Melakukan display filter `http.host contains "ichimarumaru.tech"`. Kemudian Follow TCP Stream, didapat:

![description](/img/image9.png)

![description](img/image19.png)

Didapat server: nginx/1.18.0 (Ubuntu)
## 2. Temukan paket dari web-web yang menggunakan basic authentication method!
Melakukan display filter `http.authbasic`, kemudian didapat paket-paket yang memakai authentication basic.

![description](img/image25.png)

## 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
Melakukan display filter `http.host contains "basic.ichimarumaru.tech"`. Kemudian mencari paket yang memiliki authorization, kemudian didapat credentialnya adalah `kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN`

![description](img/Capture.PNG)

Kemudian mengunjungi basic.ichimarumaru.tech dan memasukkan credential, kemudian menyelesaikan misi pada web tersebut.

![description](img/image7.png)

## 4. Temukan paket mysql yang mengandung perintah query select!

Melakukan display filter `mysql contains "select" || mysql contains "SELECT"`.

![description](img/image22.png)

## 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Melakukan display filter `mysql contains "insert" || mysql contains "INSERT"`.

![description](img/image28.png)

Kemudian Follow TCP Stream, didapat username dan passwordnya, `akakanomi:pemisah4lautan`.

![description](img/image23.png)

Kemudian login ke portal.ichimarumaru.tech dan jalankan misi.

![description](img/image10.png)

## 6. Cari username dan password ketika melakukan login ke FTP Server!

Melakukan display filter `ftp.request.command == USER || ftp.request.command == PASS`. Kemudian didapat username dan passwordnya, `secretuser:aku.pengen.pw.aja`.

![description](img/image29.png)

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Melakukan display filter `ftp-data contains "Real.pdf"`.

![description](img/Capture2.PNG)

Kemudian follow -> TCP Stream -> show data as raw -> save as “Real.pdf”

![description](img/Capture3.PNG)

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Melakukan display filter `ftp.request.command == STOR`.

![description](img/image11.png)


## 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
Melakukan display filter `ftp-data.command contains "secret.zip"`.

![description](img/image18.png)

Kemudian Follow TCP Stream -> Show data as raw -> Save as secret.zip.

![description](img/image27.png)


## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
Melakukan display filter `ftp-data.command contains "history"`. Kemudian dari paket itu didapat info ada file **bukanapaapa.txt**, cari file dengan `ftp-data.command contains "bukanapaapa.txt"`. Kemudian Follow -> TCP Stream, didapat sebuah teks password, `d1b1langbukanapaapajugagapercaya`. Masukkan password untuk mengextract **secret.zip**.


![description](img/image12.png)

![description](img/image14.png)

![description](img/image21.png)

![description](img/image2.png)

## 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
a.  Menggunakan `src port 80` pada capture filter

![11a](https://image.prntscr.com/image/cHvNUb_ORc-fdr2SAhEjIg.png)

b.  Membuka [monta.if.its.ac.id](monta.if.its.ac.id) untuk mendapatkan packet yang berasal dari port 80

![11b](https://image.prntscr.com/image/50QLTsFIQSyDQwUN4LIjoA.png)

## 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
a.  Menggunakan `port 21` pada capture filter

![12a](https://image.prntscr.com/image/K9ekrguLTfiFdQQjnJ0tQA.png)

b.  Membuka `ftp://ftp.adobe.com` untuk mendapatkan packet yang mengandung port 21

![12b](https://image.prntscr.com/image/jToS3jsMStCdU67A_sh2Lg.png)

## 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

a.  Menggunakan `dst port 443` pada capture filter

![13a](https://image.prntscr.com/image/hGxErsvOQVaZITF_1ikq1A.png)

b.  Membuka [https://www.its.ac.id](https://www.its.ac.id) untuk mendapatkan packet yang menuju port 443

![13b](https://image.prntscr.com/image/KtkwDhoPSfSYS1hUaoTY5w.png)

## 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

a.  Menggunakan `dst host kemenag.go.id` pada capture filter

![14a](https://image.prntscr.com/image/sJaCWKiqRbefnQYKRQChGA.png)

b.  Membuka [kemenag.go.id](https://kemenag.go.id) untuk mendapatkan packet yang tujuannya ke [kemenag.go.id](kemenag.go.id)

![14b](https://image.prntscr.com/image/HBp8xUqITiCdp3g69ZZ0Wg.png)



## 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

a.  Menggunakan `ipconfig` pada cmd untuk mendapatkan ip kita

![15a](https://image.prntscr.com/image/YxJkY4GZRrOeWe2mCUYJ8Q.png)

b.  Menggunakan `src host 192.168.1.5` pada capture filter 

![15b](https://image.prntscr.com/image/hcvu0NeMRs-1ZJ6QKpgxjA.png)

c. Membuka sembarang website untuk mengambil paket yang berasal dari ip tersebut

![15c](https://image.prntscr.com/image/UAA2RWBiQAGw1w6HW2aWXA.png)


## Kendala dalam Pengerjaan
Kendala saat mengerjakan nomor 7, terjebak mendownload pdf yang lain. Karena display filter kurang tepat.

![description](img/image8.png)

![description](img/image24.png)
