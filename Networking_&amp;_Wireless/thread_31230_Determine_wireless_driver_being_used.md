---
title: "Determine wireless driver being used"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by outdooricon on 2005-05-02
Well, I did the install and my wireless works really good, except for wpa. So I'm gonna set up wpa _supplicant. Anyways, is there a way that I can determine what wireless driver is being used for my laptop, it should be using madwifi (ath 5211x) but I want to verify for sure.

---

### Post by jshein on 2005-05-02
try this

#lsmod | grep ath_

should return

ath_pci
wlan
ath_hal
ath_rate_onoe

---

### Post by outdooricon on 2005-05-02
ok, i did that and It returned what you said.. so that means I'm using mad drivers?

---

### Post by jshein on 2005-05-02
That it does indeed :)

---

### Post by outdooricon on 2005-05-02
cool, thanks man! you don't happen to have wpa_supplicant working do you?

---

### Post by jshein on 2005-05-02
No I do not. I normally use an orinoco ( 3x better signal strength than my Linksys WPC55AG ) but there is a good howto here

[http://www.mattfoster.clara.co.uk/madwifi-9.htm](http://www.mattfoster.clara.co.uk/madwifi-9.htm)

and here ( for Fedora unfortunatley, but the info is mainly the same for those of us who run without RPM hell )

[http://fedoranews.org/blog/?p=599](http://fedoranews.org/blog/?p=599)

---

### Post by outdooricon on 2005-05-02
Thanks alot for pointing me in these guides directions!

If anyone else is trying to figure out how to set this up... look at the guides

Use synaptic to get wpa_supplicant, the edit the wpa_supplicant.conf like said.

Then run the supp, like the guides say... after that runs, do "sudo dhclient ath0". that will get you an ip (I believe that's what it does), then you are good to go!

I haven't automated this process yet, but I will figure that out.

---

### Post by tungsai on 2007-12-05
here at Purdue we've got some guys that have put together a WIKI specifically for this network, but I bet it helps you out!
[URL="http://wiki.purduelug.org/PAL20Howto#head-2f4b5d4565c984223a35ee8d599aae952f226d0b"]
http://wiki.purduelug.org/PAL20Howto#head-2f4b5d4565c984223a35ee8d599aae952f226d0b[/URL]

TUNGSAI
()xxx[]::::::::::::::::::::>

ASCII SWORDED!!!!!

---

### Post by tungsai on 2007-12-05
...By the way, I did that, and NOTHING SHOWED UP...

So, how do I determine what other driver(s) besides madwifi it's using?

TUNGSAI

---

### Post by kevdog on 2007-12-05
Please post

lshw -C network

This will show you the driver.

---

### Post by tungsai on 2007-12-06
Hi!

Strange... all I see are my hardware drivers:

```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=128.211.176.104 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g

```

Tungsai

()xxx[]:::::::::::::::::>

---

