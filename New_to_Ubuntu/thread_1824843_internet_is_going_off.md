---
title: "internet is going off"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by sedoyksa on 2011-08-14
hello
ubuntu 10.10 maverick
my /etc/network/interfaces
> auto eth0 
iface eth0 inet dhcp
    wpa-driver wired
    wpa-conf /etc/wpa_supplicant/wpa.confdo you need wpa.conf?
Ineta connects all okay.
 but often disconnected. Every 10 minutes
 after turning off doing
> sudo ifdown eth0
sudo ifup eth0
/etc/init.d/networking restartInet again after a reboot works fine
 so service is buggy?
 and must be restarted
 but what?
and i should turn off the cable
and after i write sudo ifdown eth0
i have answer > eth0 is not configured

---

