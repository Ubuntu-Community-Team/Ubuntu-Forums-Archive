---
title: "network card problems"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by kevinalle on 2008-06-04
Hi
I am trying to install a mini server in a rather old machine (PII, 96 MB RAM).
I installed Xubuntu and everything works fine except for the network.
i had an Encore enl832-tx-icnt network card and i thought it didn't work. so I bought a SolTech nl-n01-d.
The first time i turned on the machine, the leds of the back went on, but obviously i didn't have the drivers installed.
so i installed the drivers just as the manual said, and rebooted. since then the leds never went on again and it doesn't work..
I even tried ubuntus live cd but it doesn't seem to recognize it either.
if I do 
"ifconfig", eth0 appears, but it doesn't have any inet address.
"ethtool" says it is working at 10Mbps(??)
"lspci" says Ethernet Controller: Unknown Device
"ifup eth0" says "no DHCPOFFER"

oh, and.. a friend lend me a genius network card which worked perfectly (that is why I thought the Encore wasn't working in the first place)

the computer is connected to a router that forks fine.
I have tried quite a lot of things with ifconfig and ethtool.. but no success.. leds remain off.

Does anyone have a clue of what the problem might be?
Thanks!

---

### Post by superprash2003 on 2008-06-04
please post your ifconfig output

---

### Post by kevinalle on 2008-06-05
```

eth0  Link encap:Ethernet  HWaddr 00:E0:20:AC:AF:15
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0  txquelen:1000
      RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
      Interrupt:5 Base address:0xe800

```

it is configured with DHCP... but Static IP doesn't work either..
thanks

---

### Post by deltaprime on 2008-06-05
thats interesting let me try to come up with something.

delta

---

### Post by superprash2003 on 2008-06-05
have you tried pinging your router with static ip?

---

### Post by kevinalle on 2008-06-05
yeap.. no luck..

now.. this is kinda weird..
look at the response from ethtool:
```

kevin@server:~$ sudo ethtool eth0
Settings for eth0:
      Supported ports: [ ]
      Supported link modes:   10baseT/Half  10baseT/Full
                              10baseT/Half  10baseT/Full
      Supports auto-negotiation: No
      Advertised link modes: Not reported
      Advertised auto negotiation: No
      Speed: 10Mb/s
      Duplex: Half
      Port: Twisted pair
      PHYAD: 0
      Transceiver: internal
      Auto-negotiation: on
      Supports Wake-on: pum
      Wake-on: d
      Current message level: 0xffffffff (-1)
      Link detected: no

```

why 10Mb/s ??  my LAN connection is 100Mb/s..
I tried changing this but couldn't..

and I don't understand much of the rest...

Thanks

---

### Post by kevinalle on 2008-06-08
ok.. now I have a new problem..
I cleaned the PC and installed a text mode 8.04 ubuntu, because I wanted to try ndiswrapper so I needed a newer kernel.
I downloaded ndiswrapper and copied it to that computer.. but when y typed "make" it said I don't have the kernel source..
I tried downloading the package and copying it and installing the deb, but it didn't work..

So please.. can someone tell me how to install the source?
(that PC does not have internet)
Thanks!

---

