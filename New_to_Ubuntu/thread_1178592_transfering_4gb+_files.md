---
title: "transfering 4gb+ files"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by c0d4041292 on 2009-06-04
I have some HD movies on my laptop and I was trying to transfer them to my ps3 using a flash drive, when the transfer is almost done I get an error saying that the file is to large?... how can I get these movies to my ps3....i also have a 26GB+ file that I'm going to transfer so it would be nice to have a solution to transfer that also...

---

### Post by binbash on 2009-06-04
Are you using NTFS at flash drive?If not, format as NTFS

---

### Post by mcduck on 2009-06-04
> **c0d4041292 said:**
> I have some HD movies on my laptop and I was trying to transfer them to my ps3 using a flash drive, when the transfer is almost done I get an error saying that the file is to large?... how can I get these movies to my ps3....i also have a 26GB+ file that I'm going to transfer so it would be nice to have a solution to transfer that also...

I bet your flash drive is formatted with FAT file system?

FAT can't handle files larger than 4GB.. Sadly, PS3 can't read anything else than FAT so your only option is to use some media streaming server to transfer the files through network connection.

---

### Post by dje on 2009-06-04
yes, format as ntfs, if the ps3 supports it. your drive is probably fat32 which only supports single file sizes of upto 4gb

dje

---

### Post by binbash on 2009-06-04
sudo apt-cache search mediatomb

---

### Post by c0d4041292 on 2009-06-04
didn't even think of that  >_<

thanks for the quick reply...if ps3 cant read ntfs what programs can I use to transfer files

*edit* didn't see ya there binbash...thanks *edit*

---

### Post by mcduck on 2009-06-04
Mediatomb is quite nice, but you might also want to try "PS3 Media Server" (yes, the developer has quite some imagination when it comes to application names.. ;))

[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")

---

