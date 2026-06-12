---
title: "Aspire Atheros wireless help"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Ice_C on 2007-06-16
Hey, 
I recently bought a acer aspire 5100 series (model:BL51) and installed Feisty on it. The problem is that it doesnt show my wireless card at all; even in the device manager.

ifconfig:
```
eth0      Link encap:Ethernet  

             lo        Link encap:Local Loopback  
         

```


lpsci -v:
```
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 19
        Memory at 8c000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

I tried ndiswrapper with the drivers here:[ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip)
But my laptop would freeze everytime I tried connecting to my WPA network.

Any help?

---

### Post by Pinteiro on 2007-07-04
Hi, 
I had the same problem with my aspire 5100 (model 5033) and got it to work ok by appending "pci=assign-busses" on the kernel configuration in /boot/grub/menu.lst

I'v made a step by step guide here in ubuntu forums (just searh for "aspire" and it should come on top).
hope that helps.
> **Ice_C said:**
> Hey, 
I recently bought a acer aspire 5100 series (model:BL51) and installed Feisty on it. The problem is that it doesnt show my wireless card at all; even in the device manager.

ifconfig:
```
eth0      Link encap:Ethernet  

             lo        Link encap:Local Loopback  
         

```


lpsci -v:
```
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 19
        Memory at 8c000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

I tried ndiswrapper with the drivers here:[ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip)
But my laptop would freeze everytime I tried connecting to my WPA network.

Any help?

---

### Post by jdunn on 2007-07-18
Your guide didn't work for me Pintiero.  See my comments.

---

### Post by kevdog on 2007-07-18
Can you list the following:
lshw -C network

Sounds right now at least like a driver problem since the device is not being recognized.

---

### Post by GeeZor on 2007-07-18
Have you tried madwifi already?

Madwifi is the atheros thing to try before the ndiswrapper...  worked out for me on a laptop running fedora. Never tried with Ubuntu though. 

good luck  :)

---

### Post by jdunn on 2007-07-18
Geezor,
I know about Madwifi but haven't tried it.  The reason being, I found a short and seemingly thorough guide on this forum from Pintiero who is using Feisty on the exact same laptop I am.  Pintiero said he tried Madwifi without success.  I'm willing to try Madwifi after I've exhausted ndiswrapper as an option.

kevdog,

sudo lshw -C network
Password:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:54000000-5400ffff irq:10
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@04:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ce:d7:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.150 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:20

---

### Post by kevdog on 2007-07-18
Id second the opinion to try madwifi, however I thought beginning with feisty that the madwifi drivers were built-in if at the time of installation you chose to install proprietary software (with wireless drivers being one of the options).  You can try looking into Synaptic for this, are go to the madwifi website and download their version, although I think the two are the same.

BTW --- your network controller is unclaimed because there is no associated driver

---

### Post by Twintop on 2007-07-19
I believe Aspire 5100s are supported by [acer_acpi]("http://code.google.com/p/aceracpi/") . acer_acpi + madwifi seems to work the best (from my personal experiences and from what I've heard from others). I wonder what-all it would take to get acer_acpi included in the standard repos, since this issue seems to be a very common one -- I didn't know so many Acer owners wanted to run Ubuntu!

---

### Post by bscook on 2007-07-20
> BTW --- your network controller is unclaimed because there is no associated driver

I'm having a similar problem... how does one associate the driver?

---

### Post by jdunn on 2007-07-20
TwinTop,
I just downloaded and tried the Aceracpi. Again, I get no errors in Makefile but no driver associated with the Atheros Controller. However, there is now a /proc/acpi/acer directory and the 'wireless' attribute is set to one.

---

### Post by marsmissionaries on 2007-07-20
Try madwifi, ndiswrapper will not always work.

[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/) <---make sure you download the latest snapshot from here and compile it.


This might be the only way you get it to work.

---

### Post by Twintop on 2007-07-21
> **marsmissionaries said:**
> Try madwifi, ndiswrapper will not always work.

[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/) <---make sure you download the latest snapshot from here and compile it.


This might be the only way you get it to work.


I believe madwifi is included standard with Ubuntu installs as part of HAL, more specifically Atheros HAL in Restricted Drivers. Is that enabled?

---

### Post by jdunn on 2007-07-21
restricted drivers are enabled
but my Atheros device has no driver.

---

