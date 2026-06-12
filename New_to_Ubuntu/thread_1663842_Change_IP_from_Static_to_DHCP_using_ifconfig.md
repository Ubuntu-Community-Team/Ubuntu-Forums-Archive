---
title: "Change IP from Static to DHCP using ifconfig"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Zeke501 on 2011-01-10
Hi

I used the command "sudo ifconfig eth0 x.x.x.x netmask x.x.x.x" to change my dhcp ip address temporarily. 
I was wondering if there was a command to change this back to DHCP without having to reboot my pc?

Thanking you in advance

---

### Post by HermanAB on 2011-01-10
Howdy,

It is not an ifconfig function.

To refresh your DHCP address you have to run a DHCP client:
$ sudo dhclient eth0

---

### Post by Zeke501 on 2011-01-10
Hi Herman

Thank you so much for the quick response, that works perfectly

---

