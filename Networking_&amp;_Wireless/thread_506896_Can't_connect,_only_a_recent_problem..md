---
title: "Can't connect, only a recent problem."
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by CheshireMac on 2007-07-22
Hey folks. I've been able to connect wifi since I turned my wireless card on, but now it's turned itself off and I can't turn it back on with "iwconfig eth1 power on". It gives the error "Operation not permitted" Any thoughts?

---

### Post by CheshireMac on 2007-07-22
I just thought I'd add here that my NM-applet also doesn't find any hosts. I really need help with this problem folks.. .I have no way to connect my laptop, and only so much time on a wired computer. I thought I had the problem solved a week ago, but since two days ago, I haven't been able to connect wirelessly. It's really annoying since I work from the laptop daily.

---

### Post by burningbunny on 2007-07-22
> **CheshireMac said:**
>  I can't turn it back on with "iwconfig eth1 power on". It gives the error "Operation not permitted" Any thoughts?

Maybe a silly question, but: Did you try "sudo iwconfig eth1 power on" ?

---

### Post by CheshireMac on 2007-07-22
> **burningbunny said:**
> Maybe a silly question, but: Did you try "sudo iwconfig eth1 power on" ?
Not a silly question (I had to double check). I havethough, and it replies with "Input/Output Error". Argh!

---

### Post by kevdog on 2007-07-22
Have you confirmed that the wireless card is turned on?? Either by a switch located somewhere in the case of your laptop or through the BIOS.  

Have you checked dmesg to see if the device is found during boot??  If nothing is listed, it would seem that the device was turned off.

---

### Post by CheshireMac on 2007-07-22
> **kevdog said:**
> Have you confirmed that the wireless card is turned on?? Either by a switch located somewhere in the case of your laptop or through the BIOS. 
 
Have you checked dmesg to see if the device is found during boot?? If nothing is listed, it would seem that the device was turned off.
Where would it  be foud duringBoot? If it's not listed, then yes, I have checked power. I've found a solution the requires me to be wired to thenet. I'm uable to do this now, so I'm wondering if there's anothersolution. I've got access only through a cafe computer with non connections to my main machine. Any thoughts?

---

### Post by kevdog on 2007-07-22
After booting, type
dmesg | more

Its a long file, but look through it and see if you can find anything about wireless interface or your card.

---

