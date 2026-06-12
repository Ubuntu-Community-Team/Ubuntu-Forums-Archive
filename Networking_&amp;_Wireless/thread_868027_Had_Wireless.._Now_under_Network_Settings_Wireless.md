---
title: "Had Wireless.. Now under Network Settings Wireless Connection is Gone.... HELP???"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Kindrel on 2008-07-23
A few days ago I HAD wireless internet.  I actually figured it out.  Then I updated Ubuntu, used the internet a bit, and, shut it down.

When I came back a couple days later, my wireless is gone.  In fact, under Network Settings under the Connections tab the Wireless Connection is GONE!  Plus if I left click on the dual computers in the upper left hand corner of the desktop Enable Networking is checked, there's a Edit Wireless Networks, but there's no Enable Wireless Networking or anything.  

My Wireless LED is on.  It works in Vista.  So what's going on?  And how the heck do I get these things back??????  

Someone please guide me!!!!!!!!!

---

### Post by PinkFloyd102489 on 2008-07-23
How did you install the wireless drivers? Im betting you installed with ndiswrapper and had a kernel update.

Do this in a terminal and see what happens:

```
sudo modprobe ndiswrapper
```

---

### Post by Kindrel on 2008-07-23
Nothing happened.  Nothing changed.  I still can't see any wireless connections.  (BTW.  My laptop is beside me disconnected, I'm using a desktop)

I didn't install my wireless with ndiswrapper.

Thanks, but any other suggestions?

---

### Post by Alldan on 2008-07-23
hi, 
look here:
[http://ubuntuforums.org/showthread.php?t=773016](http://ubuntuforums.org/showthread.php?t=773016)
i wish you luck!

---

### Post by Kindrel on 2008-07-23
Thanks, but I doubt it's that.  I did have an open Wireless because of the whole WPA issue with routers and passwords in Ubuntu.  

Though it was after the recent updates, that my whole wireless connection network boxes just disappeared!  Poof!  And my Wireless was Enabled but not working.  I can hardwire connect, but not wireless.

But regardless I will check it out when I have my wireless up and running in the future.  Thanks!

---

### Post by Kindrel on 2008-07-23
Some more help and advice needed please!?!?!?!

---

### Post by matthewbpt on 2008-07-23
> **PinkFloyd102489 said:**
> How did you install the wireless drivers? Im betting you installed with ndiswrapper and had a kernel update.

Do this in a terminal and see what happens:

```
sudo modprobe ndiswrapper
```

I have this problem too, and I use ndiswrapper and recently had a kernel update! How do I fix then?

---

### Post by zipperback on 2008-07-23
Please tell us what version of Ubuntu you are running.

Please provide the output of the following command.

```

lspci

```

And please provide the output of this one too.

```

ndiswrapper -l

```


- zipperback
:popcorn:

---

### Post by Kindrel on 2008-07-23
I'm using the Hardy Heron version.  

The lspci is:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


and the ndiswrapper -l didn't show anything

---

### Post by Kindrel on 2008-07-23
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:82:13:c9  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe82:13c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14788901 (14.1 MB)  TX bytes:1835846 (1.7 MB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6800 (6.6 KB)  TX bytes:6800 (6.6 KB)


What else do you need??

---

### Post by Kindrel on 2008-07-23
and my sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:82:13:c9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

---

### Post by Kindrel on 2008-07-24
I've provided a lot of information here.  Unfortunately I'm not a Ubuntu programming expert or ANY expert at all.  

I really THANK EVERYONE for helping me.  BUT if I could get more advice I'd be even more appreciative because I desperately need my wireless for business!

Anyone???  Please???

---

### Post by PatrickFisher on 2008-07-24
> **Kindrel said:**
> I've provided a lot of information here.  Unfortunately I'm not a Ubuntu programming expert or ANY expert at all.  

I really THANK EVERYONE for helping me.  BUT if I could get more advice I'd be even more appreciative because I desperately need my wireless for business!

Anyone???  Please???

Hey there! Got your fb message... first of all, it looks like this is a kernel issue, there's already a bug report for it.

[https://bugs.launchpad.net/ubuntu/+bug/228548](https://bugs.launchpad.net/ubuntu/+bug/228548)

Now, since you really need this for your business, and it doesn'tl ook like there's a quick-fix, why don't you boot into an older kernel? If you're already dual-booting, it should be easy as pie, just select an older kernel in the GRUB menu.

If GRUB normally doesn't show up, apparently you need to push "Esc" as the computer boots. Try that.

---

### Post by Kindrel on 2008-07-24
My GRUB menu does show up (thankfully) for when and if I want to boot into Windows Vista.

There's only one problem, I can't select an older kernel to boot into for Ubuntu.  There's the regular one I log into, then the recovery one below (which doesn't quite work and is the same kernel) then another one, which which name extension I fail to remember right now.  

This is frustrating me beyond belief.  

I left Windows for a reason and mainly for constantly crashing, and, being non-supportive and unstable.  And I'm getting it here.

If it's not a quick-fix... how long do you figure a problem like this would take to solve?

---

### Post by Kindrel on 2008-07-24
Hey guys... 
Before I try the below... what do you make of it????

This seems to be a result if there are different versions of ath_pci modules installed on your computer (probably those from before the updates). Try running

find /lib/modules/ -iname "*ath*"

then post this information here. Thank you!
 Kindrel said 1 hour ago:

/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/net/ath_pci.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_sample.ko
 Dieter Smorra said 22 minutes ago:

Ok, here's the problem:

/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko

try to remove one of these (but make a backup first), e.g.
sudo mv /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko ~

then try again:

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Hope this works :-/

---

### Post by PatrickFisher on 2008-07-24
> **Kindrel said:**
> Hey guys... 
Before I try the below... what do you make of it????

This seems to be a result if there are different versions of ath_pci modules installed on your computer (probably those from before the updates). Try running

find /lib/modules/ -iname "*ath*"

then post this information here. Thank you!
 Kindrel said 1 hour ago:

/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/net/ath_pci.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_sample.ko
 Dieter Smorra said 22 minutes ago:

Ok, here's the problem:

/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko

try to remove one of these (but make a backup first), e.g.
sudo mv /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko ~

then try again:

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Hope this works :-/

Yeah ,that looks like it could work.

---

### Post by Kindrel on 2008-07-24
Granted I don't know how to make a backup on Ubuntu... so wish me luck!

---

### Post by PatrickFisher on 2008-07-24
> **Kindrel said:**
> Granted I don't know how to make a backup on Ubuntu... so wish me luck!

Oh, hey something else you could try...

[http://ge.ubuntuforums.com/showthread.php?t=598729](http://ge.ubuntuforums.com/showthread.php?t=598729)

Downgrade the kernel (choose a newer one than they mention in the thread, but same idea.)

---

### Post by Kindrel on 2008-07-24
Something's not working, cause below I did it, and below is what happened....

kindrel@kindrel-laptop:~$ find /lib/modules/ -iname "*ath*"
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/net/ath_pci.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_sample.ko
kindrel@kindrel-laptop:~$ sudo modprobe ath_pci
WARNING: Could not open '/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko': No such file or directory
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
kindrel@kindrel-laptop:~$ sudo modprobe wlan_scan_sta
kindrel@kindrel-laptop:~$ find /lib/modules/ -iname "*ath*"
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath
/lib/modules/2.6.24-19-generic/kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.24-19-generic/net/ath_hal.ko
/lib/modules/2.6.24-19-generic/net/ath_pci.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.24-19-generic/net/ath_rate_sample.ko

---

### Post by Kindrel on 2008-07-24
Stupid question... but what you're saying is if I follow those instructions I can downgrade to a different kernel?

Okay I'm searching all of the Ubuntu - software package area... and I can't find anything that would indication to me where I could get the Hardy heron downgradee except from the heron upgrade section....

---

### Post by PatrickFisher on 2008-07-24
Your problem is here. When you do a find, it comes up with:

/lib/modules/2.6.24-19-generic/net/ath_hal.ko

but when you modprobe it tries to access:

/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko


Same with PCI. Maybe try copying the files from /net/ to /volatile/ and trying modprobe again?

PS: I don't know about downgrading the kernel. Try this first, I'll do more looking into it.

---

### Post by Kindrel on 2008-07-24
I no longer have the /volatile/ file because I remember receiving this:

"try to remove one of these (but make a backup first), e.g.
sudo mv /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko ~"

So I did.  


But I understand your logic.  Only I'm not TOO entirely sure how to get into the /net/ and now the /volatile/ files and copy them to each others folders.  

I know the commands of cp and mv of Ubuntu, but moving them, I'm not comfortable doing.  Unless I get step by step instructions (at least a couple of times).

---

### Post by PatrickFisher on 2008-07-24
> **Kindrel said:**
> I no longer have the /volatile/ file because I remember receiving this:

"try to remove one of these (but make a backup first), e.g.
sudo mv /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko ~"

So I did.  


But I understand your logic.  Only I'm not TOO entirely sure how to get into the /net/ and now the /volatile/ files and copy them to each others folders.  

I know the commands of cp and mv of Ubuntu, but moving them, I'm not comfortable doing.  Unless I get step by step instructions (at least a couple of times).

Ok, what they did there was mow ath_hal.ko to your home directory, but hopefully the ath_hal.ko in /net/ should be good, but to be sure, we'll just copy it. try this:

cp /lib/modules/2.6.24-19-generic/net/ath_hal.ko /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko

and repeat for pci.

I'm not sure this will work

---

### Post by Kindrel on 2008-07-24
Didn't work.  

cp /lib/modules/2.6.24-19-generic/net/ath_hal.ko /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko
cp: cannot create regular file `/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko': Permission denied

I'm the only person using this laptop, why is it denied?

---

### Post by Kindrel on 2008-07-24
[http://ubuntuforums.org/showthread.php?t=631752](http://ubuntuforums.org/showthread.php?t=631752)

What about the above thread, any relevance?

---

### Post by voteforpedro36 on 2008-07-24
```
sudo cp /lib/modules/2.6.24-19-generic/net/ath_hal.ko /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko
```

It will ask for a password. Type your password, but nothing will show up. Just press enter, then do modprobe again.

By the way, sudo gives you root priviliges, and /lib is owned by root, so you need it.

---

### Post by PatrickFisher on 2008-07-24
> **Kindrel said:**
> Didn't work.  

cp /lib/modules/2.6.24-19-generic/net/ath_hal.ko /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko
cp: cannot create regular file `/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko': Permission denied

I'm the only person using this laptop, why is it denied?


Hehe, when you get that message, it's usually because you need to put "sudo" in front of the command...

---

### Post by Kindrel on 2008-07-24
See I'm not that smart... ;)  Thanks both for reminding me. I could copy the first ath_hal.ko successfully, but not the pci.  Then, below is modprobe....  and below that is dmesg.  Could I reinstall ubuntu on top of this version?

sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

[   23.370694] ACPI: (supports S0 S3 S4 S5)
[   23.370942] ACPI: Using IOAPIC for interrupt routing
[   23.370799] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   23.378324] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   23.378391] ACPI: EC: driver started in interrupt mode
[   23.378552] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.379507] PCI: Transparent bridge - 0000:00:08.0
[   23.379743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.379837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   23.379858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   23.379891] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   23.410238] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[   23.410670] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   23.411093] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[   23.411561] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   23.412028] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   23.412494] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   23.412965] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   23.413434] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   23.413857] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   23.414242] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[   23.414666] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   23.415091] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[   23.415515] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[   23.415943] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[   23.416367] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[   23.416836] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[   23.417263] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[   23.417688] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[   23.418113] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[   23.418441] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.418530] pnp: PnP ACPI init
[   23.418594] ACPI: bus type pnp registered
[   23.420948] pnp: PnP ACPI: found 12 devices
[   23.421010] ACPI: ACPI bus type pnp unregistered
[   23.421339] PCI: Using ACPI for IRQ routing
[   23.421400] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.433442] NET: Registered protocol family 8
[   23.433502] NET: Registered protocol family 20
[   23.433655] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   23.433892] hpet0: 3 32-bit timers, 25000000 Hz
[   23.435001] AppArmor: AppArmor Filesystem Enabled
[   23.438155] Time: hpet clocksource has been installed.
[   23.438219] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   23.438336] Could not switch to high resolution mode on CPU 0
[   23.441415] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   23.441534] Could not switch to high resolution mode on CPU 1
[   23.449431] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.449508] system 00:03: ioport range 0x1000-0x107f has been reserved
[   23.449571] system 00:03: ioport range 0x1080-0x10ff has been reserved
[   23.449634] system 00:03: ioport range 0x1400-0x147f has been reserved
[   23.449696] system 00:03: ioport range 0x1480-0x14ff has been reserved
[   23.449759] system 00:03: ioport range 0x1800-0x187f has been reserved
[   23.452428] system 00:03: ioport range 0x1880-0x18ff has been reserved
[   23.452494] system 00:04: ioport range 0x360-0x361 has been reserved
[   23.452556] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   23.452625] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[   23.452700] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   23.452774] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   23.452847] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[   23.452911] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   23.452973] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[   23.453450] PCI: Bridge: 0000:00:08.0
[   23.453509]   IO window: disabled.
[   23.453569]   MEM window: f6100000-f61fffff
[   23.453629]   PREFETCH window: disabled.
[   23.453689] PCI: Bridge: 0000:00:0c.0
[   23.453748]   IO window: 4000-4fff
[   23.453806]   MEM window: f2000000-f3ffffff
[   23.453865]   PREFETCH window: f0000000-f1ffffff
[   23.453926] PCI: Bridge: 0000:00:0d.0
[   23.453984]   IO window: disabled.
[   23.454043]   MEM window: f6000000-f60fffff
[   23.454102]   PREFETCH window: disabled.
[   23.454168] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   23.454177] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.454183] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.454230] NET: Registered protocol family 2
[   23.501449] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.503126] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   23.509777] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.510637] TCP: Hash tables configured (established 524288 bind 65536)
[   23.510703] TCP reno registered
[   23.521401] checking if image is initramfs... it is
[   24.121770] Freeing initrd memory: 7551k freed
[   24.127260] Simple Boot Flag at 0x36 set to 0x1
[   24.128846] audit: initializing netlink socket (disabled)
[   24.128918] audit(1216929182.352:1): initialized
[   24.130876] VFS: Disk quotas dquot_6.5.1
[   24.131012] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.131194] io scheduler noop registered
[   24.131254] io scheduler anticipatory registered
[   24.131314] io scheduler deadline registered
[   24.131473] io scheduler cfq registered (default)
[   24.131563] pci 0000:00:00.0: Enabling HT MSI Mapping
[   24.133208] pci 0000:00:07.0: Enabling HT MSI Mapping
[   24.133287] pci 0000:00:08.0: Enabling HT MSI Mapping
[   24.133360] pci 0000:00:09.0: Enabling HT MSI Mapping
[   24.133434] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   24.133506] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   24.133578] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   24.133650] Boot video device is 0000:00:12.0
[   24.133821] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.133844] assign_interrupt_mode Found MSI capability
[   24.133923] Allocate Port Service[0000:00:0c.0:pcie00]
[   24.133986] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.134007] assign_interrupt_mode Found MSI capability
[   24.134081] Allocate Port Service[0000:00:0d.0:pcie00]
[   24.160221] Real Time Clock Driver v1.12ac
[   24.160479] hpet_resources: 0xfed00000 is busy
[   24.160514] Linux agpgart interface v0.102
[   24.160574] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.162331] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.162469] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.162628] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   24.190487] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.190551] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.200761] mice: PS/2 mouse device common for all mice
[   24.200856] cpuidle: using governor ladder
[   24.200916] cpuidle: using governor menu
[   24.201121] NET: Registered protocol family 1
[   24.201279] registered taskstats version 1
[   24.201478]   Magic number: 0:166:901
[   24.201613]   hash matches device ptyve
[   24.201735] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.201811] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.201873] EDD information not available.
[   24.201939] Freeing unused kernel memory: 320k freed
[   24.227961] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.391941] fuse init (API version 7.9)
[   24.411126] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   24.411370] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.410896] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   24.411142] ACPI: Processor [CPU1] (supports 8 throttling states)
[   24.412598] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   24.779876] usbcore: registered new interface driver usbfs
[   24.779963] usbcore: registered new interface driver hub
[   24.780797] usbcore: registered new device driver usb
[   24.790609] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.791013] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[   24.791087] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 18 (level, low) -> IRQ 18
[   24.791430] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.791437] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.791786] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   24.791881] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[   24.824479] SCSI subsystem initialized
[   24.849610] usb usb1: configuration #1 chosen from 1 choice
[   24.849698] hub 1-0:1.0: USB hub found
[   24.849763] hub 1-0:1.0: 7 ports detected
[   24.870395] libata version 3.00 loaded.
[   24.951773] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[   24.951841] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z018] -> GSI 18 (level, low) -> IRQ 18
[   24.952201] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.952208] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   24.952334] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   24.952420] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[   25.009336] usb usb2: configuration #1 chosen from 1 choice
[   25.009423] hub 2-0:1.0: USB hub found
[   25.009489] hub 2-0:1.0: 2 ports detected
[   25.110757] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   25.110833] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 22
[   25.111197] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   25.111203] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   25.111321] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   25.111422] ehci_hcd 0000:00:02.1: debug port 1
[   25.111484] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   25.111496] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[   25.254774] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   25.265992] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.266182] usb usb3: configuration #1 chosen from 1 choice
[   25.266268] hub 3-0:1.0: USB hub found
[   25.266332] hub 3-0:1.0: 7 ports detected
[   25.370953] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   25.371021] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z019] -> GSI 22 (level, low) -> IRQ 22
[   25.371402] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   25.371409] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   25.371529] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   25.371632] ehci_hcd 0000:00:04.1: debug port 1
[   25.371693] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   25.371700] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[   25.382482] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.382647] usb usb4: configuration #1 chosen from 1 choice
[   25.382728] hub 4-0:1.0: USB hub found
[   25.382790] hub 4-0:1.0: 2 ports detected
[   25.485712] pata_amd 0000:00:06.0: version 0.3.10
[   25.485778] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   25.486277] scsi0 : pata_amd
[   25.486394] scsi1 : pata_amd
[   25.486742] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   25.486806] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   25.821878] ata1.00: ATAPI: PIONEER DVDRW  DR-KD08HB, 1K09, max MWDMA2
[   26.009657] ata1.00: configured for MWDMA2
[   26.009755] ata2: port disabled. ignoring.
[   26.047557] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW  DR-KD08HB 1K09 PQ: 0 ANSI: 5
[   26.048442] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   26.048865] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   26.048936] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 20
[   26.049110] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   26.065094] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   26.231170] usb 4-2: configuration #1 chosen from 1 choice
[   26.547388] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   26.568479] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1e:68:82:13:c9
[   26.568560] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   26.569038] PCI: Enabling device 0000:02:05.0 (0100 -> 0102)
[   26.569429] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   26.569500] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   26.621749] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   26.625910] ahci 0000:00:09.0: version 3.0
[   26.626202] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   26.626269] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 23
[   26.788035] usb 1-2: configuration #1 chosen from 1 choice
[   26.807482] usbcore: registered new interface driver hiddev
[   26.813100] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input2
[   26.834854] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2
[   26.844890] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-2
[   26.845117] usbcore: registered new interface driver usbhid
[   26.845181] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.625843] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   27.625923] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   27.625988] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   27.626296] scsi2 : ahci
[   27.626423] scsi3 : ahci
[   27.626522] scsi4 : ahci
[   27.626616] scsi5 : ahci
[   27.626750] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 509
[   27.626825] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 509
[   27.626898] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 509
[   27.626971] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 509
[   27.893397] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b000ad20701]
[   28.264507] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.264343] ata3.00: ATA-8: FUJITSU MHZ2320BH G2, 8909, max UDMA/100
[   28.264412] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.264961] ata3.00: configured for UDMA/100
[   28.583841] ata4: SATA link down (SStatus 0 SControl 300)
[   28.903170] ata5: SATA link down (SStatus 0 SControl 300)
[   29.222505] ata6: SATA link down (SStatus 0 SControl 300)
[   29.222672] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHZ2320B 8909 PQ: 0 ANSI: 5
[   29.232607] Driver 'sd' needs updating - please use bus_type methods
[   29.234115] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   29.234190] sd 2:0:0:0: [sda] Write Protect is off
[   29.234254] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.234268] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.234383] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   29.234457] sd 2:0:0:0: [sda] Write Protect is off
[   29.234528] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.234543] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.234621]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.311289]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[   29.338561] sd 2:0:0:0: [sda] Attached SCSI disk
[   29.344729] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   29.344813] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.432961] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.433042] Uniform CD-ROM driver Revision: 3.20
[   29.433160] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   29.653415] Attempting manual resume
[   29.653476] swsusp: Resume From Partition 8:5
[   29.653478] PM: Checking swsusp image.
[   29.653073] PM: Resume from disk failed.
[   29.691183] kjournald starting.  Commit interval 5 seconds
[   29.691263] EXT3-fs: mounted filesystem with ordered data mode.
[   36.551434] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.579380] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.623362] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   36.802539] input: Power Button (FF) as /devices/virtual/input/input4
[   36.841741] ACPI: Power Button (FF) [PWRF]
[   36.842349] input: Sleep Button (CM) as /devices/virtual/input/input5
[   36.862738] ACPI: Sleep Button (CM) [SLPB]
[   36.862917] input: Lid Switch as /devices/virtual/input/input6
[   36.863505] ACPI: Lid Switch [LID]
[   36.863666] input: Power Button (CM) as /devices/virtual/input/input7
[   36.894705] ACPI: Power Button (CM) [PWRB]
[   36.895281] ACPI: AC Adapter [ACAD] (off-line)
[   37.018713] nvidia: module license 'NVIDIA' taints kernel.
[   37.332402] ACPI: Battery Slot [BAT0] (battery present)
[   37.332594] ACPI: WMI-Acer: Mapper loaded
[   37.332876] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   37.332946] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16 (level, low) -> IRQ 16
[   37.333113] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   37.333339] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   37.642569] ricoh-mmc: Ricoh MMC Controller disabling driver
[   37.642637] ricoh-mmc: Copyright(c) Philip Langdale
[   37.642750] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   37.642831] ricoh-mmc: Controller is now disabled.
[   37.797432] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   37.824918] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   37.832798] sdhci: Secure Digital Host Controller Interface driver
[   37.832865] sdhci: Copyright(c) Pierre Ossman
[   37.832984] sdhci: SDHCI controller found at 0000:02:05.1 [1180:0822] (rev 22)
[   37.833410] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   37.833481] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNK2] -> GSI 7 (level, low) -> IRQ 7
[   37.833845] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   37.834012] mmc0: SDHCI at 0xf6100800 irq 7 DMA
[   38.050221] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   38.380117] ath_pci: disagrees about version of symbol _ath_hal_attach
[   38.380247] ath_pci: Unknown symbol _ath_hal_attach
[   38.380474] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   38.380614] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   38.381130] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   38.381259] ath_pci: Unknown symbol ath_hal_computetxtime
[   38.381635] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   38.381763] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   38.382051] ath_pci: Unknown symbol _ath_hal_detach
[   38.382669] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   38.383276] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   38.383405] ath_pci: Unknown symbol ath_hal_init_channels
[   38.383766] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   38.383906] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[   38.449172] Linux video capture interface: v2.00
[   38.523990] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   38.524066] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   38.524510] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   38.542574] uvcvideo: Found UVC 1.00 device HP Webcam (0408:030c)
[   38.546169] usbcore: registered new interface driver uvcvideo
[   38.546238] USB Video Class driver (v0.1.0)
[   38.649218] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   38.728149] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   40.571979] lp: driver loaded but no devices found
[   40.652450] ath_pci: disagrees about version of symbol _ath_hal_attach
[   40.652520] ath_pci: Unknown symbol _ath_hal_attach
[   40.652671] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   40.652744] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   40.653216] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   40.653280] ath_pci: Unknown symbol ath_hal_computetxtime
[   40.653604] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   40.653666] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   40.653911] ath_pci: Unknown symbol _ath_hal_detach
[   40.654555] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   40.655184] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   40.655246] ath_pci: Unknown symbol ath_hal_init_channels
[   40.655554] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   40.655627] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[   40.723105] Adding 5855652k swap on /dev/sda5.  Priority:-1 extents:1 across:5855652k
[   40.749930] EXT3 FS on sda3, internal journal
[   40.947505] kjournald starting.  Commit interval 5 seconds
[   40.947919] EXT3 FS on sda6, internal journal
[   40.947923] EXT3-fs: mounted filesystem with ordered data mode.
[   41.398387] ip_tables: (C) 2000-2006 Netfilter Core Team
[  101.063178] No dock devices found.
[  101.318525] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[  101.316939] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[  101.316943] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[  101.316946] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[  101.316948] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[  102.205217] ppdev: user-space parallel port driver
[  102.298536] audit(1216954461.972:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5468 profile="/usr/sbin/cupsd" namespace="default"
[  103.033361] Clocksource tsc unstable (delta = -80819726 ns)
[  103.905527] Bluetooth: Core ver 2.11
[  103.905611] NET: Registered protocol family 31
[  103.905613] Bluetooth: HCI device and connection manager initialized
[  103.905617] Bluetooth: HCI socket layer initialized
[  103.912273] Bluetooth: L2CAP ver 2.9
[  103.912278] Bluetooth: L2CAP socket layer initialized
[  103.944088] Bluetooth: RFCOMM socket layer initialized
[  103.944104] Bluetooth: RFCOMM TTY layer initialized
[  103.944106] Bluetooth: RFCOMM ver 1.8
[  106.402671] NET: Registered protocol family 17
[  107.428562] NET: Registered protocol family 10
[  107.429027] lo: Disabled Privacy Extensions
[  112.407799] eth0: no IPv6 routers present
[  117.489383] CPU0 attaching NULL sched-domain.
[  117.489392] CPU1 attaching NULL sched-domain.
[  117.496667] CPU0 attaching sched-domain:
[  117.496675]  domain 0: span 03
[  117.496677]   groups: 01 02
[  117.496680]   domain 1: span 03
[  117.496681]    groups: 03
[  117.496683]    domain 2: span 03
[  117.496684]     groups: 03
[  117.496686] CPU1 attaching sched-domain:
[  117.496688]  domain 0: span 03
[  117.496689]   groups: 02 01
[  117.496691]   domain 1: span 03
[  117.496692]    groups: 03
[  117.496694]    domain 2: span 03
[  117.496695]     groups: 03
[  469.511514] ath_pci: disagrees about version of symbol _ath_hal_attach
[  469.511525] ath_pci: Unknown symbol _ath_hal_attach
[  469.511622] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  469.511625] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  469.512061] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  469.512062] ath_pci: Unknown symbol ath_hal_computetxtime
[  469.512349] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  469.512352] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  469.512546] ath_pci: Unknown symbol _ath_hal_detach
[  469.513182] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  469.513803] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  469.513810] ath_pci: Unknown symbol ath_hal_init_channels
[  469.514079] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  469.514081] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  550.928506] ath_pci: disagrees about version of symbol _ath_hal_attach
[  550.928512] ath_pci: Unknown symbol _ath_hal_attach
[  550.928610] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  550.928612] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  550.929084] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  550.929086] ath_pci: Unknown symbol ath_hal_computetxtime
[  550.929367] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  550.929369] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  550.929562] ath_pci: Unknown symbol _ath_hal_detach
[  550.930192] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  550.930797] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  550.930799] ath_pci: Unknown symbol ath_hal_init_channels
[  550.931067] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  550.931069] ath_pci: Unknown symbol ath_hal_getwirelessmodes

---

### Post by Kindrel on 2008-07-24
Could there be a possibility that my /etc/modules file is screwing things up????

---

### Post by PatrickFisher on 2008-07-24
What's the error when you try to copy the pci file?

---

### Post by PatrickFisher on 2008-07-24
Wait! found something...

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

That is exactly what you have to do. Follow the directions in the FIRST post, because you have a 64 bit system.

---

### Post by Kindrel on 2008-07-24
Error?  It did nothing.  It didn't even ask me for my password.  It was if it totally ignored me.  lol.

---

### Post by PatrickFisher on 2008-07-24
Oh, that means it worked. You only have to enter the sudo password once every ten minutes. Anyways, try the above.

---

### Post by Kindrel on 2008-07-25
Okay... currently installing MadWiFi into my labtop... though it's asking me to execute scripts to remove current modules from my system, but it's not seeming to be working.  

It's as though all my previous devices are down.  Can I still continue to install with them?  For my 64-bit?

---

### Post by Kindrel on 2008-07-25
I JUST discovered something interesting.  While in the process of creating a MadWifi directory to extract the files from the MadWifi website to fix my 64-bit problem... so I hope.  

I found that in my computer there's a folder called "MadWifi-hal-0.10.5.6" and I'm assuming that's causing some problems.  I believed it was installed by the person who installed my Ubuntu to begin with and adjusted wireless initially to work.  

So with this being said... does this cause a problem?  And if so how do I deal with it?

---

### Post by Kindrel on 2008-07-26
Anyone???  

Should I do a straight reinstall of Ubuntu???  And start all over??  

If so I'm wondering if it's my router D-Link G with Rangebooster playing a problem in this (as my friend who has the exact same labtop & config as I have, except with a different router - doesn't have this problem)

Or should I use Windows Wireless Driver to try to get the *.inf driver to run, if so I don't know what I'm looking for...

See how complicated this is???

---

### Post by Kevbert on 2008-07-26
Hi.  I've had a look at all these posts and have some questions.
Would I be right in thinking you have an Acer laptop ?  What's the model ?
When you boot into Windows is the wireless on by default ? or do you have to press a button first ?  If so, please make sure it is on before you boot into Ubuntu.
What version of Ubuntu are you using ? and is it Ubuntu, Kubuntu or Xubuntu ?

---

### Post by Kindrel on 2008-07-26
Actually I have a HP Pavillion dv6000 labtop.  And when I boot into Windows Vista it's generally connected.  The on/off switch is at the front of the computer and it's always kept to the right (on), so when I boot into Windows vista, it's blue which means it's on.  And now with Ubuntu "Hardy Heron" when wireless is on the LED is orange.

---

### Post by Kevbert on 2008-07-26
I've had a quick google around and it looks like the wireless may be broadcom based.  Seeing as wireless has worked and assuming that you performed an update/upgrade to Ubuntu copying the Broadcom files from the other PC to your /lib/firmware directory may be the best bet.  The alternative is to look at the other laptop and run ```
lspci
``` in terminal on that to find out the model and revision of drivers you require.  Once you have that you could run through the guide[COLOR="Red"][ here]("http://ubuntuforums.org/showthread.php?t=766560")[/COLOR].  You need to find the revision for the sub-link in step 2.
Good luck.

---

### Post by chili555 on 2008-07-26
> I've had a quick google around and it looks like the wireless may be broadcom based.His *lshw* posted previously, indicates it's the famous Atheros AR242x. I don't believe the Broadcom instructions will help.

---

### Post by Kindrel on 2008-07-26
I thought it was Atheros Wireless.... hmmm.... I'll take a look at the other computer and take a look.

---

### Post by Kevbert on 2008-07-26
> **chili555 said:**
> His *lshw* posted previously, indicates it's the famous Atheros AR242x. I don't believe the Broadcom instructions will help.

My mistake... if an update has caused the problem it still may be possible to use the firmware files from another identical laptop and save them in the /lib/firmware directory.  Yes the infamous Atheros...

---

### Post by chili555 on 2008-07-26
> I found that in my computer there's a folder called "MadWifi-hal-0.10.5.6" and I'm assuming that's causing some problems.Maybe not. I assume it's in the /home/kindrel directory. Open a terminal and do these commands:```
cd madWifi-hal-0.10.5.6
make clean
make
sudo make install
sudo modprobe ath_pci
```Does your wireless come back to life?

---

### Post by Kevbert on 2008-07-26
> **chili555 said:**
> Maybe not. I assume it's in the /home/kindrel directory. Open a terminal and do these commands:```
cd madWifi-hal-0.10.5.6
make clean
make
sudo make install
sudo modprobe ath_pci
```Does your wireless come back to life?

It was almost definitely an update that caused the problem. Whatever works you should make a note of as it looks like a common problem that's likely to occur again and again.  There's also been one or two bugs reported on launchpad.

---

### Post by Kindrel on 2008-07-26
Chili,

I did what you said, but everything worked up til the last part....

kindrel@kindrel-laptop:~/madwifi-hal-0.10.5.6$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I'm looking hopeful now.........  :)

---

### Post by Kindrel on 2008-07-27
Thank you soooooo very much to helping me get my wireless back and running!!

:ks

---

