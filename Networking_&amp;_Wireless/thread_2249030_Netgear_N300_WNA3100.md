---
title: "Netgear N300 WNA3100"
date: 2014-10-19
forum: Networking &amp; Wireless
---

### Post by thedoctor2016 on 2014-10-19
I've been trying to install the necessary drivers for my N300 to work and I've followed post #29 on page #3 from [this thread]("http://ubuntuforums.org/showthread.php?t=1695036") and everything works except when I run ```
ndiswrapper -l
``` I get ```
bcmwlhigh5 : invalid driver!
``` and when I run autostart.exe from the CD provided when I bought the adapter and click setup and install from CD (the other option doesn't work but it's not a big deal) it says it's installing something and then nothing happens anymore and when I try to run it again it says another instance is already running, please wait for the other instance to finish and try again and the only way to get rid of it that I found is to restart my computer. Any help would be appreciated.

---

### Post by ajgreeny on 2014-10-19
You will not get autostart.exe to run; that is a windows program and nothing to do with using the driver in Ubuntu.

You need to open the CD using your file-manager (nautilus/thunar or whatever) and copy the folder with the Win XP drivers from that onto your hard disk, somewhere in your home.

Now when you run the driver installation you need to point it to the WNA3100.INF file, (or similarly named file), that should be in the folder.

I suggest that you install **ndisgtk** to do the installation, if you don't already have that package.

---

### Post by jeremy31 on 2014-10-19
You might need this file instead [http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

---

### Post by thedoctor2016 on 2014-10-21
Thank you to both of you, I have everything set up now and can connect to the internet :)

---

