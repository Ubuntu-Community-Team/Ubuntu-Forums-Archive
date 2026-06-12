---
title: "Realtek 8149 Ethernet Card Not Found"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by caolan on 2006-11-11
Hi, I've recently picked up an old desktop and I want to use it as a file server just so I can learn a bit about networking. I recently bought an Ethernet card for it and installed xubuntu dapper. 

I plugged my network card into my wireless router but the card was not picked up during the installation, which I found surprising. When it loaded up I typed 'lspci' to see if it saw anything at all, and it listed my Ethernet card as a Realtek 8149 chipset. However it is not listed in network manager and when I type 'ifconfig' all I can see is the 'lo' device.

Can someone please explain how I can install this card (in easy to follow steps where possible) as I'm really new to this whole linux thing and I hate having a new toy sitting downstairs that I can't connect to! :-D

---

### Post by DaveBorealis on 2006-11-11
Hello caolan,

I realize that ifconfig didn't return anything for the card, but just for the heck of it what happens when you try:
```
sudo /sbin/ifconfig eth0 <your IP address> up
sudo /sbin/route add default gw <your gateway IP address>

```

Also something else to try, on older computers I've had luck switching a stuborn card from one PCI slot to another.  Don't know why it sometimes works, but perhaps it's a dodgy slot, or an IRQ conflict of some sort.

Dave

---

### Post by caolan on 2006-11-12
"sudo /sbin/ifconfig eth0 <your IP address> up" 

gives: 
SI0CSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device


"sudo /sbin/route add default gw <your gateway IP address>"

gives:
SI0CADDRT: Network is unreachable


I've tried switching PCI slots and still no luck :(

---

