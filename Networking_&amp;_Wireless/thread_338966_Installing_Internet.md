---
title: "Installing Internet"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Timmy123 on 2007-01-15
Hey, Im brand new to Ubuntu and Linux in general, and im having trouble accessing the internet on it. Ive got XP as well, and the internet is working fine, but I cant get it on Linux. Ive gone into the networking part of it and and set up my Cable (no router) as DCHP and auto IP. Ive tried static IP etc and I cant seem to get it to work.

Also, I read a couple of the other threads but it was only explained in all this coding that I didnt understand, so if u can only help with coding, can u please explain to me how to implement it? 

Thanks alot.

---

### Post by Metaljaz on 2007-01-15
Start here:

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

Keep us posted as to your results.

---

### Post by Timmy123 on 2007-01-15
Hey, thanks but it still doesnt pick it up.

I typed in

sudo pppoeconf and it shows an Eth0, but when I clicked Yes, it wouldnt work

Its plugged in through the motherboad (VIA Ethernet Adapter), without a router.

---

### Post by Timmy123 on 2007-01-15
Im thinking I need a Driver.

Does anyone know where I can get a Linux compatible Driver for a VIA Compatable Fast Ethernet Adapter.

Thanks.

---

### Post by NeoLithium on 2007-01-15
The via drivers are in the kernel (I have the same adapter for mine).  I'm just looking up the stuff for you now to help you out :)  I'll post back shortly :)

---

### Post by NeoLithium on 2007-01-15
Hehe, I have ppoe so I actually had to hunt around; you should be able to set it up going into settings; and I think in administration, is where your network settings are; just enable DHCP that way on eth0; and you should be able to go ok with it.

---

### Post by Timmy123 on 2007-01-15
I disabled, enabled, disabled, enabled about 5 times and it still doesn't work. It sees the Eth0, but it can't pick it up for some reason.

---

