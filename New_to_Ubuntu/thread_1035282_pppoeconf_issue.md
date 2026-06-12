---
title: "pppoeconf issue"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by kevpants on 2009-01-09
Hi internet brain people!

Brand new user of Ubuntu (Hardy) and am having the common issue of getting my wired ethernet ADSL connection to work. This is not a new modem (Thomson Speetouch) or connection and works in windows, in fact I'm using it now from a work Dell laptop.

Here's the story, Windows on my personal laptop decided to contract a mental illness so I decided to get Ubuntu running from a disk I had from a while back when I toyed with the idea of switching from Windows.

Install went fine but I can't connect to the internet and I've a feeling it's something simple. I can see my modem no problem [http://192.168.1.1/](http://192.168.1.1/) gets me in there no problem and I can ping it from the terminal. I've a pppoe connection using DHCP.

When I use the pppoeconf command to try and get it working it does it's scans finds eth0 no problem and after I hit "yes" it returns:
> Sorry, I scanned 1 Interface but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process whihc controls the modem.

I'm in Ireland where ISP's require a username and password which I have and have tried entering this in the network settings in the "point to point connection" (little pic of a phone next to it) where I've ticked "enable this connection" and selected PPPoE. I've also tried to configure the "Wired Connection" (pic of a cable and socket) where I've set it to DHCP. I've tried all kinds of combinations. 

Funnily enough I can't put a tick next to the "point to pont connection" it flashes a few times and my tick dissapears???

Hope someone can assist. Cheers.

---

### Post by Claus7 on 2009-01-09
Hello and welcome,

does this link helps you? It seems very comprehensive to me:
[http://ubuntuforums.org/archive/index.php/t-478644.html](http://ubuntuforums.org/archive/index.php/t-478644.html)

Regards!

---

### Post by kevpants on 2009-01-10
Thanks for that link. Unfortunately it didn't help. There's nothing wrong with the ADSL modem, as I said I'm using it right now and ahve used it on the other machine when it was Windows. Plus I can connect to the modem on the Linux laptop no problem. It's simply accessing the internet that has me stumped!

Anyone got any other suggestions???

---

### Post by kevpants on 2009-01-10
hhhmmmmmm. I'm starting to think this is an issue with my ethernet card in the laptop not being configured or Ubuntu not having the driver for it. From trawling the web it seems to be the solution to people having the same issues as myself.

Can someone advise on how I would do this using the terminal?

---

### Post by arjuntank on 2009-01-10
which ethernet do u have?
is it listed in pci devices ?
what does ur ifconfig says?

---

### Post by kevpants on 2009-01-10
Thanks for the response.

I'm not sure what Ethernet I have. Don't really understand the question, sorry :( 

Yes the ethernet controller seems to be listed in the PCI devices. the output of lspci -v seems to list two. Maybe the output would harbor some clues?

> 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Subsystem: Acer Incorporated [ALI] Unknown Device 011c
Flags: bus master, fast devsel, latency 0, IRQ 219
Memory at f6000000 (64-bit, non-pretchable)[size=64k]
Expansion ROM at <ignored> [disabled]
Capabilities: <access denied>

Apologies if there are any typos I'm on a different laptop with no way of getting these terminal outputs on here without individually typing them #-o

Here is the output of ifconfig

> eth0 Link encap:Ethernet HWaddr 00:1d:72:0c:81;e9
inet addr:192.168.1.65 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21d:72ff:fe0c:81e9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:22 errors:0 dropped:0 overruns:0 frame:0
TX Packets:96 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX Bytes:2644 (2.5KB) TX Bytes:13270 (12.9KB)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:1510 errors:0 dropped:0 overruns:0 frame:0
TX Packets:1510 errors:0 dropped:0 overruns:0 carrier:0
collsions:0 txqueuelen:0
RX Bytes:7550 (73.7KB) TX Bytes:75500 (73.7KB)

Ta Da!........[SIZE="1"]help[/SIZE]

---

### Post by kevpants on 2009-01-10
Correction. I don't ahve 2. The 2nd one is a wireless adaptor. My modem isn't wireless enabled though. Feck.

---

### Post by arjuntank on 2009-01-10
naah...the second one is localhost, lo is localhost...(look 127.0.0.1)
wireless is like wlan0 or something
may be this can help:
```

poff -a

```
if another pppo is running..
also try for pppconfig again
and that doesnt work then try installing wicd..
wicd is more user friendly

---

### Post by kevpants on 2009-01-11
Thanks for your help. I tried pppconfig but this seems to be for a dialup connection?

Anyone got any idea why this wired connection isn't working from the above info?

---

### Post by arjuntank on 2009-01-14
ur adsl connection is a dial-up connection..( u have the username and the password right?)

from the error message that appeared..
all i can suggest u is doing a poff -a 
or check ur physical connections

u might wanna check [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=78337") out

---

