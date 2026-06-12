---
title: "Problem with mountin win shares"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by zeezam on 2008-05-17
I have Ubuntu 8.04 installed and trying to mount win shares with fstab like this:

//192.168.0.2/C$/"MP3 ARKIV 1"/ /media/mp3_arkiv1 smbfs  credentials=/root/.smbcredentials    0    0

//192.168.0.2/C$/"MP3 ARKIV 2"/ /media/mp3_arkiv2 smbfs  credentials=/root/.smbcredentials    0    0

Nothing happends.
I have created the folders in the mount dir and the credentials file with username and pass to the computer with win shares.

What am I doing wrong?

---

### Post by zeezam on 2008-07-22
Any?

I simplify this a little bit.

**fstab**
//192.168.0.7/music  /mnt/music smbfs user=user 0 0

**Try to mount**
root@htpc:/home/htpc# mount /mnt/musik
Password: 
5874: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
root@htpc:/home/htpc# 

The shared folder is from a win xp machine and 'ALL' users have read permission, also the 'htpc' user I have indicated.

Why access denied, which password is it supposed to be? The user htpc is a local user on the xp machine.

---

### Post by superprash2003 on 2008-07-22
in fstab you used /mnt/music but when you tried to mount you used /mnt/musik ..

---

### Post by zeezam on 2008-07-25
> **superprash2003 said:**
> in fstab you used /mnt/music but when you tried to mount you used /mnt/musik ..

What a miss, I used wrong IP. Everything works fine now. :popcorn:

---

