---
title: "Dls"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by vagelism on 2011-06-29
Hello to all!
I am using a LIVE usb of DSL to boot on my ASUS eee 900!
Everything seems great but I dont have network at all!
The only interface that the system can see is the lookback!
How can I fix this problem!
Please keep it simple since I am not an expert on Linux!
Thank you!

---

### Post by haqking on 2011-06-29
> **vagelism said:**
> Hello to all!
I am using a LIVE usb of DSL to boot on my ASUS eee 900!
Everything seems great but I dont have network at all!
The only interface that the system can see is the lookback!
How can I fix this problem!
Please keep it simple since I am not an expert on Linux!
Thank you!


mm for hardwired or wireless ?

from what i remember
iface eth0 inet dhcp

for static the
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1 

for ethernet connections where 192.168.0.10 is the IP address you want to assign to your ethernet

wireless will depend on your chipset card etc, atheros and prism i think pretty much all work

you might want to check out their FAQ's and wiki though for definitive, it is a while since i used DSL and it is not always standard

---

### Post by snowpine on 2011-06-29
DSL is dead! It's been several years since DSL had any kind of any update. It uses a 2.4 kernel that has poor support for your EEE hardware.

I recommend Ubuntu or one of its variants (Xubuntu, Lubuntu, etc.)

Good luck! :)

---

### Post by haqking on 2011-06-29
> **snowpine said:**
> DSL is dead! It's been several years since DSL had any kind of any update. It uses a 2.4 kernel that has poor support for your EEE hardware.

I recommend Ubuntu or one of its variants (Xubuntu, Lubuntu, etc.)

Good luck! :)

well said, there is DSL-N which uses 2.6 but still...there are better options nowadays ;-)

---

### Post by collisionystm on 2011-06-29
Puppy linux

---

### Post by vagelism on 2011-06-29
> **haqking said:**
> mm for hardwired or wireless ?

from what i remember
iface eth0 inet dhcp

for static the
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1 

for ethernet connections where 192.168.0.10 is the IP address you want to assign to your ethernet

wireless will depend on your chipset card etc, atheros and prism i think pretty much all work

you might want to check out their FAQ's and wiki though for definitive, it is a while since i used DSL and it is not always standard
The system dont see any interface...so i can not configure them!

---

