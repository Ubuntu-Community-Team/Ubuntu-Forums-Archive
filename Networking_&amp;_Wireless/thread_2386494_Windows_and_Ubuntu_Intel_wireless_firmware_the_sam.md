---
title: "Windows and Ubuntu Intel wireless firmware the same?"
date: 2018-03-06
forum: Networking &amp; Wireless
---

### Post by roofusthedoofus1 on 2018-03-06
Hi everyone,

I have a dualboot Windows 8.1 and Kubuntu 17.10 with Intel Wireless 7260 - Rev 6b.

My internet is very unstable and unreliable, and after researching the problem i suspect it's the firmware.  Installing firmware through Ubuntu seems a little complex and open to me messing things up.  

So if I installed the firmware through windows, would this mean that I wouldn't need to install it for Ubuntu?

Any help would be appreciated, thanks!

---

### Post by chili555 on 2018-03-06
Please see: [https://askubuntu.com/questions/1012515/are-windows-and-ubuntu-wireless-firmware-the-same](https://askubuntu.com/questions/1012515/are-windows-and-ubuntu-wireless-firmware-the-same)

I don't know if they are the same or similar, I haven't any Windows here. I *do* know that my 7260 is fast and stable. 

Do you have any files named *ucode* on Windows?

---

### Post by kerry_s on 2018-03-06
of course there not the same, linux is the third class citizen. i'm sure they put more effort into win & mac drivers.

most firmware is done in the kernel, the newer the kernel, the better supported. in theory anyways.

---

### Post by jeremy31 on 2018-03-06
Only the Intel people would know if the firmware was the same as they are the ones that commit the firmware to the upstream linux-firmware package.  It depends on the kernel as to what the lowest and highest firmware version is used as that info is in the iwlwifi source code

---

### Post by roofusthedoofus1 on 2018-03-11
Thanks a million everyone for their replies, indeed i followed the instructions on the link provided by Chili555 (which was my original question on another site)  and my internet has definitely improved.  Don't think i'll be messing around with firmware updates any time soon.

---

