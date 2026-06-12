---
title: "new wireless card"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by Stephen47 on 2007-01-05
I scrapped my broadcom wireless mini card and installed an Intel Pro Wireless 3945 What doo I have to do to get my wireless connection working? It is through a Belkin router with Wpa emcryption.

---

### Post by darrenm on 2007-01-05
First question : Edgy or Dapper?

---

### Post by Mba7eth on 2007-01-05
Frist you need to run 
#sudo lshw -C network 
see if your card is configuered to ur system. 
if yes 
just type 
#sudo ifdown eth1 
#sudo ifup     eth1
#sudo dhclient eth1
assuming eth1 is the name of ur wireless card defined by ur system

I did this once i install my card and worked perfectly   :):mrgreen:

---

### Post by Stephen47 on 2007-01-05
I am running Dapper  but am thinking of upgrading.
It does show up as eth 1. but won't configure. I thought woreless connections were supposed to be wlan 0 , wlan 1 etc.

---

### Post by Stephen47 on 2007-01-05
> **Mba7eth said:**
> Frist you need to run 
#sudo lshw -C network 
see if your card is configuered to ur system. 
if yes 
just type 
#sudo ifdown eth1 
#sudo ifup     eth1
#sudo dhclient eth1
assuming eth1 is the name of ur wireless card defined by ur system

I did this once i install my card and worked perfectly   :):mrgreen:

I tried your suggestions and I got a message about no working leases in persistent databases - sleeping. 
The wifi light on my computer is blinking not solid green like it is in windows

---

### Post by Stephen47 on 2007-01-06
bump

---

### Post by odelay on 2007-04-12
I also recently replaced my BCM4311 with an Intel 3945 abg.

I actually didn't have to do anything for it to work.  Just booted up and then enabaled wireless in System Setup (in Kubuntu).  I'm not sure, but I don't think WPA is fully supported for the Intel IPW3945abg.  I could be wrong though...I'm sure there's some work-around.  Try disabling WPA first, and go from there.

---

### Post by odelay on 2007-04-12
You probably also had ndiswrapper running...that might have cause some problems if not properly disabled.  Fortunately for me though, I did a fresh install without using ndiswrapper.

---

