---
title: "netgear wn311b help please"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Richard_2007 on 2007-02-15
I have this card and need help getting it working. The windows xp cd from netgear has cabs and cannot figure out how to extract a driver for ndiswrapper or if the broadcom 43xx driver will work, Or how to make it work for that matter.

sudo lshw -C network

*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@04:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:fdbfc000-fdbfffff irq:10

Lspci -v | grep network

04:06.0 Network controller: Broadcom Corporation Unknown device 4329 (rev 01)
        Subsystem: Netgear Unknown device 7d00
        Flags: bus master, fast devsel, latency 32, IRQ 10
        Memory at fdbfc000 (32-bit, non-prefetchable) [size=16K]

sudo lspci -n

04:06.0 0280: 14e4:4329 (rev 01)

as the above shows the device is there but no driver is installed. I have the netgear driver cd but cannot find an .inf need help extracting the cabs to find the correct driver.

Your input is WELCOMED!

Richard:guitar:

---

### Post by canisyursus on 2007-02-17
here are the drivers for the range max pci netgear wn311b, just use these they will be easier to extract 
[http://kbserver.netgear.com/products/WN311B.asp](http://kbserver.netgear.com/products/WN311B.asp)

---

### Post by Richard_2007 on 2007-02-18
Ok so I downloaded them, and also pulled them off my old win xp machine and used ndiswrapper-1.8 to install the wn311b.inf file, each time I get an invalid inf message and in /etc/ndiswrapper there is an empty file wn311b. I used unshield x data1.cab to access the drivers for winxp. My question is what the heck am I doing wrong??? This is very frustrating.

Thanks for any and all help.

Richard:guitar:

---

### Post by sixteensix on 2007-05-22
Have you had any further luck with this Richard_2007?

---

### Post by Richard_2007 on 2007-05-22
No I didn't have any luck with it and out of frustration went back to a older g card which works out of the box although slower. Someday I hope someone will post how to use the n card. Im amazed there isn't more interest in n technology.

---

### Post by rolnics on 2007-06-06
It's been a few months since your last post Richard have you had any luck?? As I'm a bit gutted about this, cos i recently bought this card before getting hooked on Ubuntu! Only to find it won't work(at present)! But fortunately i learnt this before i shelling out for the new router!! phew!! [-o<

---

### Post by Richard_2007 on 2007-06-07
Nope no luck, I have went back to an older model 802.11g card that works out of the box. Still hoping to get this one to work but I'm not an expert on Linux so waiting for the actions of others to learn how it might be done. Now that there is two of us with the card maybe there will be a bit more interest. It uses a broadcom chipset so I'm not that hopeful BCM4329 I believe.

Thanks
Richard

---

### Post by nealio1000 on 2007-07-26
i have been trying to get my card running for a while. i am now using an old card even tho the wn311b is a lot better. i got my inf file from my windows installation. but after huge amounts of work i couldnt get it to work. although, one time somehow i did get my wn311b to work but my system would crash. i would love to explain how i got it to work but i cant remember. good luck! if u get that adapter to work please pm me!

---

### Post by rolnics on 2007-08-08
Hi Richard,

I've had success!!! I'm currently wireless! I have been trawling the web i found someone on the debian forum having the same issues. With a combination of that forum and  thread as detailed i've got it working! 

I used my windows install like nealio1000 to get mine up and running.

[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206):grin:

i hope this helps to wards you becoming wireless with this setup as well. fingers crossed

---

### Post by jon_williams on 2007-09-21
I have a couple of PC's with Netgear WN311B PCI cards in, and they are currently running Windoze XP. I would like to change the machines over to 64-bit Ububtux, but I have two things preventing me (apart from being a Linux newbie!) and they are; 
1. monitoring the core temp of Core 2 Quad machines, and
2. wireless connection for the above Netgear cards
Does anyone know whether these two desirable features will be pre-integrated into Gutsy Gibbon?

---

### Post by fidge on 2007-11-16
i have had no luck with a WN311B 802.11a/b/g/n wireless card, anyone got any suggestions???

dont want to have to go back to an 802.11g card :(

LF

---

### Post by jon_williams on 2007-11-18
> **jon_williams said:**
> I have a couple of PC's with Netgear WN311B PCI cards in, and they are currently running Windoze XP. I would like to change the machines over to 64-bit Ububtux, but I have two things preventing me (apart from being a Linux newbie!) and they are; 
1. monitoring the core temp of Core 2 Quad machines, and
2. wireless connection for the above Netgear cards
Does anyone know whether these two desirable features will be pre-integrated into Gutsy Gibbon?

Glad to see No. 1 was solved in Gutsy Gibbon \\:D/
But it looks as though there are a number of us who really need some help in getting the Netgear Range Max WN311B PCI cards working .... ](*,)

[IMG]http://serve.dynasig.net/4087.gif[/IMG]

---

### Post by jeconnolly on 2008-07-16
A bit late now, but I picked up a wn311b PCI card today and got it working with NDIS wrapper, loosely following instructions here: 

[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

I just installed the driver with the CD on my windows system, found the .sys and .inf files in Windows folders, and used them to install it.

Works like a charm.  :)

---

