---
title: "Change MAC on bcm4318"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by dany_r50 on 2007-05-10
Hello everyone!

I have a problem trying to change the MAC addres of my wireless card bcm4318. I am using the ndiswrapper to apply the windows driver and I have tryed the the following things:

* sudo ifconfig iface down; sudo ifconfig iface hw ether 30:50:10:00:00:00; sudo ifconfig iface up
* macchanger
* changing the config files of ndiswrapper (/etc/ndiswrapper/iface/*.conf

...and got nothing

iface=wlan0 (the one that diswrapper put by default)

I'm using Ubuntu 6.10 kernel 2.6.19.1.linux2.6.19. The bcm43xx linux native driver doesn't connect to the internet (so I don't use it).

Any help is welcome. Thank you in advance.

---

