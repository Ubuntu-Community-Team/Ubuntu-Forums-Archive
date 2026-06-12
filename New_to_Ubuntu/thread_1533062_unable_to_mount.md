---
title: "unable to mount"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-17
just did a new install of ubuntu 10.04 and get this error message
undable to mount 252 files system not authorized. how do i correct. note this partition has my music and documents on also note i changed all to ext4 when did new install.tks

---

### Post by MooPi on 2010-07-17
If you changed all the partitions to ext4, you may have just lost all data, which includes music and documents. Try to boot to the live CD you used during install to determine if your files are still intact.

---

### Post by rburkartjo on 2010-07-17
i tried this


ray@ray-desktop:~$ sudo nautilus
[sudo] password for ray: 
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by Serpher on 2010-07-17
Seems like your stuff is "gone". When you delete something it doesn't turn all the bits on the hardrive representing that data back into 0's, the filesystem's records just show that the range of bits where the file was is no longer a file. I am no expert on doing this, and somebody else is going to have to explain this but there are programs out there to recover data in cases like yours. Just don't mess around with that space on your computer right now or you'll be changing bits that was your data.

---

### Post by rburkartjo on 2010-07-17
ser tks will wait for advanced advise

---

### Post by rburkartjo on 2010-07-17
used live cd there is data in there just cant access it. any help will be appreciate./tks

---

### Post by frenchn00b on 2010-07-17
> **rburkartjo said:**
> just did a new install of ubuntu 10.04 and get this error message
undable to mount 252 files system not authorized. how do i correct. note this partition has my music and documents on also note i changed all to ext4 when did new install.tks

sudo su 
cd /
mount 
check what it mounted
 
if you wanna badly force : umount -l (and lost of data)

lsof can tell you who have it mounted in

---

### Post by rburkartjo on 2010-07-17
tks ya'll but all data gone. no problem just music

---

