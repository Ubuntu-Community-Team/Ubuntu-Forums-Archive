---
title: "Persistent wireless problem with Acer Aspire 3680"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by CyberBob on 2007-06-12
I'm posting the information below about my Acer laptop with an Atheros wireless chipset that I've not been able to get working, despite trying a variety of approaches read in other posts.  If anyone else has had success with this wireless device on this rather popular low-priced laptop, please post your step by step method to get it working.

Output of uname -r:

```

bob@CyberBob:~$ uname -r
2.6.20-16-generic

```

Output of lshw:

```

cyberbob                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm syscall nx x86-64 constant_tsc up pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0300000-d037ffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:d0400000-d043ffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0380000-d03fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:d0440000-d0443fff irq:22
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@01:00.0
                logical name: eth0
                version: 14
                serial: 00:1b:24:06:c0:04
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=192.168.1.2 latency=0 multicast=yes
                resources: iomemory:34000000-34003fff ioport:2000-20ff irq:16
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:34100000-3410ffff irq:17
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Mouse
                   vendor: Topro
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:d0644000-d06443ff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@04:09.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
                resources: iomemory:d0204000-d0204fff iomemory:300000000-2ffffffff irq:20
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@04:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: iomemory:d0205000-d0205fff irq:20
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:18b0-18bf irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0-18df irq:10


```


Output of lspci:

```


bob@CyberBob:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


```

The Restricted Drivers manager is installed and the "Atheros Hardware Access layer (HAL) is installed and is enabled  (checked "in use").

My dmesg output was too lengthy to include in this post, but if need be I'll post it later.

Any help is appreciated!  Thanks ...

p.s. forgot to mention that I am running the 64-bit version of Fiesty Ubuntu 7.04

---

### Post by tturrisi on 2007-06-13
Did you turn on wifi using the switch on the front of the laptop?
[http://ubuntuforums.org/showthread.php?t=429182](http://ubuntuforums.org/showthread.php?t=429182)

---

### Post by blakesle on 2007-06-14
I too have the same problem with not being able to get the wireless working. Same computer Acer Aspire 3680 and 32 bit version of Ubuntu Fiesty.

The problem with the switch on the front is that it is impossible to tell wether the switch is on or off since the light does not work. I have tried it both ways but because of the lack of an indicator I can't tell when I am on and when I am off.

I have a wired connection as well and it works great.

---

### Post by CyberBob on 2007-06-17
Same here ... the light for the wireless switch on the front of this laptop has never lit.  I've also tried toggling the switch but it does not respond.

Still only using a wired connection ...

---

### Post by FearlessPax on 2007-06-18
I'm having the same problem, and this is my first time using any build of linux at all, so I'm not even really sure where to begin. Any advice?

---

### Post by tommcd on 2007-06-22
Anybody find an answer to this? I have an Acer 3680-2633 laptop with the same problem. lspci -v shows it is an Atheros unknown device 001c (rev 01). The restricted drivers are in use, yet iwconfig shows no wireless.

---

### Post by tturrisi on 2007-06-22
If the madwifi drivers are loading and yet the device still does not work, then the wifi switch on front of laptop may be set at OFF.  I had no issues using wifi on a new acer 3680 I setup for my kid's friend last week.  here's some additional info that may be useful, though I did not need to do this:
[http://madwifi.org/wiki/UserDocs/MiniPCI](http://madwifi.org/wiki/UserDocs/MiniPCI)

---

### Post by theDaveTheRave on 2007-06-30
Hello All.

Sorry to hear that a number of you are having issues with Feisty and Wireless connections. Mine seemed to work straight off almost - which I am both pleased and surprised about.

Here is a quick praisee of what I did.

I've followed what cyberbob has done to get the same listings.

from lshw the part pertaining to the atheros chip is differet my list is as follows
> 
 *-network
                description: Wireless interface
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 3
                bus info: pci@0a:03.0
                logical name: wifi0       
                version: 01
                serial: 00:19:7d:40:b8:c0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.2.3 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g



the line quoting a logical name doesn't appear in CyberBob's output - I wonder if this is the problem??

there was one other difference comparing the outputs, mine is a celeron M 420 not the 560 chip (I'm sure that chipwise it makes no difference whatsoever, but there may be other diferences in the inner workings that I am unaware of)
--------------------

When I first got Fiesty onto my system it didn't seem as though it was working! On checking the network settings the first option in the list was for a wireless.
Check the properties and see if "Roaming" is enabled, and check that the ESSID is set - as I use it at home I deselected the roaming, and put in the details - then added this as a "location".

I then hard wired into the net and got all of the required updates. I didn't think that it was going to work without some jiggery pokery.... so next morning..... today in fact... in bed turned on and...

tried a few things

> 
davemyers@Aramis:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:17:3F:15:5D:43
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.


which told me that the wirless was hooked in via the ah0 port (as opposed to the wifi0 port - if anyone can explain the reason for this I will be very interested.


Anyway I continued to see if the interface was up

> 
davemyers@Aramis:~$ sudo ifup ath0
Password:
ifup: interface ath0 already configured


so this told me that I should be logged in, started up firefox, and imagine my shock and surprise when I was able to see the forums!

a few notes.

I allways used <ifup> and <ifdown> to bring the internet on / off respectively on my old desktop with a usb wireless key, Reading the forums it is possible to set the button at the front to hook into this somehow, but that is something I will have to sort.

OK how to tell if you are hooked in without the light.... simple add a network monitor to one of the task bars and configure it to show the internet via wireless (in my case ath0), it even has a nice little signal strength bar at the side. Interesting point here, if I run my pc at the same time as my GF runs her works pc (running XP) then the signal strength coming into my box is about double that running into hers - can anyone please explain!

By the way, I am only a relative newbe to the forums and messing about with Linux (previously using Suse 9.0,  I didn't do much command line stuff, just used it for internet via wvdial and college assignments etc - not much of a gamer!)

However some interesting things that I can point out / questions to ask.

When I got my Belkin USB wireless adapter I was able to determine the chipset from running a <lsusb> command. As mentioned earlier my main chip is a 420 not a 560 (like CyberBob's), how can we do a list to get just the details of the Atheros chip out?? I think I am right in that the detail is held inside dmesg, and that you can pipe out just the information that you are looking for, I have looked at the help screens for dmesg but can't decipher them on the code that I should use. I guess that I could take the whole lot into an editor and then search for Atheros, but I know that I can pipe the information out directly, any help on how I do this would be great, it would also be helpfull for the others on this forum as we could then do a comparison of our Atheros chipsets.

good luck all.

I'm contemplating writting a quick howto on my install procedure, so check back on this section for the 3680.

Good luck, Keep doing the funky Penguin.

Dave

---

### Post by tturrisi on 2007-06-30
> **theDaveTheRave said:**
> Hello All.
...which told me that the wirless was hooked in via the ah0 port (as opposed to the wifi0 port - if anyone can explain the reason for this I will be very interested.
Dave
First of all, ath0, wifi0, eth0, ethX, etc., are not ports.  These are names given to the adapter by the kernel.  Atheros chipsets are given names ath0, ath1, ath2, etc.  If you has 2 atheros chipset adapters you would have ath0 & ath1.

Now, atheros devices require the madwifi driver.  This driver works by creating a parent interface (wifi0) and subsequent virtual interfaces (athX).  Thus, you will always have wifi0 and an athX. 

You can have almost an unlimited quantity of athX interfaces, meaning you could have 1 device and be running multiple athX interfaces which do specific connections.  An example would be having a virtual device in monitor mode and a second virtual device in managed mode.

see [http://madwifi.org/wiki/UserDocs#ApplicationManPagesinHTML](http://madwifi.org/wiki/UserDocs#ApplicationManPagesinHTML)

---

### Post by tommcd on 2007-07-01
It seems the Acer 3680 can come with several different Atheros chips. There is another thread about this laptop on these forums. One guy said he bought 2 of them, and each had a different atheros. One worked, and one did not (if I remember correctly).
My atheros shows up as "Unknown device 001c (rev 01" like CyberBob's. Zenwalk identifies it as Atheros AR5006EG, and it don't work with madwifi on zenwalk either, even though the madwifi site says it should:
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)
So I ended up buying a Belkin wireless card with a Ralink chip that works in zenwalk with ndiswrapper. Unfortunately, this same card causes ubuntu to lock up solid on bootup (isn't wireless fun?!). Turns out ubuntu comes with drivers for that card also, but they are buggy and cause the lockup. However, this guy found a solution:
[http://ubuntu.loathsome.us/doc/rt61](http://ubuntu.loathsome.us/doc/rt61)
I'm gonna try that when I get around to it.

---

### Post by theDaveTheRave on 2007-07-01
Hello again Guys and Gals.

This morning I switched on my laptop, and no wireless....??

very strange, the device didn't appear anywhere in the <ifconfig> or <iwlist scan> outputs.. very unhappy I was!

Well that was untill I did the same thing in Vista... and it didn't turn on thier either?? even more strange thinks I.....??:confused:


So then I remember about laptops and power management..... It would seem that occasionally Vista will start up in "power saver mode" if I startup on the battery... when I plug in the cable, or switch the power mode to "performance" the wireles mirraculously starts up again - oh what fun...

So not a large jump from here to a similar thing occuring in Ubuntu...., so reboot....whilst plugged into the mains power...

Yipee... wireless is back!

:guitar:


Looking at what other have done I have included the output of <lspci -v> pertaining to the atheros chip below.


[quote=]
Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
[/quote]

so it would seem that I may be using a different atheros chipset to other.

But I recall that CyberBob had an issue where he sometimes had the connection and sometimes not, maybee power is the part of the problem..... who knows


Tourisi, thanks for the following information

[QUOTE=]

First of all, ath0, wifi0, eth0, ethX, etc., are not ports. These are names given to the adapter by the kernel. Atheros chipsets are given names ath0, ath1, ath2, etc. If you has 2 atheros chipset adapters you would have ath0 & ath1.

Now, atheros devices require the madwifi driver. This driver works by creating a parent interface (wifi0) and subsequent virtual interfaces (athX). Thus, you will always have wifi0 and an athX.

[/QUOTE]

I was wondering about the various ports / adapters etc, very helpfull. It would seem that Feisty is distributed with the madwifi drivers that work for my chip, and this would explain why I had some strange error messages when I first installed Ubuntu onto the laptop, and why the wireless didn't work until after I had received all the updates etc over a hard wired link.

hope everone else is getting their problems sorted out.

Dave

---

### Post by CyberBob on 2007-07-03
Some interesting posts folks!

It looks like I need to clarify a couple of minor points ...

I am the guy who purchased two of these Acer laptops - one was a gift for my son and the second was one purchased for myself to replace an older Compaq laptop that overheated for the last time such that I could no longer boot the machine and use it without it abruptly shutting down.  I purchased both of these Acer laptops from the same store on consecutive days.  Once I saw the quality of the laptop for such a low price I could not resist ...

OK - laptop #1 for my son had the AR5005G chipset

 lspci output contains this line:

Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Initially I did not have this laptop working with the wireless card, and after several re-installations of Feisty it "magically" started working.  I frankly do not know why previous attempts failed nor why it started working on the last attempt - but obviously glad I was able to finally get it to work before giving it to my son as a graduation gift.  I think I had the AC power cord attached each time I used it, but not certain.  So far, almost 3 weeks after giving it to my son he has had no further issues with wireless to my knowledge.


So then, laptop #2 is my machine that I'm currently using with all of the associated info in my original post in this thread.  I have since plugged in a US Robotics PCMCIA wireless card that works fine - but obviously I'd like to get the internal card working.  My system yields the following when given the  command: sudo ifup ath0

```
bob@CyberBob:~$ sudo ifup ath0
Password:
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.

```

Interesting to see that there is a pid file associated with the ath0 device ... does this signify anything or serve as another clue?

Thanks to all for your comments!

---

### Post by tturrisi on 2007-07-03
modprobe ath_pci
ifup ath0

will work IF /etc/network/interfaces has config data for the ath0 device:
iface ath0 inet dhcp
wireless-essid YOUR-ESSID
# wireless-key YOUR-WEP-KEY
auto ath0

if use network-manager then may have to config ath0 after loading the ath driver (modprobe ath_pci will also load the driver dependencies automatically; ath_hal, wlan_wep, wlan_scan_sta, ath_rate_sample, etc. )

---

### Post by Supermort on 2007-07-04
I'm in the same boat as ZellBob here.  x86 Ubuntu 7.04 on an Aspire 3680-2633.  How exactly can I find out which chipset it is when all it spits out is unknown device?  I've been playing with ndiswrapper trying to get something to work but nothing yet.  It seems that the only .inf I can find is the net5211.inf which upon loading claims no such hardware is present.  Any new info/ideas here would be greatly appreciated.

---

### Post by theDaveTheRave on 2007-07-08
Hi again all.


Had a bit of a problem yeterday afternoon with my wireless - it didn't want to work at all.

an ifconfig didn't even show up the wifi0 or ath0 interface, I was very confused.

I tried all the usual stuff... all to no avail, nothing worked.

SOLUTION.

boot into Vista (make a cup of tea, have lunch and run around the local lake while Vista starts up) - check everything is working OK, switch the wireless on and off a couple of times with the button at the front, re-boot back into Fiesty (have dinner and go watch a move while vista shuts down)

..... did I mention how much slower Vista is compared to ubuntu :lolflag:

Well now wirelss is working again....??

probably not much help if you have a dedicated Ubuntu system!

I do remember reading somewhere that it was possible to link the button to the system in some way and hence make it  "work" or turning of / on  the wireless card, but I haven't found the thread again yet!!

hope this helps some of you.

Dave

---

### Post by CyberBob on 2007-08-14
HOORAY!  :)

I FINALLY got my Acer 3680-2633 laptop working with the built-in wireless card, but alas, had to use ndiswrapper.

See this thread:  [http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros]("http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros")

It worked for me, and should work for those of you with the same hardware config that I have.  Have a go at it, and post your results here so that we can compare notes.

Here's what I did in the terminal after running the scripts from the thread referenced above:

```
bob@CyberBob:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bob@CyberBob:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:24:06:C0:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7302 (7.1 KiB)  TX bytes:7302 (7.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7E:1E:66:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:34100000-34110000 

wlan0:ava Link encap:Ethernet  HWaddr 00:19:7E:1E:66:58  
          inet addr:169.254.4.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:34100000-34110000 

bob@CyberBob:~$ ifconfig up
up: error fetching interface information: Device not found
bob@CyberBob:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
bob@CyberBob:~$ sudo ifconfig wlan0 up
Password:
bob@CyberBob:~$ man iwconfig
Reformatting iwconfig(8), please wait...
bob@CyberBob:~$ man iwconfig
Reformatting iwconfig(8), please wait...
bob@CyberBob:~$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
bob@CyberBob:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5512
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:06:c0:04
Sending on   LPF/eth0/00:1b:24:06:c0:04
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6893
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:7e:1e:66:58
Sending on   LPF/wlan0/00:19:7e:1e:66:58
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:06:c0:04
Sending on   LPF/eth0/00:1b:24:06:c0:04
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:7e:1e:66:58
Sending on   LPF/wlan0/00:19:7e:1e:66:58
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.8 -- renewal in 36318 seconds.
                                                                         [ OK ]



```


Good Luck!  

And of course, a BIG THANK YOU **bmartin** for the post that solved this problem and to all who have contributed comments here!!


p.s. Since my previous posts I have had to revert to the "normal" 32-bit Feisty platform because of a necessity to get a particular printer driver compiled.  That problem could not be solved with the AMD-64 distribution, so I opted (once again) to do a fresh install.  I now have everything working for the first time since purchasing the laptop in late May.  Whew!  It was worth the effort - patience does pay off sometimes.

---

### Post by DukeTech on 2007-08-14
I guess I was really lucky. I installed using Wubi last night & the wireless worked without a hitch. I was surprised myself.

---

