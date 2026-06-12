---
title: "Ubuntu 8.10 Installation stuck at 99%"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by xItachi on 2009-02-10
So I'm trying to install 8.10 on my friend's laptop, but the installation gets stuck at 99% and it seems like nothing is happening.

'Running post-installation trigger libc6'

Any ideas? Thanks

---

### Post by jrusso2 on 2009-02-10
How long did you let it run for?  Its almost done.  Maybe it will finish if you leave it run.

---

### Post by cerpin on 2009-02-10
It could be a problem with the disk. what burn speed did you use?

if its too high it could create errors. you should be burning it at the lowest speed possible, it will take awhile but it will burn it correctly.

you could, also try running a cd error check. just to see if its the cd or something else.

Edit: also check the download hash, might have been a bad download

---

### Post by Michael.Godawski on 2009-02-10
hi,

patience, man. 

Either you have to wait some few minutes according to the performance of you laptop or you should check the CD for integrity.

The last percent may be the longest one, as far as I remember correctly :)

---

### Post by xItachi on 2009-02-10
Actually, it's been running for about 2 hours at 99% haha.  I'm not installing it with a CD, but rather with a USB startup disk that I made with my 8.10 on my own laptop.  His laptop's cd drive is broken, so it can't read discs.  Also, is it possible to install Windows without a cd? It would be much easier for him to use Windows =p

---

### Post by Rivindu Prasanga Perera on 2009-02-10
If installing inside window, this is because of not enough space in hard disk.
If installing full version please switch off the machine(nothing to do) and try again.

---

### Post by bakz on 2009-08-11
I've got the same problem also. Any help would be appreciated. By the way, I installed it using vmware. I installed pclinux in vmware and it was successful however I've decided to switch to ubuntu but not successful. I tried to reinstall many times but still I got stuck on this problem.

---

### Post by manish0233 on 2009-11-10
I tried to install ubuntu on my machine on a separate HDD (using a CD) and then using VM ware (using the ISO file), however the installation got stuck at 99%.

Don't know what to do.
Please help.

---

### Post by CaptainMark on 2009-11-10
you should check the iso file, this is easy to do just type into the terminal ```
md5sum <file name>.iso
``` then compare the nice long code you get given back against the entry for your file type here[ https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")
if your like me youve got the usb install off an old cd you had hanging around and may not the original iso, in which case your best downloading a new one and start again

---

