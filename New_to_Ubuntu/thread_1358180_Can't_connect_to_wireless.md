---
title: "Can't connect to wireless"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2009-12-18
Hello everybody. 
I know I should have searched first, but, to be honest, I don't have a clue what I'm looking for.

I just installed Ubuntu 9.10 in my aspire 5000, from inside Windows XP. Now, for some reason, I can't connect to my wireless router. 
When I click on the network manager, it says "disconnected" under wireless network, but it doesn't let me connect.
I've been looking around, set up my network and everything, but nothing. Incidentally, the wireless network light in the computer is off.

So I looked in "help", and started the troubleshooting. When I did the sudo lshw -C network thing, this is what I got:

*-network:0
        description: Ethernet interface
        product: SiS900 PCI Fast Ethernet
        vendor: Silicon Integrated Systems (SiS)
        physical id: 4
        bus info: pci@0000:00:04:0
        logical name: eth0
        version: 91
        serial: 00:c0:9f:ee:00:ad
        size: 10 MB/s
        capacity: 100 MB/s
        width: 32 bits
        clock: 33 MHz
        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=SiS900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
        resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:28000000-2801ffff (prefetchable)

*-network:1
        description:Network controller
        product: BCM4318 [AirForce One 54g]802.11g Wireless LAN Controller
        vendor: Broadcom corporation
        physical id: b
        bus info: pci@0000:00:0b:0
        version: 02
        width: 32 bits
        clock: 33 MHz
        capabilities: bus master
        configuration: driver=b43-pci-bridge latency=64
        resources: irq:17 memory: e2000000-e2001ffff

*-network DISABLED
        description: wireless interface
        physical id: 1
        logical name: wlan0
        serial: 00:14:a4:4b:a4:07
        capabilities: ethernet physical wireless
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

And that's it. I don't know if this helps or not. I don't have a clue about Ubuntu. It seems to me that the wireless is disabled, but I don't see any way to enable it.

Can anybody please tell me what to do?

Thanks in advance.:)

---

### Post by Some Penguin on 2009-12-18
BCM4318 -- BroadCom.

Look at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by lidex on 2009-12-18
Is there a hardware kill-switch? Your light should be on for wireless to work.

---

### Post by Some Penguin on 2009-12-18
Aside from hardware switches and driver issues, you could fiddle with iwconfig -- perhaps txpower was set to off.

If so, of course, the obvious question is why -- dmesg might help.  Perhaps a power-saving sleep mode was invoked for some reason, like buggy ACPI.

---

### Post by Greenwidth on 2009-12-18
The Broadcom driver is on the CD, but you need to add it as a software source in:
System > Admin > Software Sources

Then have a look in:
System > Admin > Hardware Drivers

There should be a driver to enable.

---

### Post by Extract_Here on 2009-12-18
******* I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you

---

### Post by Inodoro Pereyra on 2009-12-18
Thanks everybody. I will try now, and report back.:)

---

### Post by Inodoro Pereyra on 2009-12-18
Thanks everybody for taking the time. I'm now finally connected, and loving it!\\:D/

Extract_Here: you hit it right in the head.

Thanks again.

---

### Post by Extract_Here on 2009-12-18
sure thing

glad to help

-may the source be with you.

---

### Post by lidex on 2009-12-18
> **Extract_Here said:**
> ******* I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you

*[COLOR="Blue"]Nice post and thanks for that info - it will come in handy.[/COLOR]*

---

### Post by Rrory on 2009-12-18
My dad just got the Asus U81A-RBBDRD05 erased Windows 7 and installed 9.04  but the wireless won't connect.

He's not a tecchie, neither am I so is the above the answer to our problem too?
 thanks, he's a noob to Ubuntu as well.

---

### Post by Extract_Here on 2009-12-18
yes that is most likely the problem follow the directions and i should work.

---

### Post by Rrory on 2009-12-19
Will this help me to connect to LAN as well? I forgot to say I can't do that either.
 thanks
Rory

---

