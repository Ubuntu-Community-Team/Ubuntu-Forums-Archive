---
title: "Help Installing Rt3090 zip file from Mediatek"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by jhaimy on 2014-07-08
Hello, 

I own a HP Pavilion dm1 with 14.04 and inside I have a ralink3090 wifi driver and I'm trying to install the proprietary drivers found on mediateks site.
It comes back as a .zip file and I have no idea how to install this driver. Is there a command line or a way to install it using a graphic interface in Lubuntu? 

Thanks!

---

### Post by Vladlenin5000 on 2014-07-08
Hi, welcome.

Usually there are instruction inside in some "read me" file or something like that. If you have any doubts - you will - or stumble upon compiling errors - most likely - then post it here.

---

### Post by jhaimy on 2014-07-08
I also have the broadcom drivers but Lubuntu won't seem to apply them :(

---

### Post by jhaimy on 2014-07-08
Hi Vlad, 
Thanks! 

I don't have a read me in there.  That's why Im' so confused. I've successfully added a catalyst AMD driver using command line.  Gosh I'm so new to this and feel idiotic speaking but is there a universal method to installing drivers? Or a resource which can teach me to extract .zips and install the driver therein?

---

### Post by Vladlenin5000 on 2014-07-08
> **jhaimy said:**
> I don't have a read me in there.
I meant inside the ZIP file...

> is there a universal method to installing drivers?
I'm afraid there isn't.
A vast majority is already included and works fine. A few manufacturers provide an easy to use DEB file for Debian/Ubuntu and RPM for RedHat and derivatives. Some provide the source code only and that has to be compiled in the target system. Ralink, now Meaditek, used to do the latter.

> Or a resource which can teach me to extract .zips and install the driver therein?
You can easily extract by opening the default file manager of your distro, right-click the file and select the proper option -or- double-click to open. When you do that then you most certainly will find the file with th instructions.

---

### Post by jhaimy on 2014-07-08
Thanks Vlad, 
Also is it at all possible to apply the broadcom driver?  I know its worked fine with other distros i've used but for some reason lubuntu won't apply it.

---

### Post by Vladlenin5000 on 2014-07-08
There are a few pages about it in the stickies. 
I'm definitely the wrong person for broadcoms.

---

### Post by chili555 on 2014-07-08
I suspect the driver is already resident in your system. What do you mean by 'I also have the broadcom drivers but Lubuntu won't seem to apply them'? Do you have a Broadcom device or a Ralink?? The drivers aren't interchangeable.

From a terminal, may we see:```
lspci -nn
lsusb
rfkill list all
```Thanks.

---

