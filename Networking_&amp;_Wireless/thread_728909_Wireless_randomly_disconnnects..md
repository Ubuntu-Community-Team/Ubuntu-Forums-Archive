---
title: "Wireless randomly disconnnects."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by pankirk on 2008-03-19
When I am downloading something or viewing multiple pages at once, it seems like my internet connection stops working, adn the only solution is to reset my computer and when I do that it works fine. sometimes I am not even downloading anyhng and it stops though. So I wonder what the problem is. Do I have incorrect drivers for my device? I dont know. Any help is appreciated.

this is my hardwatre (pci wmp54g wireless card made by linksys):
[html]  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:a7:fd:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.104 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g[/html]

---

### Post by pankirk on 2008-03-19
any help

---

### Post by Netsurfer on 2008-03-20
I have the same problem (same pci card by Linksys).

As workaround you can try:

[COLOR="Red"]$ sudo /etc/init.d/networking restart[/COLOR]

Any other solution?:(

---

### Post by pankirk on 2008-03-20
Nobody has answered it yet =/. I guess "$ sudo /etc/init.d/networking restart" is a good soultion so far, atleast i dont have to reset my whole computer anymore

---

### Post by clueless on 2008-03-20
I have the same problem with an ASUS USB wifi adaptor that uses the rt73 module. I have found that - at least for now - the solution could be using ndiswrapper.
Step by step instructions on how to install here:
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by Netsurfer on 2008-03-22
Thank you for suggestion.
I used "ndiswrapper" and I solved the problem. Now the wireless connection is stable with a good signal.

Bye (and Good Easter)

---

