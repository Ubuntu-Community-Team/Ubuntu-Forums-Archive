---
title: "iwconfig confusion"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by blindjustice on 2006-07-28
Hey, new here to the linux world. I installed Ubuntu 6.06 on a box I have at home with ease however the wireless card (WMP11) by linksys didn't work. So I did some poking on the forums and learned alot but something still doesn't fit. When I enter 'iwconfig' the wireless card is registering as 'eth1'. Shouldn't it be wlan0?

Thanks!

---

### Post by wieman01 on 2006-07-28
Hi, 

The name of the adapter does not play a role, it's important that it's THERE. :-)

If your adapter is installed via the tool called "ndiswrapper" then the name normally is "wlan0". If the system is using RTxxx drivers, then it should be "eth1" as far as I remember.

But the name per se does not play an important role. Does this answer your question?

---

### Post by blindjustice on 2006-07-28
yes, thank you :)

---

### Post by blindjustice on 2006-07-28
new question

Everytime I reboot my machine I have to...

modprobe ndiswrapper

to get it to work. is there a way to get it to stay in the system, i'm guessing the kernal, so that I dont have to keep reloading the damn driver?

---

### Post by wieman01 on 2006-07-29
Yes, there is:

> 
sudo gedit /etc/modules

Then add new line saying "ndiswrapper", save, and reboot.

---

### Post by blindjustice on 2006-07-29
I used ndiswrapper -m and it worked. I would use your suggestion but I tried the aformentioned before checking the forum again :)

thanks again!

---

### Post by wieman01 on 2006-07-29
Alright, it's been a while for me. :-)

---

