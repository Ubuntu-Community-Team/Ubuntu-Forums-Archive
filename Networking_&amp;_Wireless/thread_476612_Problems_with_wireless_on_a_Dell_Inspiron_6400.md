---
title: "Problems with wireless on a Dell Inspiron 6400"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by twuerz on 2007-06-17
Hi all!  Having trouble with my wireless connectivity. I have an Inspiron 6400 laptop with a Dell Wireless 1390 WLAN Mini-PCI Card. When I run sudo lshw in terminal, the driver is recognized, but it says

*-network DISABLED

I also ran the following in Terminal, and received the returns:

lspci | grep Network

0b:00.0 Network Controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

lspci -n

0b:00.0 0280: 14e4:4311 (rev 01)

Thanks for your help!!

---

### Post by nachotronics on 2007-06-18
Hello, there's two ways to use that wlan card on Linux, the first one is installing bcm43xx-fwcutter
```
sudo apt-get install bcm43xx-fwcutter
```
Wich extracts your wireless card firmware from the windows drivers. It does work, but in my case i had less signal range and the speed was limited to 11MBps.
The other way is to use the ndiswrapper kernel module instead of the bcm43xx, this worked better for me. You can get this going following [**_THIS HOWTO_**]("http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390+ndiswrapper"). I used the drivers I'm attaching to this post since the ones from dell.com didn't work.

Hope this helps :wink:

---

