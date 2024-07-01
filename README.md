# Tugas Praktikum UAS { Pertemuan ke 16 } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Oktavia Rizkha Kurniawati|312310509|TI.23.A5|Basis Data|

***Query MySQL Pada Tabel Perusahaan***

![Screenshot 2024-07-01 105444](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/4eb5c14f-5a05-4155-8331-f67fa4df12a3)

## Soal Latihan Praktikum UAS

![Screenshot 2024-07-01 105617](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/d35f97c8-4170-4465-b777-7bc446c7edf3)

# Di bawah ini merupakan perintah dan juga hasil yang di minta

# 1. Menampilkan Nama Karyawan yang Berada di Departemen yang Dipimpin
oleh Manajer dengan Nama 'Rika'

```
SELECT DISTINCT K.nama
FROM Karyawan K
JOIN Departemen D ON K.id_dept = D.id_dept
JOIN Karyawan M ON D.manajer_nik = M.nik
WHERE M.nama = 'Rika';
```
![Screenshot 2024-07-01 110522](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/6cac1dda-454c-4c00-9bcd-9b2aecb914aa)

# 2. Menampilkan Nama Proyek yang dikerjakan oleh Karyawan dari Departemen 'RnD'
```
SELECT DISTINCT P.nama
FROM Project P
JOIN Project_detail PD ON P.id_proj = PD.id_proj
JOIN Karyawan K ON PD.nik = K.nik
JOIN Departemen D ON K.id_dept = D.id_dept
WHERE D.nama = 'RnD';
```
![Screenshot 2024-07-01 110728](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/c73f53a1-88b2-497c-8fbe-8d366b6a2bb0)

# 3. Menampilkan Nama Karyawan yang Terlibat dalam Lebih dari Satu Proyek

```
SELECT K.nama
FROM Karyawan K
JOIN Project_detail PD ON K.nik = PD.nik
GROUP BY K.nik, K.nama
HAVING COUNT(PD.id_proj) > 1;
```
![Screenshot 2024-07-01 110942](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/0e606794-733c-45d7-9e17-ccc65c2190ba)

# 4. Menampilkan Nama Proyek yang melibatkan Karyawan terbanyak.


```
SELECT P.nama, COUNT(PD.nik) AS jumlah_karyawan
FROM Project P
JOIN Project_detail PD ON P.id_proj = PD.id_proj
GROUP BY P.id_proj, P.nama
ORDER BY jumlah_karyawan DESC
LIMIT 1;
```

![Screenshot 2024-07-01 111119](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/d60d5f2e-3109-4df9-8e7a-5696885f7301)

# 5. Menampilkan Nama Proyek yang Diikuti oleh Karyawan dengan Gaji Pokok Kurang dari 3 Juta

```
SELECT DISTINCT P.nama
FROM Project P
JOIN Project_detail PD ON P.id_proj = PD.id_proj
JOIN Karyawan K ON PD.nik = K.nik
WHERE K.gaji_pokok < 3000000;
```

![Screenshot 2024-07-01 111254](https://github.com/oktavia18/praktikum-UAS-2/assets/147913672/705aaec3-8ee2-4156-be15-3896c741b8c1)

# selesai
