---
title: "Viewing Ubuntu on a different computer?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by wok951 on 2008-05-27
I was wondering if there is a way to view Ubuntu on a different computer that runs Win XP Home. If there is a way can someone help me out on how to set that up. Thank You.

---

### Post by tamoneya on 2008-05-27
it depends on exactly what you mean by "view" but generally when people want to view their comptuer from win XP it means that they need to install samba.```
sudo apt-get install samba samba-client
```

---

### Post by jrusso2 on 2008-05-27
You could install one of the VNC servers on the Linux box and a VNC viewer on the xp box.

Either regular VNC or if your more security wary and if your not behind a firewall you probably want tightvnc

[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)


[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by mankygitt on 2008-05-27
Use Vnc:

Simple stuff:

Set up Ubuntu first: (assuming you're running Ubuntu for desktop (7.0.4, 7.10, 8.0.4)
============
To enable this on Ubuntu: System > Preferences > Remote Desktop.. This applet should be fairly self explanatory.

Windows
======
Find and install a VNC application. There are many.
Try tucows.com, download.com or majorgeeks.com for a source.
Once installed, simply "call" the Ubuntu machine.
This will give you remote desktop access just like you were sitting at it.

More Advanced Stuff:
Now you're up and running: You'll probably want to enable file-sharing between the two machines.
If you're a Windows type, use windows file sharing on the windows machine, and access it from ubuntu - Note, you'll not be able to do things with files over 2Gb.

A better alternative is learn how to set up Samba on your ubuntu machine and access it from Windows.
Linux File systems are tidier, more efficient, etc, etc, etc

Happy networking!!

---

### Post by wok951 on 2008-05-27
How would i "call" the Ubuntu machine for vnc server. If I were to install samba, will it have to be on both machines?

---

### Post by Iowan on 2008-05-28
Ubuntu usually comes with the Samba client installed, but to share files with a windows machine, the Samba server would need to be installed on Ubuntu.  The windows box could stay fat, dumb, and... well, I guess that pretty well describes it. Samba lets Ubuntu (or other Linux boxes) speak "Window-ese" - Windows already speaks it.  

If you opt to go the Samba route, I've referenced some good How-To's [here]("http://ubuntuforums.org/showthread.php?t=810619").

---

