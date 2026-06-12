---
title: "Internet connection sharing with only one NIC"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by ihti on 2007-09-15
My goal is to share and limit other computer's internet connection with Ubuntu laptop. There is only one network socket available in this Ubuntu-laptop.

I can get multiple IP address (to be default gateway for other computer) with:
sudo ifconfig eth0:1 192.168.0.33
but firestarter doesn't allow the internet connection sharing by using the same eth0

How could I get this working?

---

### Post by rivalarrival on 2007-09-15
I'd spring 10 bucks and pick up some kind of additional NIC - they are available for USB and PCMCIA and can be had for $10 to $50.

You're basically trying to run a trusted and an untrusted network over the same ethernet switch - that's generally a big no-no.

That said, this (4-year old) guide says that it can be done...
[http://www.linuxjournal.com/article/7175](http://www.linuxjournal.com/article/7175)

Your modem may or may not allow this to work, and if it does, your machines are still open to an untrusted network.  Your local machines will NOT be able to use DHCP addresses - if one manages to grab a dhcp address from the modem, the rest of your network will be offline, and that one machine will completely bypass any restrictions you had placed on it.

You'll save yourself hours of configuration and insanity by getting a second NIC working...

---

### Post by ihti on 2007-09-16
> **rivalarrival said:**
> I'd spring 10 bucks and pick up some kind of additional NIC - they are available for USB and PCMCIA and can be had for $10 to $50.

You're basically trying to run a trusted and an untrusted network over the same ethernet switch - that's generally a big no-no.

That said, this (4-year old) guide says that it can be done...
[http://www.linuxjournal.com/article/7175](http://www.linuxjournal.com/article/7175)

Your modem may or may not allow this to work, and if it does, your machines are still open to an untrusted network.  Your local machines will NOT be able to use DHCP addresses - if one manages to grab a dhcp address from the modem, the rest of your network will be offline, and that one machine will completely bypass any restrictions you had placed on it.

You'll save yourself hours of configuration and insanity by getting a second NIC working...

Thanks, that article helped!!

What I needed was this:
```
sudo ifconfig eth0:1 192.168.0.23
sudo iptables -I INPUT -s 192.168.0.23 -d 192.168.0.22 -j ACCEPT
```
..and setting static ip for windows with default GW 192.168.0.22

In this case I was routing net connection inside firewalled LAN for windows traffic control purpose, so another NAT was not needed and procedure was not unsafe.

---

