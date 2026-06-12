---
title: "Help! Trouble setting up ndis wrapper"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by carguy0625 on 2005-06-29
I'm following this guide
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
and I'm on step 6 of Compiling from source and I'm getting the following error.

root@Cackler:/usr/src/ndiswrapper-1.2# make deb
/bin/sh: fakeroot: command not found
make: *** [deb] Error 127
root@Cackler:/usr/src/ndiswrapper-1.2#

Does anyone know what I'm doing wrong??

---

### Post by StupidHaiku on 2005-06-29
[QUOTE=carguy0625]I'm following this guide
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
and I'm on step 6 of Compiling from source and I'm getting the following error.

root@Cackler:/usr/src/ndiswrapper-1.2# make deb
/bin/sh: fakeroot: command not found
make: *** [deb] Error 127
root@Cackler:/usr/src/ndiswrapper-1.2#

Does anyone know what I'm doing wrong??[/QUOTE]
 Dependency problem.  Go to kynaptic or synaptic (package manager) and install package 'fakeroot.'  Also, ndiswrapper should be available there too (precompiled, so you don't have to worry about all this compiling junk).

---

### Post by carguy0625 on 2005-06-29
I'm trying to set up the driver and I get this

root@Cackler:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
root@Cackler:~# ndiswrapper -l
Installed ndis drivers:
rt2500  invalid driver!
root@Cackler:~#

What's wrong?

---

### Post by StupidHaiku on 2005-06-29
Your first problem is because you're running as regular user, 'modprobe' needs to be run as root.  Do 'sudo modprobe ndiswrapper' and enter your password.  Next one, I dunno, are you sure you're using the right drivers for your card from the website (not install cd)?

---

### Post by bpender on 2005-07-17
I am getting the same message, even after trying
sudo modprobe ndiswrapper

and besides... this was all attempted from a root shell by using 
sudo -s

I am trying to configure a netgear ma521 for a dell 8500, any help would be greatly appreciated.

-Blake

---

