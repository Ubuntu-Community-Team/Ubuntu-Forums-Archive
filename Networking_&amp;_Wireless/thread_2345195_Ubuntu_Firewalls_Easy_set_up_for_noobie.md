---
title: "Ubuntu Firewalls Easy set up for noobie"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by jebi on 2016-12-01
hi

i have my pc connected directly to modem, ie no router. so no firewall.

1.      is there a firewall already installed?
2.      if so is there a gui?
3.      is it possible to install NAT and SPI like a router has?
4.      anything else i could you as well like peer guardian?

please i am a noob i cant configure iptables, need something that does that, like just installing zonealarm or even better little snitch? i need to enable openvpn to get thru as well..

mny thx

---

### Post by Frogs Hair on 2016-12-01
1. yes
2. If you want a GUI use the following.

```
sudo apt-get install gufw  
```

---

### Post by jebi on 2016-12-02
hi

is it possible to install something like windows peer guardian on ubuntu?

also using this gufw could you tell me how to still have a functional os but stop everything that is not essential? still need to use openvpn...

thx

---

### Post by Frogs Hair on 2016-12-04
I have no experience with parental/content control software on Linux and the projects I know of aren't well supported and might have to be compiled .  

 [https://sourceforge.net/projects/peerguardian/](https://sourceforge.net/projects/peerguardian/)

[http://dansguardian.org/](http://dansguardian.org/)

---

### Post by Frogs Hair on 2016-12-06
Another option if using Firefox. 
[https://addons.mozilla.org/en-US/firefox/addon/foxfilter/](https://addons.mozilla.org/en-US/firefox/addon/foxfilter/)

---

