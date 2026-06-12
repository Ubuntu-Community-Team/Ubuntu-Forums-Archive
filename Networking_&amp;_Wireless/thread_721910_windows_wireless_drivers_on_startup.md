---
title: "windows wireless drivers on startup"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by absolution87 on 2008-03-11
Hi all,

I have finally got my draft n usb module to connect to my router and access the internet (yay!!!). I have run into a problem though, i am running the driver using the windows wireless drivers front-end for ndiswrapper and im not sure how to make it boot on startup. I have read that writing "ndiswrapper" to the "/etc/modules" can make it work but i wanted to check to make sure that was the case.

Thanks in advance

---

### Post by handydan918 on 2008-03-11
hmph. I woulda thought a simple ```
sudo modprobe ndiswrapper
``` would do it.

---

### Post by absolution87 on 2008-03-11
I was wanting to make it automated. When the computer boots i go to the windows wireless drivers application, and the driver is there and it says the device is present but none of the lights on the usb device are on, i have to remove the driver then reinstall the driver everytime i boot the computer.

---

### Post by kevdog on 2008-03-12
Type this once:

echo ndiswrapper | sudo tee -a /etc/modules

Now it will be loaded during boot!
Enjoy!

---

