---
title: "Internet Connections"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by GodlySoup on 2011-07-11
So I install Jaunty on my friend's Acer and the network connections aren't working. Plugging it in or wireless. How do I approach this? Do I need to download the drivers on my computer and transfer them over to his?

---

### Post by jtarin on 2011-07-11
A hardwire should be able to just work.....how are you connecting? DSL,cable etc;
Are you using a router, modem etc;
Issue the command "ifconfig" and post the output here.

---

### Post by GodlySoup on 2011-07-11
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4504 (4.5 KB)  TX bytes:4504 (4.5 KB)

pan0      Link encap:Ethernet  HWaddr c6:15:b1:7e:b0:3e  
          inet6 addr: fe80::c415:b1ff:fe7e:b03e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)


```

Edit: It's a wireless router. DSL I guess. Works fine on the several other laptops around ze house. Just need to figure out how to set it up.. Last computer I had with Ubuntu just automatically worked.

---

### Post by westie457 on 2011-07-11
> **GodlySoup said:**
> ```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4504 (4.5 KB)  TX bytes:4504 (4.5 KB)

pan0      Link encap:Ethernet  HWaddr c6:15:b1:7e:b0:3e  
          inet6 addr: fe80::c415:b1ff:fe7e:b03e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)


```

Edit: It's a wireless router. DSL I guess. Works fine on the several other laptops around ze house. Just need to figure out how to set it up.. Last computer I had with Ubuntu just automatically worked.

Hi looks to me that there is no eth0 or wlan0 device on your system. I believe the pan0 is an adhoc network to a blue tooth device. Though why other things are not showing I cannot understand. Could you run lspci and post the result please?

---

### Post by GodlySoup on 2011-07-11
> **westie457 said:**
> Hi looks to me that there is no eth0 or wlan0 device on your system. I believe the pan0 is an adhoc network to a blue tooth device. Though why other things are not showing I cannot understand. Could you run lspci and post the result please?

Here it is:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
08:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
```

Is this just a driver issue?

---

### Post by alphacrucis2 on 2011-07-11
> **GodlySoup said:**
> Here it is:



Is this just a driver issue?

Post output of 

```
sudo lshw -C network
```

BTW I take it that you realise that Jaunty (Ubuntu 9.04) is out of support?

---

### Post by GodlySoup on 2011-07-11
> **alphacrucis2 said:**
> Post output of 

```
sudo lshw -C network
```BTW I take it that you realise that Jaunty (Ubuntu 9.04) is out of support?

I kind of got that sneaky suspicion. Is that the reason it isn't working?

```
  *-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:15:b1:7e:b0:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by alphacrucis2 on 2011-07-11
> **GodlySoup said:**
> I kind of got that sneaky suspicion. Is that the reason it isn't working?

```
  *-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:15:b1:7e:b0:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

So no driver is assigned to these devices. "Unclaimed". You may be able to get drivers for them (even Windows drivers using NDISwrapper) but you might find it less hassle to try an up to date distro that supports them out of the box. The easiest way is to download and burn a Ubuntu live CD and boot into it and select the "Try Ubuntu" option. If the live CD supports the ethernet and or wireless then you are good to install. If the latest live CD doesn't support the network devices then you are in for a bit of messing around manually installing drivers. It can be a good learning exercise anyway.

---

### Post by jtarin on 2011-07-11
[This]("http://ubuntuforums.org/showthread.php?t=75451") should get you up and running.

[MadWifi Home and install instructions]("http://madwifi-project.org/wiki")

---

### Post by 3rdalbum on 2011-07-11
Stop messing around with an ancient version of Ubuntu, just install Ubuntu 11.04 and it'll probably work out-of-the-box.

---

### Post by jtarin on 2011-07-11
> **3rdalbum said:**
> Stop messing around with an ancient version of Ubuntu, just install Ubuntu 11.04 and it'll probably work out-of-the-box.11.04 doesn't work for everyone. If I was to recommend a newer version for someone new to Linux it would be 10.04 or 10.10.

---

### Post by wep940 on 2011-07-12
+1 - especially since (as I learned recently) 11.04 is NOT a long term support release.  10.04 is the latest LTS release and what I would go with.  Nobody claims 11.04 to be bad, perhaps a little buggy here and there, but I would go with the latest LTS release.  I tried 11.04 on my desktop and on my laptop and just personally it wasn't for me at this time.
 
Also, I'd be interested in how the MadWifi things turn out, as I was under the impression from the web site a few months ago that they got out of the "to the individual" driver releases and were instead concentrating on building drivers for inclusion in Linux distributions.  So, if the MadWifi things still work I'd like to know.
 
As mentioned, there is always using ndiswrapper and the Windows drivers.  Some people frown on this, but when there are no native drivers and you can't get it to work, it's a good option.  Especially for people who have no network connection so they need ndiswrapper just to get going.  There are a LOT of outdated old posts out there are using it - ignore those and just post back if you want to try that route as it is VERY simple now - just be sure you have Windows XP (only) drivers that match your OS architecture - 32 or 64 bit.
 
However, and it may take me a while to find it, I thought that the your device was supported now - perhaps requiring the unloading of a kernel module and the loading of another.

---

### Post by wep940 on 2011-07-12
I think there are a couple of ways to approach this.  The first would be to follow this thread so you can download the package on another PC and bring it to yo(ur ubuntu box:  [http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)
 
The other, if you can get a hard-wired connection running, is to enable the backports - this will get the driver for you.
 
From what I've read, some people have problems with the MadWifi drivers and your particular chipset.  There have also been problems reported when trying to use it with wicd - almost every post I read said to use network manager.
 
And, the most important thing (as has already been mention), is to install 10.04 first.

---

