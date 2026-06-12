---
title: "Ubuntu limiting the internet bandwith"
date: 2019-10-23
forum: Networking &amp; Wireless
---

### Post by thiagoandf on 2019-10-23
Hello there!

Recently we have noticed that a few computers at work that use Ubuntu are having their internet speed limited. 
We tried every troubleshooting method we could think of (more or less in this order): 
- Restarted the affected computers, 
- Changed the cables (including using a cable that provides the correct internet speed on other computers),
- Changed the switch settings for the affected computers,
- Changed the port in which the computer is connected to the switch,
- Changed most Ubuntu network settings

The only thing that changed the speed was using our office phone as a switch (connection became ISP -> Switch -> Phone -> Computer).

It's important to note that this issue affects just some of the computer running Ubuntu in the office. If the computer is running Windows it isn't affected.
Also important to note that only the download speed is affected, upload speeds are normal in all machines.

All connections are cabled. All machines running Ubuntu 19.04.

Attached to this post is a screenshot of an affected Ubuntu machine and another of a non-affected one, both taken almost at the same time with both machines running Chrome on Ubuntu 19.04.

---

### Post by TheFu on 2019-10-23
NIC device drivers?
How is the speed between systems on the same LAN?
You have a phone between the computer and the internet?  Why?  Cheap ATAs are  uh .... cheap.  Try removing the phone/ATA.

Running a non-LTS inside a business seems like a less-than-good idea.

Simplify and test.  Take a problem computer and remove everything between it and the gateway - direct, CAT5e cable would be best. Test again. Does that solve the issue?  Then add in 1 more thing at a time and retest.

---

### Post by thiagoandf on 2019-10-23
Thanks for the reply! Hope the info helps.

> **TheFu said:**
> NIC device drivers?

RealTek RTL-8168 Gigabit Ethernet driver
version: 8.046.00-NAPI

> **TheFu said:**
> How is the speed between systems on the same LAN?

Normal, no problems there

> **TheFu said:**
> You have a phone between the computer and the internet?  Why?  Cheap ATAs are  uh .... cheap.  Try removing the phone/ATA.

We don't, that's just a test we did to check if the problem was with the connection between the switch and the computer. Btw, the phone we used was a Cisco IP Phone SPA502G

> **TheFu said:**
> Running a non-LTS inside a business seems like a less-than-good idea.

I believe that, if the Ubuntu version was the issue, the problem would happen in all computers running 19.04, which is not the case.

> **TheFu said:**
> Simplify and test.  Take a problem computer and remove everything between it and the gateway - direct, CAT5e cable would be best. Test again. Does that solve the issue?  Then add in 1 more thing at a time and retest.

The connection to the computer comes straight from the switch with a CAT5e cable. Nothing in between :/

---

### Post by TheFu on 2019-10-23
Still need to isolate the issue.  Simplify and test.

Support for 19.04 ends in 2.5 months.  Probably worth moving to 19.10 to see if that fixes anything. I doubt it will, but for a company, planning an OS migration takes a few months and being out of support isn't an option.

I've avoided realtek for years now.  Can you swap in an Intel PRO/1000 NIC and test one of the problem boxes?  Simplify and test. If nothing else changes, then you know it is related to realtek. If it doesn't matter, you've ruled out realtek.

If the connection from the computer isn't directly to the gateway, then there is something in the middle. 
Simplify and test.

When posting command output, please post the exact command and the output inside "*code tags*".  Otherwise, we don't know what we are seeing.

The fact that the issue is only on the WAN and not the LAN tells me it is a gateway or proxy or routing issue, nothing about the clients.  Have you swapped an ok and slow computer around?  Seems you believe all of the systems are identical.  I wouldn't assume that without checking myself.  I'd probably use ansible to do that if more than 5 PCs are involved.

---

### Post by thiagoandf on 2019-10-24
> **TheFu said:**
> Still need to isolate the issue.  Simplify and test.

Support for 19.04 ends in 2.5 months.  Probably worth moving to 19.10 to see if that fixes anything. I doubt it will, but for a company, planning an OS migration takes a few months and being out of support isn't an option.

I've avoided realtek for years now.  Can you swap in an Intel PRO/1000 NIC and test one of the problem boxes?  Simplify and test. If nothing else changes, then you know it is related to realtek. If it doesn't matter, you've ruled out realtek.

If the connection from the computer isn't directly to the gateway, then there is something in the middle. 
Simplify and test.

When posting command output, please post the exact command and the output inside "*code tags*".  Otherwise, we don't know what we are seeing.

The fact that the issue is only on the WAN and not the LAN tells me it is a gateway or proxy or routing issue, nothing about the clients.  Have you swapped an ok and slow computer around?  Seems you believe all of the systems are identical.  I wouldn't assume that without checking myself.  I'd probably use ansible to do that if more than 5 PCs are involved.


We are a very small company, so upgrading the systems is not a problem. I'll try formatting an affected machine with a fresh install of 19.10 and check if the problem solves itself.

About swapping to an Intel adaptor. We use Dell machines that come with the adaptor soldered to the motherboard, so that's not really an option.

While testing, we swapped the cables from a normal machine to an affected machine, and the speeds continued to be the same (the affected machine was still slow and the good machine was still good). We also tried installing Windows in one of the affected machines and the problem solved itself. That's when we figured it was probably something to do with Ubuntu itself, not the machines.

We had never heard of ansible, will give it a try to check if it offers any answers.

Bellow is the complete output of the version of the NIC driver.

```
 
$ modinfo r8168
                  filename:       /lib/modules/5.0.0-32-generic/updates/dkms/r8168.ko
version:        8.046.00-NAPI
license:        GPL
description:    RealTek RTL-8168 Gigabit Ethernet driver
author:         Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion:     1B7F4580601BCFA0300F9D2
alias:          pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
alias:          pci:v000010ECd00008161sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:        
retpoline:      Y
name:           r8168
vermagic:       5.0.0-32-generic SMP mod_unload 

```

---

### Post by TheFu on 2019-10-24
Ah, the r8168 driver strikes again!

**sudo lshw -C network** will show the actual NIC, not just the driver selected.  You will probably discover it is some funky realtek NIC and the needed driver is well-known.  When you see the ,multiple card numbers, searching for solutions is much easier.  I have a "RTL8111/**8168**/8411" in 1 system here. It uses the r8169.ko driver.  Why would a NIC with 8168 in the name use a 8169 driver?  Thanks realtek. They do make NICs with 8169 in the name, BTW.

Thanks for the reminder about the cable swap.

Just because the NIC is on the motherboard, that doesn't mean you can't disable it in the BIOS and put another PCIe NIC in a slot for use.  Probably won't need to do this.

Drivers are not Canonical or Linux.  They are the vendor's problem.  Complain to them about their poor support, poor deployment, ambiguous choices.

Ansible works over ssh from a single workstation and every admin should have ssh into every system they manage.  With ansible setup, you can easily pull information (setup module) or run remote commands on all systems.
```
$ ansible -i hosts -a "cat /var/run/reboot-required" powered
```
That is how I know which machines need to be rebooted after patching on Saturday mornings.  The 'hosts' option is deprecated for newer Ansible versions.  'powered' is just a way I group systems that should be running inside the hosts inventory file.

---

### Post by thiagoandf on 2019-10-24
After a lot of research I'm back here.

Running **sudo lshw -C network **showed me I was running the version r8168 of the driver:

```
  
*-network                        description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: d0:94:66:af:23:cb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8168 driverversion=8.047.02-NAPI duplex=full ip=192.168.0.182 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:126 ioport:3000(size=256) memory:e4204000-e4204fff memory:e4200000-e4203fff

```

It's true that searching for the adaptor model, I found several other users with similar problems, but all solutions were to install the updated r8168 (eg: [https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/) and several others). 
I tried installing several different versions of the driver as well, but none of them worked. 

Do you still have the file you used to configure the RTL8111/8168/8411 machine you have there? 

In the mean time, I'll try to contact Realtek to see if they have a solution.

About ansible, I'll make sure to check it out, it seems extremely useful. 

Thanks a lot for the help!

---

### Post by TheFu on 2019-10-24
So, the description of your NIC and mine seem to be different versions, yet mine automatically selected the r8169 driver but yours didn't?  Be certain when searching for answers that the card/NIC version matches yours.  

I've seen claims that the r8169 driver is buggy. Haven't noticed it here and it has been working 24/7/366 for over 5 yrs on an NFS and VM server.

Exact HW on 1 machine here:
```
$ sudo lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
02:00.0 Ethernet controller: **Realtek Semiconductor Co., Ltd. RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller (rev **0c**)
        Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
        Flags: bus master, fast devsel, latency 0, IRQ 27
        I/O ports at e000 [size=256]
        Memory at f7e00000 (64-bit, non-prefetchable) [size=4K]
        Memory at f0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number xx-xx-xx-xx-xx-xx-xx-xx-xx
        Capabilities: [170] Latency Tolerance Reporting
        Kernel driver in use: r8169
        Kernel modules: r8169
```
See how I show the command AND the output?  That helps others solve their own issues.  I did xx the MAC for privacy
Can't run **lshw** on the machine. It just locks up the command and never finishes due to a less-than-great SATA controller. That's what I get using a $49.99 MB. ;)

The box also has a cheap Marvell NIC installed.  Other servers all use Intel NICs.  Much, much, less hassles - actually, zero hassles.  *Intel Corporation I211* are pretty painless next time you shop and have good BSD support while using fewer interrupts of the OS for high workloads.  Hardware that supports BSD is usually extremely stable on Linux and virtual machine hosts.

Can you check every machine to see if some picked the r8169 driver?

BTW, we are on 16.04 here.  We don't touch non-LTS releases and 18.04 has enough issues for us not to want it.  We don't have any plans to use 18.04.

Might just need to blacklist the r8168 driver so the r8169 gets picked at boot. I don't have that blacklist on the machine here.  I haven't need to pull network drivers down in at least 15 yrs, perhaps longer.

---

### Post by thiagoandf on 2019-10-28
So, first of all, sorry for the delay replying. 

I tried blacklisting the r8168 and it was completely ignored, as you can see by the results below (btw, thanks for the tips on how to show code, I'm not really experienced on writing forum posts).

```

$ sudo lshw -C network  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: **:**:**:**:**:**
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8168 driverversion=8.047.02-NAPI duplex=full ip=192.168.0.183 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:126 ioport:3000(size=256) memory:e4204000-e4204fff memory:e4200000-e4203fff



```

```

$ sudo lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
     02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 126
	I/O ports at 3000 [size=256]
	Memory at e4204000 (64-bit, non-prefetchable) [size=4K]
	Memory at e4200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number **-**-**-**-**-**-**-**
	Capabilities: [170] Latency Tolerance Reporting
	Capabilities: [178] L1 PM Substates
	Kernel driver in use: **r8168**
	Kernel modules: **r8168**

```

Realtek replied to my email asking for the correct driver, but they sent the r8168-8.047.04 driver. I tried installing it but, as expected, it didn't work. I replied saying it didn't work, but haven't heard back yet. Will post an update here if they send something different.

We bought some new machines last week for some people we are hiring, and they come with the same adapter, but don't have the same problem (they came if the r8169 driver installed and it works even on Ubuntu 19.10. The output is exactly like of your machines above). Do you know if there's a way to extract the driver they use?

---

