---
title: "[SOLVED] network two ubuntu computers"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by werdna5225 on 2007-11-01
I tried the link:

 [https://wiki.ubuntu.com/SettingUpNFS...NFSServerHowTo](https://wiki.ubuntu.com/SettingUpNFS...NFSServerHowTo) 

to network ubuntu computers and for some reason it didn's work for me.  I can ping my two computers but  I do not know how to set up a network between the two.  Is there a gui that  Ican use or does anyone know how to talk me through it?

---

### Post by Deathmoon on 2007-11-01
Have you added the IP address in your firewall (install firestarter for a GUI to change settings to your firewall configuration)?

also, can you post from the hosting machine (server) the file from:
sudo gedit /etc/exports

and from the client:
sugo gedit /etc/fstab

---

### Post by Jose Catre-Vandis on 2007-11-01
how are your two computers connected?

Also a nice simple NFS howto for Ubuntu here:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by werdna5225 on 2007-11-01
I was finally able to get it working using FTP.  Using this link to a how-to

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

However, when it said to use hostname.local, i had to use the ip address of the computer i wanted to connect to.

---

