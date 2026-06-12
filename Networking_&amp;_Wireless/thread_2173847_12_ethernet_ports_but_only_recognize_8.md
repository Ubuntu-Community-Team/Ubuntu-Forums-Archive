---
title: "12 ethernet ports but only recognize 8"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by antonio7 on 2013-09-11
Hi,

I have 3 equal quad port nics cards with chipset VT6122 and only 8 ports are recognized, the other 4 ports remaing in *Unclaimed* state. How is possible that Ubuntu does not recognize all the ports if they are the same? I already changed the PCI slot, but it is not a hardware problem.
I'm running ubuntu 12.04LTS. NICs are Mikrotik 44GV

Here is some information:
**sudo lshw**
```
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:8000(size=24576) memory:ddc00000-ddefffff
        *-pci:0
             description: PCI bridge
             product: HB6 Universal PCI-PCI bridge (non-transparent mode)
             vendor: Hint Corp
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm hotswap normal_decode bus_master cap_list
             resources: ioport:8000(size=8192) memory:ddc00000-ddcfffff
           *-network:0
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 11
                serial: 00:0c:42:1a:2f:cc
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:19 ioport:9800(size=256) memory:ddcffc00-ddcffcff
           *-network:1
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: eth1
                version: 11
                serial: 00:0c:42:1a:2f:cd
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:18 ioport:9400(size=256) memory:ddcff800-ddcff8ff
           *-network:2
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth3
                version: 11
                serial: 00:0c:42:1a:2f:ce
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 ioport:9000(size=256) memory:ddcff400-ddcff4ff
           *-network:3
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:02:0b.0
                logical name: eth4
                version: 11
                serial: 00:0c:42:1a:2f:cf
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:16 ioport:8800(size=256) memory:ddcff000-ddcff0ff
        *-pci:1
             description: PCI bridge
             product: HB6 Universal PCI-PCI bridge (non-transparent mode)
             vendor: Hint Corp
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm hotswap normal_decode bus_master cap_list
             resources: ioport:a000(size=8192) memory:ddd00000-dddfffff
           *-network:0
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth5
                version: 11
                serial: 00:0c:42:1a:2f:c0
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:18 ioport:b800(size=256) memory:dddffc00-dddffcff
           *-network:1
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:03:09.0
                logical name: eth6
                version: 11
                serial: 00:0c:42:1a:2f:c1
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 ioport:b400(size=256) memory:dddff800-dddff8ff
           *-network:2
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:03:0a.0
                logical name: eth7
                version: 11
                serial: 00:0c:42:1a:2f:c2
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:16 ioport:b000(size=256) memory:dddff400-dddff4ff
           *-network:3
                description: Ethernet interface
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:03:0b.0
                logical name: eth8
                version: 11
                serial: 00:0c:42:1a:2f:c3
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:19 ioport:a800(size=256) memory:dddff000-dddff0ff
        *-pci:2
             description: PCI bridge
             product: HB6 Universal PCI-PCI bridge (non-transparent mode)
             vendor: Hint Corp
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm hotswap normal_decode bus_master cap_list
             resources: ioport:c000(size=8192) memory:dde00000-ddefffff
           *-network:0 **UNCLAIMED**
                description: Ethernet controller
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:04:08.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=8 mingnt=3
                resources: ioport:d800(size=256) memory:ddeffc00-ddeffcff
           *-network:1 **UNCLAIMED**
                description: Ethernet controller
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:04:09.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=8 mingnt=3
                resources: ioport:d400(size=256) memory:ddeff800-ddeff8ff
           *-network:2 **UNCLAIMED**
                description: Ethernet controller
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:04:0a.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=8 mingnt=3
                resources: ioport:d000(size=256) memory:ddeff400-ddeff4ff
           *-network:3 **UNCLAIMED**
                description: Ethernet controller
                product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:04:0b.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=8 mingnt=3
                resources: ioport:c800(size=256) memory:ddeff000-ddeff0ff



```
**lspci -nn | grep 0200**

```
02:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
02:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
02:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
02:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
03:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
03:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
03:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
03:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
04:08.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
04:09.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
04:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
04:0b.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter [1106:3119] (rev 11)
```

---

### Post by varunendra on 2013-09-12
Welcome to the forums antonio !

I was hoping someone else with a better understanding than me would pick it up, but no one did, so let's try my wits.

After loading, when the system starts showing above state, what if you manually unload and reload the driver -
```
sudo modprobe -rfv via-velocity
sudo modprobe -v via-velocity
```

Does it get loaded for the third card as well?

**PS:**
I see your post has been edited by lisati to wrap the code within 'Code' tags. Next time while posting commands/outputs, please do what he mentioned in the comment or follow the "Using Code Tags" link in my signature to see how to do it yourself.

---

### Post by antonio7 on 2013-09-14
Hi varuendra,

I tried the commands that you suggested but it didn't work. Nothing changed.
This is a odd behaviour since it's not a drivers issue. It it was a drivers problem it wouldn't recognize any card.
Another idea?

---

### Post by varunendra on 2013-09-14
> **antonio7 said:**
> This is a odd behaviour since it's not a drivers issue. It it was a drivers problem it wouldn't recognize any card.

As far as just driver-device relation is concerned, it is definitely not an issue. But I've seen this kind of setup for the first time, so can't say if there maybe some 'hidden' issues, like some sort of limit or conflict.

Have you checked the dmesg and syslog?
```
dmesg | grep -i via
```

Maybe take a look yourself at full logs (/var/log/syslog and /var/log/dmesg) to see if there are any hints about why this is happening.

I also suspect possibly a communication problem at the motherboard itself. Can you try some other kind of PCI card in one of the slots (testing each one of the three) to see if it is recognized and usable when other two are occupied with these ethernet cards?

---

### Post by antonio7 on 2013-09-14
Hi,

This is the output from the syslog. Notice the last 4 lines, seems like Ubuntu is skipping the ports for some reason.
I also added another quad port nic from a different vendor based on Intel chipset and it's been recognized correctly, however the third VIA card still not working. I have change the PCI slot to discard IRQ issues. 

```

Sep 10 20:31:24 CCIELAB kernel: [    1.336213] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
Sep 10 20:31:24 CCIELAB kernel: [    1.336214] Copyright (c) 2004 Red Hat Inc.
Sep 10 20:31:24 CCIELAB kernel: [    1.336344] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
Sep 10 20:31:24 CCIELAB kernel: [    1.336964] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.336965] eth0: Ethernet Address: 00:0c:42:1a:2f:cc
Sep 10 20:31:24 CCIELAB kernel: [    1.351389] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
Sep 10 20:31:24 CCIELAB kernel: [    1.351824] eth1: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.351825] eth1: Ethernet Address: 00:0c:42:1a:2f:cd
Sep 10 20:31:24 CCIELAB kernel: [    1.367318] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 17
Sep 10 20:31:24 CCIELAB kernel: [    1.367736] eth2: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.367737] eth2: Ethernet Address: 00:0c:42:1a:2f:ce
Sep 10 20:31:24 CCIELAB kernel: [    1.383277] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
Sep 10 20:31:24 CCIELAB kernel: [    1.383692] eth3: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.383693] eth3: Ethernet Address: 00:0c:42:1a:2f:cf
Sep 10 20:31:24 CCIELAB kernel: [    1.392107] forcedeth 0000:00:07.0: ifname eth4, PHY OUI 0x732 @ 1, addr 20:cf:30:92:de:59
Sep 10 20:31:24 CCIELAB kernel: [    1.392110] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
Sep 10 20:31:24 CCIELAB kernel: [    1.399561] eth5: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.399563] eth5: Ethernet Address: 00:0c:42:1a:2f:c0
Sep 10 20:31:24 CCIELAB kernel: [    1.415507] eth6: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.415509] eth6: Ethernet Address: 00:0c:42:1a:2f:c1
Sep 10 20:31:24 CCIELAB kernel: [    1.431454] eth7: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.431456] eth7: Ethernet Address: 00:0c:42:1a:2f:c2
Sep 10 20:31:24 CCIELAB kernel: [    1.447420] eth8: VIA Networking Velocity Family Gigabit Ethernet Adapter
Sep 10 20:31:24 CCIELAB kernel: [    1.447422] eth8: Ethernet Address: 00:0c:42:1a:2f:c3
Sep 10 20:31:24 CCIELAB kernel: [    1.462955] via-velocity 0000:04:08.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.462974] via-velocity 0000:04:09.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.462989] via-velocity 0000:04:0a.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.463004] via-velocity 0000:04:0b.0: already found 8 NICs.

```

Thanks

---

### Post by varunendra on 2013-09-14
> **antonio7 said:**
> 
```

Sep 10 20:31:24 CCIELAB kernel: [    1.462955] via-velocity 0000:04:08.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.462974] via-velocity 0000:04:09.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.462989] via-velocity 0000:04:0a.0: already found 8 NICs.
Sep 10 20:31:24 CCIELAB kernel: [    1.463004] via-velocity 0000:04:0b.0: already found 8 NICs.

```

This definitely sounds like some kind of limitation to me, either on driver's side or the OS. Since the messages are coming from the driver, I suspect it is a limitation on the via-velocity driver ("I'm already full, can't eat more.."). Can you try a different kind of PCI card? Not ethernet.

---

### Post by antonio7 on 2013-09-15
I already plugged another ethernet card using an Intel chipset and it's being recognized correctly. I'm afraid I will use this Intel card and take off one of the VIA unless any other community memeber provide new ideas.

Thanks varunendra.

---

### Post by varunendra on 2013-09-15
You mean the current setup is 8-VIA, 4-Intel ports - all recognized? If so, then congratulations for having at least your 12-ports working somehow. :)

I missed the fact (didn't look closely) that all 8 recognized ones in the output you posted were VIA, no Intel one. Interesting issue though, worth digging deeper.... I wish I had enough time to chase this one..

---

### Post by antonio7 on 2013-09-15
Exactly, now the setup is 8 VIA ports + 4 Intel ports. I will test it deeply and I expect it work fine for my CCIE Lab.

Thanks for your help Varun.

---

### Post by sisco311 on 2013-09-15
> **varunendra said:**
> I suspect it is a limitation on the via-velocity driver ("I'm already full, can't eat more..").

Yep. And the funny thing is that even the author(s) of the driver think that this limitation is nonsense. :)
 
via-velocity.h:

```

...
#define MAX_UNITS           8
...

```

via-velocity.c: 
 
```

...

        /* FIXME: this driver, like almost all other ethernet drivers,
         * can support more than MAX_UNITS.
         */
        if (velocity_nics >= MAX_UNITS) {
                dev_notice(dev, "already found %d NICs.\n", velocity_nics);
                return -ENODEV;
        }

...
 
```

 @OP: I would file a bug report @ launchpad.net asking for this limit to be raised in the upstream kernel sources. The fix is trivial. In the meantime you could try change the value in via-velocity.h and recompile the kernel module. If you need some pointers on how to do it feel free to ask.

---

### Post by varunendra on 2013-09-15
Wow ! Great discovery sisco311, and funny indeed. I guess I'm not going to forget this one ever :P

Antonio,

I'd encourage you to file the bug at launchpad. Both this driver and this kind of limitations are rare to see in Linux, so I guess this one is immediately going to catch some attention.

---

### Post by antonio7 on 2013-09-24
Hi sisco311,

Thanks for your input. Looks like that is the problem. How can I locate the via-velocity.h? I'm new in Ubuntu and my knowledge is very basic. I tried with "locate via-velocity.h" but it does not find anything.
Can you provide a how to guide to compile the kernel once the via-velocity file has been changed?

Regards.

---

### Post by varunendra on 2013-09-25
> **antonio7 said:**
> How can I locate the via-velocity.h?
You can't locate it in your system. The driver is part of the kernel and comes as a pre-compiled binary. You don't get the source code by default.

If you want to compile the driver yourself with the desired changes, you'll have to find and download its source code.

You can find the source code files for individual drivers like [here]("http://lxr.linux.no/linux+v3.11.1/drivers/net/ethernet/via/"), or download the whole kernel as source code from [here]("https://www.kernel.org/") and extract individual driver source code from it.

I have never done it myself so can't say if there are any catches in trying to manually compile individual drivers, but it looks like it shouldn't be much different than normal "config > make" procedure. If you decide to try that, please let us know. If any problems occurred, we might be able to help, if all went smooth, you'll be helping many. :)

---

### Post by tgalati4 on 2013-09-25
You are looking at 2 to 3 hours to set up a build environment, apply the patch, then compile the kernel and the modules.  It would be nice if you could just compile the module and substitute and you could if someone else has already built it with the correct patch, then you could download it and manually replace the old module.

---

### Post by sisco311 on 2013-09-29
Sorry for the delay.

It is possible to build the kernel module without building the whole kernel. Here is how to do it .

Install the linux headers and dpkg-dev packages:
```
sudo apt-get install linux-headers-$(uname -r) dpkg-dev
```

Create a directory for  the kernel source and download it with apt-get:
```
mkdir ~/linux
cd ~/linux
apt-get source linux-image-$(uname -r)
```

cd into the source directory:
```
cd linux**-version**
```
where **version **is the version number of the kernel (e.g. `cd linux-3.11.0').

Now you can edit the via-velocity.h header file. It's in the ./drivers/net/ethernet/via/ directory.

At this point please read the comments at the top of the via-velocity.h and via-velocity.c files. In theory, and according to the comment made by the author in the .c file, the driver should support more than 8 ports, but even the original driver is distributed without any warranty. 

The next step is to prepare the source code for compiling the module:
```
make defconfig && make prepare
```

You can build the module with:
```
make -C /usr/src/linux-headers-$(uname -r) M=~/linux/linux-**version**/drivers/net/ethernet/via/
```

Now you can try to unload the old driver and load the new one:
```

sudo modprobe -rfv via-velocity
sudo insmod ~/linux/linux**-version**/drivers/net/ethernet/via/via-velocity.ko
```

---

