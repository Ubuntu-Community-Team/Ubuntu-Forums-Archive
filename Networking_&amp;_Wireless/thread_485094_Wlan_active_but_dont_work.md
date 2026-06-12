---
title: "Wlan active but dont work"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Jobbe123 on 2007-06-26
Hello..

I just installed Ubuntu and it work..
But my wlan card is noticed but ain't working it is a pcmcia card with ralink clipset
type: DN-7041
chipset: RT2600

i used this command: lspci -v | less 

and read the info and found this:
02:00.0 Network controller: RaLink Ralink RT2600 802.11 MIMO
        Subsystem: RaLink Unknown device 2661
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 34000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

the little lamp "link" on my card is on and the activity lamp flashing sometimes

can i use the pcmcia card out of box?

---

### Post by t4thfavor on 2007-06-26
Make sure you only have one of the drivers loaded, you will need either the rt61 driver( old) or the rt2x00 drivers (AKA serialmonkey).

check here
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2115](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2115)

---

### Post by Jobbe123 on 2007-06-26
well the driver work but i cant connect to my wireless network..
my network have no password..

---

### Post by t4thfavor on 2007-06-26
how do you know the driver is working if you cannot connect to the network? Seeing is not always working.

It still could be the issue. I would suggest running lsmod |grep rt to see if you have both drivers loading at the same time. I have seen other posts where this was the issue.

---

### Post by Jobbe123 on 2007-06-26
i ran the command and got this:

morten@morten-laptop:~$ lsmod |grep rt
exportfs                6912  1 nfsd
rt61                  245128  1 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
agpgart                35400  2 drm,ati_agp
morten@morten-laptop:~$

**UPDATE**
I think my wireless card work now..
But i dont know why..

---

