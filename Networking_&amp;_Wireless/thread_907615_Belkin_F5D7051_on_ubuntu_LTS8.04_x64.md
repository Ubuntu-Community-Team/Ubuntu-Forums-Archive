---
title: "Belkin F5D7051 on ubuntu LTS8.04 x64"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by zain4ever on 2008-09-01
Hi there,
I've been trying to use my usb wireless adapter ([FONT="Courier New"]Belkin F5D7051[/FONT])on ubuntu LTS8.04 x64 for last two days but i havn't been able to configure it properly. I have installed the drivers using ndiswrapper-1.53 and it shows that the hardware is present on the terminal ([FONT="Courier New"]lsusb,ndiswrapper -l[/FONT]) and on the [FONT="Courier New"]ndisgtk[/FONT] window but the usb adapter doesn't blink the green light at all. It can't find any wireless network either. 

There are tons of posts about this wireless adapter on the internet but none of them are up to date. Please help me ](*,)
Thanks.

---

### Post by zain4ever on 2008-09-02
**Is there anybody out there willing to help???**

---

### Post by Kevbert on 2008-09-02
Yopu probably need to install firmware drivers.  Post the terminal output for 
```
lspci
```
so that we know what chipset your Belkin adapter is based on.

---

### Post by zain4ever on 2008-09-02
Hello Kevbert, as I mentioned above my wireless adapter is usb not pci ([FONT="Courier New"]lspci[/FONT] is for pci devices, isn't it?). Anyway this adapter ([FONT="Courier New"]Belkin F5D7051[/FONT]) is based on [FONT="Courier New"]Broadcom BCM4320[/FONT] chipset. Let me know if you have anything for me :) 
Thanks.

---

### Post by Kevbert on 2008-09-02
Sorry, missed the USB bit.  There is a [[COLOR="Red"]guide in the forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=847226") for this device.  Please be aware that USB dongles can be problematic when being set up in Linux.

---

### Post by zain4ever on 2008-09-03
I had followed the same instructions before as described on the link you gave :p thats how i installed the drivers.  But the device won't work properly :(. Though thanks for the link :). Anyway i have uninstalled ubuntu and installed it again using vmware. Now i can use internet on ubuntu and use both system at the same time :D
Thanks.

---

### Post by ugutugut on 2008-10-10
Hi there, am new comer to linux, decided to use ubuntu LTS8.04. 
I'm also have problem with Belkin device F5D7051 for wireless connection.
I follow the instruction on [http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)
The instruction works perfectly on my device, now I can connect to wireless network.
Thank you.

---

