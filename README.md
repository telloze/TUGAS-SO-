# Praktikum 5: Job Control

**Eka Prasetya Adi Nugraha/ 09030282428041 / TK2B**

## Jawaban Tugas

### 1. Eksekusi Seluruh Profile yang Ada

#### a. Edit `/etc/profile`
Tambahkan baris berikut:
```bash
sudo nano /etc/profile
```
Tambahkan:
```bash
echo "Profile dari /etc/profile"
```
![image](https://github.com/user-attachments/assets/1c3009fa-2e24-4f4d-9414-0c75d4cbb544)

#### b. Edit Profile Pengguna
```bash
nano /home/stD02001/.bash_profile
```
Tambahkan:
```bash
echo "Profile dari .bash_profile"
```
Lakukan hal yang sama untuk:
```bash
nano /home/stD02001/.bash_login
```
```bash
nano /home/mahasiswa/.profile
```
```bash
nano /home/mahasiswa/.bashrc
```

#### c. Jalankan Perintah Berikut
```bash
su mahasiswa
exit
su - mahasiswa
exit
```
**Perbedaan:**
- `su mahasiswa` mengganti user tanpa memuat profile shell.
- `su - mahasiswa` memuat profile shell seperti login baru.

---

### 2. Prompt String (PS)

a. Edit `.bash_profile`:
```bash
nano ~/.bash_profile
```
Tambahkan:
```bash
PS1="> "
export PS1
```

b. Eksperimen PS1:
```bash
PS1="\! > "  # Nomor perintah
PS1="\d > "  # Tanggal
PS1="\t > "  # Waktu
PS1="Saya=\u > "  # User
PS1="\w > "  # Direktori kerja
PS1="\h > "  # Hostname
```

---

### 3. Logout
Edit `.bash_logout`:
```bash
nano ~/.bash_logout
```
Tambahkan:
```bash
echo "Terima kasih atas sesi yang diberikan"
sleep 5
clear
```

---

### 4. Bash Script

a. Buat script:
```bash
nano p1.sh
```
Isi:
```bash
#!/bin/bash
echo "Program p1"
ls -l
```

```bash
nano p2.sh
```
Isi:
```bash
#!/bin/bash
echo "Program p2"
who
```

```bash
nano p3.sh
```
Isi:
```bash
#!/bin/bash
echo "Program p3"
ps x
```

b. Jalankan script:
```bash
chmod +x p1.sh p2.sh p3.sh
./p1.sh ; ./p3.sh ; ./p2.sh
./p1.sh &
./p1.sh & ./p2.sh & ./p3.sh &
( ./p1.sh ; ./p3.sh ) &
```

---

### 5. Jobs

a. Buat script loop waktu:
```bash
nano pwaktu.sh
```
Isi:
```bash
#!/bin/bash
while [ true ]
do
  date >> hasil
  sleep 10
done
```
Jalankan:
```bash
chmod +x pwaktu.sh
./pwaktu.sh &
```

b. Jalankan `find` di background:
```bash
jobs
find / -print > files 2>/dev/null &
jobs
```

c. Ubah ke foreground, lalu ke background:
```bash
fg %1
^Z  # Tekan Ctrl+Z
bg
```

d. Stop program dengan `kill`:
```bash
ps x
kill [PID]
```

---

### 6. History

a. Ganti HISTSIZE:
```bash
HISTSIZE=20
history
```

b. Edit instruksi ke-5 dari history:
```bash
!-5
```

c. Ulangi instruksi terakhir dan navigasi dengan `Ctrl+P` dan `Ctrl+N`:
```bash
!!
```

Ulangi instruksi tertentu:
```bash
!150
!ls
```

---

**Selesai!**

