---
title: "IBM Thinkpad T23 and eepro100 and e100 network drivers, so close"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by berlinbrown on 2007-04-01
I am very close to resolving this.  here is the scenario:

I have a thinkpad t23 (800mhz, older laptop), I am trying to get the internal network card to work.  It looks like I have a choice between the eepro100 driver (older) and the newer e100 driver?  The e100 driver is the default and doesnt seem to work properly.

After some readings, the default settings dont work.  So I added the following to /etc/modules (note I am typing from memory, so may not be 100% correct):

alias eth0 e100 eeprom_bad_csum_allow=1

With the e100 (dmesg)
I get the following error:

e100_eeprom_load: EEPROM corrupted.

And 'eth0' is not recognized when I do ifconfig, only 'lo' is.

```
So, I try the other driver:

sudo modprobe eepro100

sudo dhclient eth0

I get an error at dmesg:

eth0: Invalid EEPROM checksum 0x0000, check settings before activating this device.
eth0: 0000:00:03.0, 00:00:00:00. ... IRQ 11

Receiver lock-up bug exists -- enabling work-around.
```



---
but at least with this one I get eth0 up. If I go to ifconfig; eth0 is available, but it doesnt look valid:

Link encap: Ethernet HWaddr 00:00:00:00:00:00
...
... 

The strange part with the eepro100 driver is that if I reboot enough times it may actually work and their is a valid mac address and I can get on the internet.  This has happened twice.


Berlin Brown

---

### Post by chili555 on 2007-04-01
In my T23, e100 works perfectly. When you are trying to use e100, may I assume you are blacklisting eepro100? It may be blacklisted by default, and so to use eepro100, you'd have to un-blacklist it and then blacklist e100.

When you say with e100, you get eth0 up, do you mean you can get an IP address and get on line? If so, I'd just go with it.

Are your BIOS and embedded controller up to date? You might check here: [http://www.thinkwiki.org/wiki/Category:T23](http://www.thinkwiki.org/wiki/Category:T23)

My tendency is to suspect a hardware problem, that is, your eeprom chip is actually corrupted, rather than a driver problem. In that case, your ethernet connection will be hit-or-miss, even if you trick the driver into action. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122117](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122117)

---

### Post by koshari on 2008-05-19
it would appear that even with e100 blacklisted it still loads in 8.04, i have a ethernet port that works with eepro100 when you rmmod e100 and modprobe eepro100 however i just cant get it to load at boot time,

---

