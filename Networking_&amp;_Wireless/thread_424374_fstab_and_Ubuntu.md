---
title: "fstab and Ubuntu"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by PaulClarke on 2007-04-26
Hello,

I'm new to Ubuntu and am trying to set up the mounting of a USB drive connected to a Windows PC on my home LAN.

I have two laptops connected to a home LAN one is running Fedora and the other has just moved to Ubuntu from Windows.  I store a lot of my data on a USB drive connected to the wife's windows PC.  In Fedora I can get the drive to mount using the following line in its fstab

//192.168.0.194/f  /home/paul/usb  cifs  uid=000,auto,defaults  o o

I have tried this in Ubuntu and the drive fails to mount.  To test what could be wrong I have tried some mount options in the terminal and I keep getting the error that 

 "special device //192.168.0.194/f does not exist"

I have tried using the wifes PC name in both FC and Ubuntu and that does not work in either but the IP address does work in FC.

What could be wrong here?

I believe it has something to do with Samba.  Ubuntu does connect to the lan and I can "see" all the PCs both windows and linux in the networked PC window.

Thank you for any assistance anyone can give

Regards

Paul

---

### Post by tturrisi on 2007-04-26
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking)

---

### Post by PaulClarke on 2007-04-28
Hello,

I figured this out via [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Thank you

Paul

---

