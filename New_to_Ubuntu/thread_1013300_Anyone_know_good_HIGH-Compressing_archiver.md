---
title: "Anyone know good HIGH-Compressing archiver"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Art3mis on 2008-12-16
Hi,


Does anyone know a good high compressing archhiver. (linux native please)

is .tar.gz one???

I used tar.gz but the file dosen't get smaller

---

### Post by shae on 2008-12-16
LZMA tends to be a good high-compression format that should integrate with archiver.

```
sudo apt-get install lzma
```

---

### Post by jerome1232 on 2008-12-16
It does depened on what your compressing, many file formats are already compressed or just don't compress well. ie mp3's, jpegs, avi's, essentially all media files are compressed and won't compress much more. That's just an example.

7zip is good (uses lzma actually) Haven't used it personally but I've heard it praised many times.

bzip2 has a higher compression ratio than gzip but is significantly slower.

---

### Post by oldos2er on 2008-12-16
> **Art3mis said:**
> Hi,


Does anyone know a good high compressing archhiver. (linux native please)

is .tar.gz one???

I used tar.gz but the file dosen't get smaller

 What kind of file are you trying to compress?

---

