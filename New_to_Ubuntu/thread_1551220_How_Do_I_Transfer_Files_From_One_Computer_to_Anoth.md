---
title: "How Do I Transfer Files From One Computer to Another?"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2010-08-12
I have desktop and laptop connected by a crossover cable; both of which are running 10.04. Is there an easy way to transfer files from one computer to another? 

Thanks

---

### Post by HermanAB on 2010-08-12
Howdy,

The easiest way is with good old FTP.  The securest way is with SSH, the traditional way is with NFS and the most frustrating way is with Samba.  Pick your poison.

You can install proftpd or vsftpd - they work out of the box - do not change the default settings.  Then connect to it using Nautilus (the File menu - connect to server).

---

### Post by Sup3r3g0 on 2010-08-12
Ok, thanks. I'm going to try using proftp. I'll give updates soon

---

### Post by Sup3r3g0 on 2010-08-12
I switched to vsftpd. How do I get access it?

---

### Post by Sup3r3g0 on 2010-08-12
Nevermind. I got it to work with proftpd. My problem was that I wasn't using an ftp client.:redface:

---

### Post by marka101 on 2011-05-07
Hi im noob
I have small computer in the shed i control from front room tell it to down load torrents then transfer them to the computer in front room , it works well, it took me ages to work it out , hope i can save someone the hassle,

on target computer (computer you want to copy files from) enable wake on Lan in the bios

install wakeonlan and secpanel using Ubuntu software centre on both computers

open terminal and type - sudo apt-get install openssh-server        (on both)

system-preferences- remote desktop allow others to view/control , configure network to accept connections
 there may be security issues but im on local network ..its up to you

click on the desktop network icon to find your ip addess and your hardware address write them down,

hibernate target computer ensuring timer working for OS boot option

from destination computer (where you want files copied to) 
open terminal and type - wakeonlan (hardware address)

start secpanel , create profile save it then click transfer icon click profile and connect done
hope this helps):P

---

