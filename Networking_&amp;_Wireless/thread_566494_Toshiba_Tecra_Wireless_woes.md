---
title: "Toshiba Tecra Wireless woes"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Christ_Guard on 2007-10-03
Hey my Ubuntu Networking Homies!
   Here is the deal, I am running Ubuntu FF on my Toshiba Tecra Laptop and am having problems with the wireless. It can detect and even connect to networks, but it drops the network connection constantly, normally when it is trying to work and not just sitting idle. I assume this is a driver problem, but me not knowing the first thing about Ubuntu has caused my hunt for drivers to fail miserably, can you help?

Thanks!
    -Christ_Guard

---

### Post by siralphred on 2007-10-03
what is make of your wireless card? If it happens to be broadcom follow this [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless) works great if its inte4965 follow this [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

---

### Post by Christ_Guard on 2007-10-03
how can I find out what my wireless card is? Sorry, I am a n00b!

---

### Post by siralphred on 2007-10-03
lspci -v | less

---

### Post by Christ_Guard on 2007-10-03
Looks like I have:

Ethernet controller: Intel Corporation 82573L Gigabite Ethernet controller

and

Network Controller: Intel Corporation PRO/Wireless 3945ABG Network conection (Rev 2)

---

### Post by siralphred on 2007-10-03
i found this for your wireless card so read through and follow the links u should get it going in no time [http://kerneltrap.org/node/7704](http://kerneltrap.org/node/7704)

---

### Post by floke on 2007-10-03
I have a toshiba tecra - exact same card and it works perfectly - are you sure it's nothing to do with your network?

---

### Post by siralphred on 2007-10-03
> **floke said:**
> I have a toshiba tecra - exact same card and it works perfectly - are you sure it's nothing to do with your network?

Did it work out of box or did you have to install any drivers? if you did can u link to it?

---

### Post by Christ_Guard on 2007-10-03
> **floke said:**
> I have a toshiba tecra - exact same card and it works perfectly - are you sure it's nothing to do with your network?

It's not my network, It does it on all networks, some worse than others... I am trying the above link now =)

---

### Post by floke on 2007-10-04
> **siralphred said:**
> Did it work out of box or did you have to install any drivers? if you did can u link to it?

Worked straight ootb for me. Didn't have to do a thing.
There are some restricted drivers for it - but AFAIK ubuntu installs them by default.

Try - 'iwconfig' from the terminal to see if you are getting anything.
Also - try 'lsmod' (or 'lsmod | more') and ensure you have the ipw3945 module loaded in the kernel.

---

