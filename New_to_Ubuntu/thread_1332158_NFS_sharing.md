---
title: "NFS sharing"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by jrev on 2009-11-20
I always used the NFS sharing system in order to synchronize my /home/ documents to another PC of my local network.
This doesn't seem to work anymore with the 9.10 Karmic Koala 
could you tell me why ?

Have you got another way to do the job ? 

Thanks

---

### Post by NickJones on 2009-11-20
Is it a Windows PC? If it is you will need to install SAMBA,
sudo apt-get install samba. 
Can talk you through it if you want.
Nick

---

### Post by Elfy on 2009-11-20
I've got no problems here with nfs.

It might be worth saying what errors you are getting.

---

### Post by jrev on 2009-11-21
> **forestpiskie said:**
> I've got no problems here with nfs.

It might be worth saying what errors you are getting.

Thanks for your answer. the sharing machine is ubuntu kk 9.10, the NFS client is Debian Lenny LXDE

My script is :
> #!/bin/bash
SOURCE_DIRS=/media/nfs/
TARGET_DIR=/home/jean/documents
# monter le repertoire nfs 
mount /media/nfs

rsync -av --del --stats $SOURCE_DIRS "$TARGET_DIR"

umount /media/nfs

echo "Backup Terminé"

when I try to mount /media/nfs on the client I got > System error: no route to host 

no ping from the 2 clients to the server 
ping OK from server to the clients. 

The mounting line in fstab is 
> 192.168.0.1:/home/jean/Documents /media/nfs nfs user, noauto 0   0

---

### Post by Elfy on 2009-11-22
Have you checked that they are beng exported by the server?

I have little experience with NFS to be honest, in fact I had to go back to my old router as a new one I got from my ISP caused issues.

I assume that your fstab line usually works - mine looks ssomewhat different
```
192.168.0.2:/mnt/data /mnt/data nfs rsize=8192,wsize=8192,noexec,nosuid
```

---

### Post by frenchn00b on 2009-11-22
> **jrev said:**
> I always used the NFS sharing system in order to synchronize my /home/ documents to another PC of my local network.
This doesn't seem to work anymore with the 9.10 Karmic Koala 
could you tell me why ?

Have you got another way to do the job ? 

Thanks

this is a picture of the result:
[http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG](http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG)

and run this auto-installer.
[ ...  ]

Enjoy Ubuntu Installers !!

---

### Post by jrev on 2009-11-22
I think before anything the "ping" should be OK between all the machines.
My problem could come from the fact that I recently changed my dial up connection through a router PC to a broad band modem (ADSL type [www.free.fr](www.free.fr))

---

### Post by jrev on 2009-11-22
192.168.0.1:/home/jean/Documents /media/nfs nfs user, noauto 0 0 

this line has been working for years with ubuntu 6.06 onwards
it mounts the Documents folder of my main PC into the /media/nfs folder of the client PC in order to copy the content for back-up

---

### Post by frenchn00b on 2009-11-22
Forget all those nano and complicated things:

use my [installer]("http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu_server_logins.jpg") : 
Here guys I made what I want for installers:

```
  cd /tmp 
wget http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu-samba-nfs-installer.sh
cat ubuntu-samba-nfs-installer.sh  
# in case: sudo apt-get install xdialog
sudo su 
sh ubuntu-samba-nfs-installer.sh  
```
 
 
--
edit:
It is a beta version, and you have no warranties

---

### Post by frenchn00b on 2009-11-22
> **forestpiskie said:**
> Have you checked that they are beng exported by the server?

I have little experience with NFS to be honest, in fact I had to go back to my old router as a new one I got from my ISP caused issues.

I assume that your fstab line usually works - mine looks ssomewhat different
```
192.168.0.2:/mnt/data /mnt/data nfs rsize=8192,wsize=8192,noexec,nosuid
```

```
rsize=8192,wsize=8192
``` is nto needed.
Universities use defaults
defaults is better

---

### Post by Elfy on 2009-11-22
> **frenchn00b said:**
> ```
rsize=8192,wsize=8192
``` is nto needed.
Universities use defaults
defaults is better
Thanks = I was wandering around on google when I managed to get nfs working - consequently it got left as it was.

---

### Post by jrev on 2009-11-22
How do you start the NFS sharing once the Internet connexion sharing is working ?

---

### Post by frenchn00b on 2009-11-22
> **jrev said:**
> How do you start the NFS sharing ?

did you try my script? 
It depends on which one server or client? 
reboot both , it is brutal (in linux) but will do all

---

### Post by jrev on 2009-11-23
> **frenchn00b said:**
> did you try my script? 
It depends on which one server or client? 
reboot both , it is brutal (in linux) but will do all

I would like to know the exact details of your script ...
Thanks :p

Might be interesting to put it in practice ...

---

### Post by frenchn00b on 2009-11-23
> **jrev said:**
> I would like to know the exact details of your script ...
Thanks :p

Might be interesting to put it in practice ...

less script.sh
arrows then
:q

You get a menu and it asks you server, client , and few information. it configures it. it works for fresh installed pc, normally, and not messed up.

---

