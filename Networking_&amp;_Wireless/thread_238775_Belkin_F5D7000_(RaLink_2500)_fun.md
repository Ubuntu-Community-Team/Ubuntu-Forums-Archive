---
title: "Belkin F5D7000 (RaLink 2500) fun"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by gkcj on 2006-08-18
Hi all.

I just moved into a new house and only have wireless Internet access.  I'm new to all this wireless stuff, but I got a Belkin F5D7000 after reading that it works out of the box with the GPL RaLink 2500 driver on Ubunutu 6.06.1 LTS.

Well, needless to say, it didn't...

In order to make it work, I had to blacklist ipv6 (`blacklist ipv6' in /etc/modprobe.d/blacklist-ipv6), and on *every* boot:

1) Run the System|Network tool and disable the (now unused) ethernet card.

2) Enable the ra0 device.  This fails after a couple of minutes when dhclient appears not to receive any replies, but at least it gets the card's LEDs glowing!

3) Run the following commands (as root), while the graphical tool is still running:
---
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=SHARED
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=*****
iwpriv ra0 set SSID=*****
dhclient ra0
---
The set SSID command fails if I don't run the graphical tool previously, and dhclient will fail if the card's LED isn't on after the previous step.

This usually works (not always), but the network often only stays up for a few minutes at a time.  Once it disconnects (the LEDs on the card cut out), or if the commands above fail, the only way I've found to regain Internet access is to reboot and start over.

Does anyone have any ideas of how to get the ra0 interface up automatically, and make it stay up?  Unfortunately I don't have wired access on that machine, or Windows to compare with.

Many thanks for any help, I'm completely stumped!

Gareth

---

### Post by ComplexNumber on 2006-08-18
>  In order to make it work, I had to blacklist ipv6 (`blacklist ipv6' in /etc/modprobe.d/blacklist-ipv6), and on *every* boot: you don't need to do that. go to firefox. in the address bar, type in about:config. search for "v6". disable it. 

> 
Does anyone have any ideas of how to get the ra0 interface up automatically i'm using using ralink 2500 on fedora. initially i spend a while trying to get things to work. since then, i've done a few reinstalls to set up my partitions properly. i hghly recommend that you install the following programs:
network manager
wifi-radar
ndiswrapper
kmod-ndiwrapper
ndiswrapper-kmdl

i suspect that you're probably using ndiswrapper, but i don't know for sure. if ubuntu supports it, then there is no need for ndiswrapper. when i tried ubuntu dapper, i couldn't get wireless card to work, so i went back to fedora.

---

### Post by lupine_nickt on 2006-08-18
The file you're looking for is /etc/network/interfaces - you want to make it look a bit like this:-

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Comment out the wired network card - that'll stop it from being configured at boot.
#auto eth0
#iface eth0 inet dhcp

auto ra0
iface ra0 inet <dhcp|static>
        address xx.xx.xx.xx # Only if static
        netmask xx.xx.xx.xx # Only if static
        broadcast xx.xx.xx.xx # Only if static
        gateway xx.xx.xx.xx # Only if static
        dns-nameserver xx.xx.xx.xx # Only if static        
        wireless-essid bobsyouruncle
        wireless-ap xx:xx:xx:xx:xx:xx # MAC address of the AP
        wireless-key wepkey

```

Edit it as root (e.g. "kdesu kate /etc/network/interfaces", for Kubuntu), then save and reboot (or run ifdown followed by ifup -a, but a reboot is cleaner). 

xF,

...Nick

---

### Post by gkcj on 2006-08-18
Thanks ComplexNumber and Nick!

Nick's solution has the thing working on boot.  Now I'll see how long it stays up for. ;) 

I'm using the rt2500 driver not ndiswrapper, but if I still have problems I'll probably try that instead.

Gareth

---

### Post by lupine_nickt on 2006-08-18
As I pointed out [here](http://www.ubuntuforums.org/showthread.php?t=237369), make sure you're using an up-to-date version of the driver! Regarding the bloody things switching off, check [here](http://www.ubuntuforums.org/showthread.php?t=235450)

To find out which version of the driver you're using, run:-
```
strings `slocate rt2500.ko` |grep "description"
```

xF,

...Nick

---

