---
title: "install NDISWrapper from desktop"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by jorisdewilde on 2008-12-17
Hi,

I've installed successfully ubuntu on my laptop. Unfortunately, my wireless topcom pcmcia-card is not supported… So I’m unable to connect with the internet.
 
To solve this problem, I’ve found on the internet that I can use the windows95-driver of this card with NDISWrapper ([https://lists.ubuntu.com/archives/ubuntu-nl/2006-January/001026.html](https://lists.ubuntu.com/archives/ubuntu-nl/2006-January/001026.html)) . So I’ve downloaded NDISWrapper and transferred the folder to the ubuntu desktop with a usbsitck.

But now…

How do I install this program? 

Many thanks for your reactions.

---

### Post by starcannon on 2008-12-17
Plug in a network cable or have the install CD in the drive and then:
You can install from the package manager:
System>Administration>Synaptic Package Manager
Search: ndisgtk
Install that package

Alternatively you can install it from a terminal:
Applications>Accessories>Terminal
```
sudo apt-get install ndisgtk
```

If memory serves you'll find the new menu item under:
System>Administration
though it may be under:
System>Preferences

GL and have fun

---

### Post by jorisdewilde on 2008-12-17
Hi, 
thanks for your fast answer.
The trouble is that I don't have a LAN connection or cd, so the synaptic package manager can not find the NDISWrapper. I've downloaded the NDISWrapper on an other computer and putted the folder with the software on the ubuntu desktop by tranfering it with an usb-stick. I thought that I could install it by double clicking the INSTALL-file... I’m still windows thinking I think…

If I put the code in the terminal I get the message that the ndisgtk package was not found…

All the files needed for the installation are on the desktop. Is there an alternative for double-clicking the install file?

---

