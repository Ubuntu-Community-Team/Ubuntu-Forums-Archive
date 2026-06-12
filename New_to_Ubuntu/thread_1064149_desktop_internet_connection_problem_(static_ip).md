---
title: "desktop internet connection problem (static ip)?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by garyed on 2009-02-08
Everything was working fine until I changed my /etc/network/interfaces file for a static ip for my Apache: 
```

auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.136
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

``` 
Now I have to manually enter "sudo ifup eth0" everytime I reboot my computer to get an internet connection. If I do a "network restart" it takes me off line & I have to use ifup agian. Any one have any ideas what I'm missing? I have two other Ubuntu computers I could check their config but I don't know what other files to look for to edit.

---

### Post by bgates on 2009-02-08
What do you get from ifconfig -a when it first comes up before using ifup?

Is the router set to act as DHCP server?  If so you should configure it so that 192.168.1.136 is outside of its range.

---

### Post by garyed on 2009-02-08
I think I found the problem. I needed to put "auto eth0" also in the interfaces file. So far so good.

---

### Post by bgates on 2009-02-08
Oh yeah, I missed that, heh.  Glad it is working.

---

