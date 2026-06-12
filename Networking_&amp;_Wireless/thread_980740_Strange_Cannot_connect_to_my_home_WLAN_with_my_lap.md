---
title: "Strange: Cannot connect to my home WLAN with my laptop"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Khorde on 2008-11-13
Hi, 

I've been suffering from a very strange problem and I haven't found anyway to solve it, I hope that you guys will know what the solution is, call me a n00b, slap me in the face, then help me. Deal? Ok, lets go.

I have a Dell Inspiron 6400 laptop with a Ubuntu 8.04 installation and a Windows XP Pro installation. 
When in Ubuntu, the laptop cannot connect to my wireless network at home. 

Here are some facts that puzzle me:

- I can connect to other wireless networks with my laptop from Ubuntu, in fact, I'm writing this post from school, attached to the WLAN of my uni.
- The Windows partition of my laptop can connect to the wlan at home.
- I have another laptop, a Thinkpad X41, with Xubuntu 8.04 which can connect to the wlan at home.

So it's only the Inspiron laptop, only in Ubuntu and only my home network I cannot connect to :/ it is driving me nuts. 
Before I upgraded to 8.04 i used to be able to connect to the wlan at home but only after calling dhclient a million times and trying and waiting for at least a couple of minutes. 

I can't look up what kind of a router I have but it's a Netgear router with wlan , I think it is a MBR814. I can look this up at home.

I have tried looking up various solutions, most include the use of ndiswrapper but it seems that the drivers for my wireless card are already installed.

[quote=lshw]
>sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:70:92:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=130.237.7.127 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:b8:5b:d5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
[/quote]

Help please? I realize that there might be something which I'm completely oblivious to which might have solved my problem in a jiffy, but I'm quite green in the meadows of Linux :)

Just reply if there is any more info you guys need. I'll look up my netgear model when I'm at home.

---

### Post by iponeverything on 2008-11-13
It might be dhclient.

Something to try:

Instead of dhclient try dhcpcd or pump.

I have found some dhcp servers are very picky about the dhcp clients that they will listen too.

sudo apt-get install pump
sudo apt-get install dhcpcd

---

### Post by AndyCee on 2008-11-13
Is it just me - or should the following line:

```
configuration: <snip> wireless=IEEE 802.11a
```
be
```
configuration: <snip> wireless=IEEE 802.11abg
```

Your router shouldn't matter. Is your home network encrypted? Hidden? Just trying to rule out the obvious...

---

### Post by Khorde on 2008-11-13
My home network has a WEP 64 bit encryption (correct term?) and it should be pointed out that my other laptop with xubuntu 8.04 can connect to it and the windows partition as well. 
The network is not hidden since it shows up in all wireless network scanners i have tried on different computers. :)

---

