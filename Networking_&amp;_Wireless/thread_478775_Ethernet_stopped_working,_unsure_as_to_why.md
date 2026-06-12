---
title: "Ethernet stopped working, unsure as to why"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by thelost on 2007-06-19
hi there, my ethernet stopped working today. To be more exact, I did an update of ubuntu yesterday, turned off my laptop and turned it on today to find that ethernet networking isn't working.

thankfully wireless is still ok, but i would like to know what's going on.

I don't find the ubuntu network applet or settings very helpful. Anyhow. some info

ethtool eth0
[INDENT]
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
[/INDENT]

ifconfig eth0
[INDENT]
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:A2:45:00  
          inet6 addr: fe80::20a:e4ff:fea2:4500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4845 (4.7 KiB)  TX bytes:109036 (106.4 KiB)
          Interrupt:18 Base address:0xc400
[/INDENT]

How do I disable/enable wireless from the command line? Is it taking precendence over ethernet and interfering?

If I do set up network settings to ethernet, it will not aquire an address via DHCP, nor can I ping my router. However I have no problem using dhclient with wlan0 for instance.

I've checked my cabling. It was working yesterday, and the day before, so why should it not be working today?

I would be greatful for an answer, I'm not a fan of wireless, specially unencrypted wireless (I can't change it because it's not mine).

Further info. If I type
dhclient

it will bind to wlan0 and pick up info from the router. However if I specify
dhclient eth0

it will fail

---

### Post by dreadlord_chris on 2007-06-19
what happens when you do a:
```

sudo ifconfig eth0 down && sudo ifconfig eth0 up

```

---

### Post by thelost on 2007-06-19
I've already tried pretty much that. I just did again, making sure to issue ifconfig wlan0 down first.

I then ran dhclient eth0
[INDENT]
Listening on LPF/eth0/00:0a:e4:a2:45:00
Sending on   LPF/eth0/00:0a:e4:a2:45:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/INDENT]

I then brought up wlan0 and ran dhclient wlan0 for comparison

[INDENT]
Listening on LPF/wlan0/00:0e:9b:84:49:17
Sending on   LPF/wlan0/00:0e:9b:84:49:17
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.4 -- renewal in 104885 seconds.
[/INDENT]

---

### Post by dreadlord_chris on 2007-06-19
what kind of router do you have? and have you tried resetting it?

---

### Post by tgalati4 on 2007-06-20
Rats tend to do their chewing at night.

---

### Post by JSpaceCadet on 2007-06-20
Hi there,
I am having what may be a similar problem.  I am not sure of the cause, but posted a workaround that works for me.

[http://ubuntuforums.org/showthread.php?p=2883902#post2883902]("http://ubuntuforums.org/showthread.php?p=2883902#post2883902")

[http://ubuntuforums.org/showthread.php?p=2883902#post2883902](http://ubuntuforums.org/showthread.php?p=2883902#post2883902)


Hope it helps and that you get your network trouble taken care of soon.
Joe

---

