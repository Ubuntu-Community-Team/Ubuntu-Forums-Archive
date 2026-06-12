---
title: "ethernet (wired LAN connection) tutorial"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-10
looking for information on configuring wired ethernet connection in Ubuntu. My computer is running dual boot OS and internet link is fine under XP. 

I do not have Network manager or something set up right. Is there a tutorial on this subject?

Ed

---

### Post by Peter09 on 2009-02-10
Its unusual for a wired LAN connection not to come up in Ubuntu. Can you provide the output of the terminal command

```
lshw -C network
```

---

### Post by ozark_hillbilly on 2009-02-10
I'm not sure I will get through all this. If I could vent for a second:
if Linux is going to succeed in entering more homes worldwide there has to be a definitive "go to" location to help the uninitiated. Is there a website that offers step by step assistance? I need someone to hold my hand right now. 
I typed in the terminal command lshw -C network and got some info. One problem- I saved the data to a text file but Ubuntu does not see my floppy disk drive so I can't save the file to transfer it to the computer I'm typing at now. There is always something blocking my progress. I do not want to type the data in by hand.
Where do I go to get info for troubleshooting ethernet connection.
I have absolutely no idea how to make Ubuntu recognize my floppy disk drive. I DO NOT like knowing so little about all this. I guess a book will be next step.
One part of data results said *-network DISABLED 
That could be a problem, huh.

Ed

---

### Post by ozark_hillbilly on 2009-02-10
Peter,

figured out how to make floppy be recognized....my first success w/ hardware under Linux!!!

lshw results:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:22:15:d8:54:1b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:ca:0b:4d:c5:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Is there an easy fix to this? Hopefully so....

Ed

---

### Post by lavinog on 2009-02-10
Can you give any information about the system? Manufacturer/model number...
Sometimes knowing the brand of the network card can speed up the process.

Also, which version of ubuntu are you using? Include which archetecture (32/64 bits)

---

### Post by lavinog on 2009-02-10
take a look at /etc/network/interfaces
press alt-f2
```
gedit /etc/network/interfaces
```
Does it look like this:
```
auto lo
iface lo inet loopback

```
if not, does it have some lines for eth0?

also try right clicking the network icon by your clock and make sure that "Enable Networking" is checked. If it already was, try unchecking it and checking it again.

---

### Post by ozark_hillbilly on 2009-02-10
System: Asus P5N73-AM mobo  Intel duocore E8500 processor   4 gig RAM
Ubuntu 8.10 Desktop Edition

LAN Realtek RTL8201CP (on mobo) 10/100 Mbps

According to leenooks.com this mobo has a compatibility issue unless the chipset drivers are installed, which they are. Something about the LAN circuitry being a "phyceiver" device.

From leenooks.com:

Phyceiver Devices

A phyceiver device is a dumb network connection device, that does not contain any network control technology. Motherboards fitted with phyceiver devices require a motherboard chipset driver, rather than a network interface driver. In order to locate a driver for a phyceiver, it is necessary to find out the name of the motherboard chipset, rather than look for a network controller driver.

That's all I know,

Ed

---

### Post by lavinog on 2009-02-10
I have read a couple of posts on various linux forums that describe the same issue. I have only seen posts about hardy though and not intrepid. Are you using intrepid?

try this and see if it reports anything:
```
dmesg | grep -i forcedeth

```
it searches the kernel messages for the word forcedeth, which should be the driver for your card.
If you get a version number, can you post it here?

---

### Post by lavinog on 2009-02-10
Also, try shutting down the computer, See if your network card lights are still on, unplug your ethernet cable, wait 15 secs, plug back in, the boot up.
If that works, then the problem has to do with some sort of wake on lan bug.

---

### Post by ozark_hillbilly on 2009-02-10
Yes, the following showed up:

auto lo
iface lo inet loopback

I deleted under Network Connections the "wired" setups and made a new one.
I selected connect automatically and not system setting.
Now I no longer get the enable/disable networking text under the terminal icon. Instead it displays in half intensity the Wired Network and full intensity VPN Connections.

---

### Post by ozark_hillbilly on 2009-02-10
dmesg | grep -i forcedeth  results:


[    4.300594] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.300826] forcedeth 0000:00:0f.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    4.300828] forcedeth 0000:00:0f.0: setting latency timer to 64
[    4.820660] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:15:d8:54:1b
[    4.820662] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq lnktim msi desc-v3

---

### Post by ozark_hillbilly on 2009-02-10
lavinog,

ethernet is ON THE MOTHERBOARD, NO SEPERATE CARD. no LAN light.
hooking/unhooking cable no change.

LAN works under Windows XP.

---

### Post by lavinog on 2009-02-10
Sorry, I was using the term card to refer to device (card or motherboard.) I have never came across an onboard ethernet port without lights though.
I am out of ideas.
I would recomend changing your title to say something like "No ethernet connection - Realtek RTL8201CP"
This way someone with the same card might read your thread.

---

### Post by egalvan on 2009-02-10
> **ozark_hillbilly said:**
> ethernet is ON THE MOTHERBOARD,** NO SEPERATE CARD. no LAN light.**
hooking/unhooking cable no change.

LAN works under Windows XP.

The LAN light is on the connector where the LAN cable is plugged, not on the card.
Try looking for it while running XP.
I've never seen a LAN socket that did not have one (or two) lights,
to indicate connectivity, activity and sometimes speed.

As for "LAN works under Windows XP", that just tells us it's CAPABLE of working... 
now we have to figure out how *nix is going to get it working.
(manufacturers have been known to jump through hoops to get their products working under Microsoft.
At times this has meant mis-configuring hardware or software to work with wonky Windows)

---

### Post by ozark_hillbilly on 2009-02-10
You're right egalvan! Led's above cable on connector.
When I first hooked up cable LED came on and pulsed. Got a swirelling movement at terminal icon for about half a minute then the error message network connection has been disconnected. Light continues to pulsate at LAN connector. But terminal icon displays no network connection.

?????

---

