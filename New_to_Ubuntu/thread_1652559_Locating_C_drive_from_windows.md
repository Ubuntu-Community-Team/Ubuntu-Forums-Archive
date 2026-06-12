---
title: "Locating C: drive from windows"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by mustis81 on 2010-12-25
I have windows 7 and ubuntu 10.10 dual booted. How do I locate the C: drive from windows on ubuntu?

---

### Post by Quackers on 2010-12-25
In Places menu it will be listed as something like 250GB hard drive

---

### Post by amjjawad on 2010-12-25
> **mustis81 said:**
> I have windows 7 and ubuntu 10.10 dual booted. How do I locate the C: drive from windows on ubuntu?

Applications > Accessories > Terminal

then run this command:

```
sudo fdisk -l

```
You can copy the above command and paste it.

You should have something like this:

```
/dev/sdb1   *           1        3264    26218048+   7  **HPFS/NTFS**
```

That should be your Windows Partition.
Sometimes, it's different from PC to PC so it might be sda1 in your case. It depends. Just check with one is NTFS, that would be your Windows Partition.

---

### Post by Verbeck on 2010-12-25
> **Quackers said:**
> In Places menu it will be listed as something  like 250GB hard drive
^ that or
if you installed using wubi, its places>computer>file system>host

---

### Post by 987abcq on 2010-12-25
If you installed Ubuntu using WUBI you will have to mount your file-system (places/file-system) and then go into the folder titled "[FONT="Courier New"]host[/FONT]" to get to the C:/ dirve.

---

### Post by OldBoy44 on 2010-12-25
Thanks Verbeck and 987abcq.

That was exactly what I wanted too!

 :p

---

### Post by mustis81 on 2010-12-25
Thank you all!

---

