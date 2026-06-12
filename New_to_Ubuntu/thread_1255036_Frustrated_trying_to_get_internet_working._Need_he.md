---
title: "Frustrated trying to get internet working. Need help."
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-09-01
Okay, so I am absolutely completely utterly you get the point frustrated! I just cannot, no matter what, get internet access on my laptop with Ubuntu 9.04! I tried everything: restarting my computer, asking my friend for help (who works with Linux daily at work), restarting Network manager, reinstalling Network manager, uninstalling NM and installing wicd, and then finally posting here. 

(Okay...a little less frustrated now that I got that out of me)

Anyways, my problem is that I cannot use anything that requires the internet in Ubuntu 9.04, though both Network manager, and Wicd when I tried either tell me I am connected. Now Wicd refuses to even connect. I have only tried to connect to my home network, and not any others (as all the other networks in my neighborhood are secured). I could connect to the internet perfectly fine for about the first week after I installed Ubuntu to dual boot with Vista. Then I went for a weekend vacation (I brought my laptop along, and tried to connect to a couple unsecured networks by the hotel), and when I got back, I ran into the problem outlined at the top of this pararaph. I could get internet within a Live CD enviroment, so I reinstalled Ubuntu. Completely. This fixed the problem for about a day, then it came back with the same problem. I tried restarting, asking a friend knowledgeable about Linux, unistallling Network Manager and installing Wicd, that didn't work, and then finally turning my computer off and saying to hell with this. After about 4 days I went back to it and tried even harder to fix the problem. I tried changing some of the preferences randomly to see if it made a difference. All this did was get Wicd to refuse to connect to the network at all.

My experience with Linux has been, to sum it all up, *a pain in the ****. I could not hibernate/suspend, spent about 6 hours googling and posting here before I fixed it. Then I spent another 5 hours googling and pasting to be able simply play a movie from a Dvd. Then I spend a week trying to fix this damn issue, which *still *hasn't been solved.

Thank you for bearing with me for being a bit whiney, but I am pretty frustrated with both myself an Ubuntu right now, and would like to stay a Linux user and not have to go back to Windows.        

Scott

---

### Post by oboedad55 on 2009-09-01
> **Windows Nerd said:**
> Okay, so I am absolutely completely utterly you get the point frustrated! I just cannot, no matter what, get internet access on my laptop with Ubuntu 9.04! I tried everything: restarting my computer, asking my friend for help (who works with Linux daily at work), restarting Network manager, reinstalling Network manager, uninstalling NM and installing wicd, and then finally posting here. 

(Okay...a little less frustrated now that I got that out of me)

Anyways, my problem is that I cannot use anything that requires the internet in Ubuntu 9.04, though both Network manager, and Wicd when I tried either tell me I am connected. Now Wicd refuses to even connect. I have only tried to connect to my home network, and not any others (as all the other networks in my neighborhood are secured). I could connect to the internet perfectly fine for about the first week after I installed Ubuntu to dual boot with Vista. Then I went for a weekend vacation (I brought my laptop along, and tried to connect to a couple unsecured networks by the hotel), and when I got back, I ran into the problem outlined at the top of this pararaph. I could get internet within a Live CD enviroment, so I reinstalled Ubuntu. Completely. This fixed the problem for about a day, then it came back with the same problem. I tried restarting, asking a friend knowledgeable about Linux, unistallling Network Manager and installing Wicd, that didn't work, and then finally turning my computer off and saying to hell with this. After about 4 days I went back to it and tried even harder to fix the problem. I tried changing some of the preferences randomly to see if it made a difference. All this did was get Wicd to refuse to connect to the network at all.

My experience with Linux has been, to sum it all up, *a pain in the ****. I could not hibernate/suspend, spent about 6 hours googling and posting here before I fixed it. Then I spent another 5 hours googling and pasting to be able simply play a movie from a Dvd. Then I spend a week trying to fix this damn issue, which *still *hasn't been solved.

Thank you for bearing with me for being a bit whiney, but I am pretty frustrated with both myself an Ubuntu right now, and would like to stay a Linux user and not have to go back to Windows.        

Scott

Scott, take a deep breath. :P I know it's a tendency to want to un-install, reinstall, when things don't work. That's a windows holdover, and it does sometimes work. I've found it's better to try and find another solution before I start frantically reinstalling stuff. 
The best way to start is to give us your computer specs, including which wireless and ethernet cards you have. I had a similar problem with a common wireless card on my laptop and I found a simple solution that didn't require frantic reinstalling. 

--Jon

---

### Post by pablolie on 2009-09-01
can you post your computer specs from system info?
it is bizarre network managers claim you are connected when you aren't. there may be something weird about your network environment - is it all a plain vanilla dhcp environment etc?

---

### Post by nothingspecial on 2009-09-01
If I understand correctly from your previous thread, you could connect and then it stopped working. You reinstalled and it worked again, then you did your updates and it broke.

As I said before this is in all probability a kernel update problem. Boot in to your earliest available kernel. Does it work now?

---

### Post by Windows Nerd on 2009-09-01
> **pablolie said:**
> can you post your computer specs from system info?
it is bizarre network managers claim you are connected when you aren't. there may be something weird about your network environment - is it all a plain vanilla dhcp environment etc?
Whoa, plain Vanilla dhcp environment? I may have plenty of experience within Windows, what you said there is, to be quoting Shakespeare, "Greek to me".

 I will post what I can remember for my system specs off the top of my head, as my computer is off now, and I am using my iphone to answer you guys's feedback. 

160 HDD: It contains  4 partitions: a recovery partition that came with the computer, my Windows vista partition, my Ubuntu partition, and a 4 Gb swap partition.
2.5 gb RAM
An Intel 1.73 GHz Cpu
Do not know anything about my network/wireless card or drivers (I know that there is a command out there to find all this information out with a simple few words in terminal, thouh I can't seem to remember any.)

If you would like to find out the make/model or anything else about my wireless or network card, please let me know and tell me how to find it out.

If you would like to know any thing else about my system specs, tell me please and I will readily list  them here.

Scott

Scott

---

### Post by Windows Nerd on 2009-09-01
> **nothingspecial said:**
> If I understand correctly from your previous thread, you could connect and then it stopped working. You reinstalled and it worked again, then you did your updates and it broke.

As I said before this is in all probability a kernel update problem. Boot in to your earliest available kernel. Does it work now?

I have tried booting into evry kernel I have installed, and nothing changes. I shall try again, though, as I guess it is worth a try.

Scott

---

### Post by nothingspecial on 2009-09-01
> **Windows Nerd said:**
> Whoa, plain Vanilla dhcp environment? 

Normal everyday internet connection.
> 
Do not know anything about my network/wireless card or drivers (I know that there is a command out there to find all this information out with a simple few words in terminal, thouh I can't seem to remember any.)

If you would like to find out the make/model or anything else about my wireless or network card, please let me know and tell me how to find it out.

If you would like to know any thing else about my system specs, tell me please and I will readily list  them here.

```

sudo lshw -C network
```

---

### Post by Windows Nerd on 2009-09-01
> **Windows Nerd said:**
> I have tried booting into evry kernel I have installed, and nothing changes. I shall try again, though, as I guess it is worth a try.
Scott
Well, scratch that. After booting into my oldest kernel, I remembered that in my haste, I went and deleted Wicd too. So now I am left with neither network manager, nor wicd, and no way to install either. Dammit, that was so stupid of me...*sigh*

---

### Post by Windows Nerd on 2009-09-01
```
scott@scott-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c5:c0:eb
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:de:d7:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:4d:92:c0:37:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
scott@scott-laptop:~$ 
```

Scott

---

### Post by nothingspecial on 2009-09-01
You`re going to have to try to start your wireless on the command line then
```

sudo ifconfig wlan0 up
```

Then ```
iwlist wlan0 scan
```

Do you see your network?

---

### Post by Windows Nerd on 2009-09-01
> **nothingspecial said:**
> You`re going to have to try to start your wireless on the command line then
```

sudo ifconfig wlan0 up
```

Then ```
iwlist wlan0 scan
```

Do you see your network?

Nope, all it tells me is:

```
wlan0.      No scan results
```

Scott

---

### Post by nothingspecial on 2009-09-01
Just checking, it`s not a hidden network is it?

---

### Post by nothingspecial on 2009-09-01
> **Windows Nerd said:**
> ```
scott@scott-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c5:c0:eb
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:de:d7:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:4d:92:c0:37:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
scott@scott-laptop:~$ 
```

Scott

Whoops, missed this post. I don`t seem to see your card. Try

```
lspci -v
```

Just post the bits back related to network.

---

### Post by Windows Nerd on 2009-09-01
> **nothingspecial said:**
> Just checking, it`s not a hidden network is it?
Nope it is not a hidden network. 

Scott

---

### Post by anujpathania on 2009-09-01
Can you post the screenshot of your desktop here? Want to see howz the network icon behaving on Top right corner.

Also if you are able to dual boot you can see the type of wireless card you have in system information.

Also both ethernet and wifi are not working?

Also make sure your network doesn't need additional settings to work?

Is your PC a custom rig?

---

### Post by Windows Nerd on 2009-09-01
> **nothingspecial said:**
> Whoops, missed this post. I don`t seem to see your card. Try

```
lspci -v
```Just post the bits back related to network.

Sorry, wasnt really clear on which bit you wanted to see, so I posted back the whole thing:

```
scott@scott-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d4100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d4200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0
    Memory at d4180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2000000-d3ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d4444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4000000-d40fffff
    Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2302
    I/O ports at 18d0 [size=8]
    I/O ports at 18c4 [size=4]
    I/O ports at 18c8 [size=8]
    I/O ports at 18c0 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at d4444400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 2301
    Memory at d2000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at d4006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: 88000000-8bfff000 (prefetchable)
    Memory window 1: 8c000000-8ffff000
    I/O window 0: 00003000-000030ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at d4005000 (32-bit, non-prefetchable) [size=2K]
    Memory at d4000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d4004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

scott@scott-laptop:~$ 


```

I will be going to bed right now, so any more posts will go unanswered until morning. 

Scott

---

### Post by nothingspecial on 2009-09-01
> **anujpathania said:**
> Can you post the screenshot of your desktop here? Want to see howz the network icon behaving on Top right corner.



He doen`t have network manager or wicd.

---

### Post by nhasian on 2009-09-01
if lshw says your wlan0 is disabled then its no use trying to find wifi access points.  

some laptops have a hardware on/off switch.  can you verify that its set to ON?  alternatively some laptops use a keyboard combination to turn the wifi on/off.  when you boot it may default to OFF and you may have to turn it on manually.  lastly check the bios to see if there are any switches for the wifi adaptor or radio.  it may toggle from OFF/ENABLED/AUTO if thats the case, set it to enabled.

---

### Post by Windows Nerd on 2009-09-01
> **nhasian said:**
> if lshw says your wlan0 is disabled then its no use trying to find wifi access points.  

some laptops have a hardware on/off switch.  can you verify that its set to ON?  alternatively some laptops use a keyboard combination to turn the wifi on/off.  when you boot it may default to OFF and you may have to turn it on manually.  lastly check the bios to see if there are any switches for the wifi adaptor or radio.  it may toggle from OFF/ENABLED/AUTO if thats the case, set it to enabled.

Thats funny...I have the hardware switch set to enabled (as far as I can tell) and the light that notifies this is on or off is lit up, indicating it is on.

I will check the bios configuration for my card, but I think it is all set to on at boot because I can access internet perfectly fine within my windows partition....

Scott

---

### Post by Windows Nerd on 2009-09-01
> **Windows Nerd said:**
> Thats funny...I have the hardware switch set to enabled (as far as I can tell) and the light that notifies this is on or off is lit up, indicating it is on.

I will check the bios configuration for my card, but I think it is all set to on at boot because I can access internet perfectly fine within my windows partition....

Scott
Ok, checked the bios, and I found a pretty interesting situation. I am not sure if it is on or not, but this is what I saw: 

Internal LAN   [Enabled]
Wireless LAN [COLOR=Gray] [/COLOR][COLOR=Gray][Restore]
[COLOR=Black]Some other option that I cannot remember [Enabled]

I could not select Wireless LAN to change it to [Enabled]. It just skipped right to the next option.

Scott
[/COLOR]
[/COLOR]

---

### Post by LewRockwell on 2009-09-01
> **Windows Nerd said:**
> Ok, checked the bios, and I found a pretty interesting situation. I am not sure if it is on or not, but this is what I saw: 

Internal LAN   [Enabled]
Wireless LAN [COLOR=Gray] [/COLOR][COLOR=Gray][Restore]
[COLOR=Black]Some other option that I cannot remember [Enabled]

I could not select Wireless LAN to change it to [Enabled]. It just skipped right to the next option.

Scott
[/COLOR]
[/COLOR]

looks like you've found the culprit

.

---

### Post by Windows Nerd on 2009-09-01
> **LewRockwell said:**
> looks like you've found the culprit

.

Mind telling me how to fix that then?

Scott

---

### Post by LewRockwell on 2009-09-01
> **Windows Nerd said:**
> Sorry, wasnt really clear on which bit you wanted to see, so I posted back the whole thing:

```
scott@scott-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d4100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d4200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0
    Memory at d4180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2000000-d3ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d4444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4000000-d40fffff
    Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2302
    I/O ports at 18d0 [size=8]
    I/O ports at 18c4 [size=4]
    I/O ports at 18c8 [size=8]
    I/O ports at 18c0 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at d4444400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Gateway 2000 Device 0366
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, fast devsel, latency 0, IRQ 2301
    Memory at d2000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at d4006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: 88000000-8bfff000 (prefetchable)
    Memory window 1: 8c000000-8ffff000
    I/O window 0: 00003000-000030ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at d4005000 (32-bit, non-prefetchable) [size=2K]
    Memory at d4000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Gateway 2000 Device 0366
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d4004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

scott@scott-laptop:~$
```

we might have missed it, but we do not see your wireless card listed

that it is missing from your configuration is also supported by your post relating to what you found in the BIOS area

unless you can find some additional BIOS configuration setting(s) which would engage your wifi card(or some other hardware/keystroke-combination switch that turns the card on and off(some folks have their laptops for years without ever knowing about the "switch" which might just be "Function F8" or something similar) then you may either have a card that has went bad or might need to be reseated/reconnected/etc

.

---

### Post by Windows Nerd on 2009-09-01
> **LewRockwell said:**
> we might have missed it, but we do not see your wireless card listed

that it is missing from your configuration is also supported by your post relating to what you found in the BIOS area

unless you can find some additional BIOS configuration setting(s) which would engage your wifi card(or some other hardware/keystroke-combination switch that turns the card on and off(some folks have their laptops for years without ever knowing about the "switch" which might just be "Function F8" or something similar) then you may either have a card that has went bad or might need to be reseated/reconnected/etc

.
My laptop does have a key-combo to turn wireless on or off (function+F2), though this is set to ON at all times. I will try fooling around with this key combo at boot within BIOS. I think that the card itself is fine...it works within Windows, though not in Linux. Maybe my card is not naively supported in Jaunty? I will try browsing within Windows to find an see what my Wireless card info is too.

Scott

Edit: Okay, so within Windows through device manager, I found this:
Motorola SM56 Speakerphone Modem
MAC Bridge Miniport
Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller
Realtek RTL8187 Wireless 802.11b/g 54Mbps USB 2.0 Network Adaptor #2

---

### Post by oboedad55 on 2009-09-01
> **Windows Nerd said:**
> My laptop does have a key-combo to turn wireless on or off (function+F2), though this is set to ON at all times. I will try fooling around with this key combo at boot within BIOS. I think that the card itself is fine...it works within Windows, though not in Linux. Maybe my card is not naively supported in Jaunty? I will try browsing within Windows to find an see what my Wireless card info is too.

Scott

Edit: Okay, so within Windows through device manager, I found this:
Motorola SM56 Speakerphone Modem
MAC Bridge Miniport
Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller
Realtek RTL8187 Wireless 802.11b/g 54Mbps USB 2.0 Network Adaptor #2

Do you know which card you have?

---

### Post by LewRockwell on 2009-09-01
> **oboedad55 said:**
> Do you know which card you have?

ummm.....

you even quoted it right above your question?> Realtek RTL8187 Wireless 802.11b/g 54Mbps USB 2.0 Network Adaptor #2

.

---

### Post by LewRockwell on 2009-09-01
[http://ubuntuforums.org/search.php?searchid=63655155](http://ubuntuforums.org/search.php?searchid=63655155)

.

---

### Post by oboedad55 on 2009-09-01
> **LewRockwell said:**
> ummm.....

you even quoted it right above your question?

.

LOL! sorry, my bad...

---

### Post by Windows Nerd on 2009-09-01
Apparently the drivers for my card are included automatically with kernels 2.6.25 and later. I will check my kernel version. 

Scott

---

### Post by Windows Nerd on 2009-09-01
Nope, I have the newest kernel 2.6.xx.28

---

### Post by zer010 on 2009-09-01
> **oboedad55 said:**
>  I know it's a tendency to want to un-install, reinstall, when things don't work. That's a windows holdover, and it does sometimes work.

--Jon

Thats been me a couple of times! :) "Windows holdover", love that one!  I'm learnin', thanks to all the great people in the 'buntu community!

---

### Post by anewguy on 2009-09-02
Don't know if you got this working or not.  If possible, here is what I would try:

- either hardwire connect to your router, or find a friend who has a router you can hardwire to.  This will at least allow you to connect to the net for the next steps.

- check the madwifi drivers.  I have seen many other posts about your chipset that people had better luck using the madwifi drivers.

- since you have Windows, you could copy the corresponding .inf and .sys files for your wireless and then try using ndiswrapper or ndisgtk (both are on the LiveCD if you look in pool main and find the n set or folder.

- you may also want to post back a "lsusb -v dxxxx:yyyy" where xxxx is the manufacturer and yyyy is the product id - both can be found on a straight lsusb.

- are there any drivers list under restricted drivers?


Dave :)

---

### Post by Windows Nerd on 2009-09-02
> **anewguy said:**
> Don't know if you got this working or not.  If possible, here is what I would try:

- check the madwifi drivers.  I have seen many other posts about your chipset that people had better luck using the madwifi drivers.

- since you have Windows, you could copy the corresponding .inf and .sys files for your wireless and then try using ndiswrapper or ndisgtk (both are on the LiveCD if you look in pool main and find the n set or folder.

- you may also want to post back a "lsusb -v dxxxx:yyyy" where xxxx is the manufacturer and yyyy is the product id - both can be found on a straight lsusb.

- are there any drivers list under restricted drivers?


Dave :)

By the way guys, I got Wicd back up and working. That means I have a graphical user interface back up and working.


Okay, I don't know if it's because I just woke up, but I don't know how to do any of that. As far as madwifi drivers go, I believe wicd has an option to select them under preferences, though I don't know if it just uses the driver and you have to install the driver seperately or it installs the driver as well as uses it.

As far as ndiswrapper goes, I know it is a utility that uses the Windows driver for my computer on linux. You said you can find it on the Live CD, though I do not know how to install software from the Live CD. As well I do not know how to find the windows driver, as all of them came prinstalled on my computer, and I do not know what filename to look for.

I will post the feedback from lsusb from terminal to here, as well as lsusb -v.

And what do you mean, "restricted drivers"? I'm confused, isnt Linux all open source?  

Scott

---

### Post by NightwishFan on 2009-09-02
The Linux kernel is open source and the majority of software. Some software is proprietary such as Skype, Opera, and some Drivers. Similar to how there is Open Source on Windows.

---

### Post by Windows Nerd on 2009-09-02
> **NightwishFan said:**
> The Linux kernel is open source and the majority of software. Some software is proprietary such as Skype, Opera, and some Drivers. Similar to how there is Open Source on Windows.
I know, but "restricted drivers" just didn't sound open source. I am still confused what he means by restricted drivers. How do I get them?

Scott

---

### Post by NightwishFan on 2009-09-02
Restricted drivers are installable in Ubuntu but they are not distributable or supportable, as they are maintained by their own developers. I believe they are free as in cost but not as in freedom. You can use the "Restricted Drivers Manager" to use them. (In GNOME: System -> Administration)

---

### Post by Windows Nerd on 2009-09-02
> **NightwishFan said:**
> Restricted drivers are installable in Ubuntu but they are not distributable or supportable, as they are maintained by their own developers. I believe they are free as in cost but not as in freedom. You can use the "Restricted Drivers Manager" to use them. (In GNOME: System -> Administration)

Thanks. I will try that. I have to help a friend with a job in 10 minutes, so I won have a chance until later.

Scott

---

### Post by Windows Nerd on 2009-09-02
Okay I don't see anything about restricted drivers under administration, all I see that could install anything is synaptic. 

Edit: there is something called hardware drivers and it recommends a driver that I need to be able to use my modem. The only thing is is that I cannot get internet to download this. Even a hardwired connection to my router will not work.

On another note, when I run lspci in terminal it does not reconize any sort of network controller, so this may be the problem. It reconizes my Ethernet controller though.

Scott

---

### Post by Windows Nerd on 2009-09-02
Bump. Any ideas? 

Also could somebody provide me with a helpful way to use the madwifi drivers? As well as an easy to understand instructions? I am using wicd to connect. 

If the madwifi thing does not work, I will try the Ndiswrapper thing, though some people have advised as only using Ndiswrapper as a last resort.

Scott

---

### Post by lkraemer on 2009-09-02
Scott,
Would your laptop be a Gateway?  If you boot into Windows does your Wifi
work correctly? (Assuming you have dual boot Windows with Ubuntu.)
If you enable your Wifi, and leave it enabled in Windows (and don't turn
it off by keystrokes or via a switch) you should be able to make it 
work in Ubuntu.  NOTE: Your LED might not reflect the proper state, just
don't disable the Wifi....forget about the LED.

I'd like to see the results of each of these commands.
```

lspci
lsusb
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use:
                                  cat /etc/modprobe.d/blacklist.conf

iwconfig

```

Your Wifi appears to be wlan0.  Maybe you can try the following:
You should know your essid and a previous command showed wlan0.

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Then post the output of iwconfig.

Have you tried the LiveCD of Ubuntu 9.10 Alpha 4?  You should be able to download it and pop in the LiveCD
and see if your Wifi works from the LiveCD.

Maybe this might give some help.
[http://ubuntuforums.org/showthread.php?t=503092&highlight=HOWTO%3A+Realtek+RTL8187](http://ubuntuforums.org/showthread.php?t=503092&highlight=HOWTO%3A+Realtek+RTL8187)
[http://ubuntuforums.org/showthread.php?t=792092&highlight=HOWTO%3A+Realtek+RTL8187](http://ubuntuforums.org/showthread.php?t=792092&highlight=HOWTO%3A+Realtek+RTL8187)
[http://ubuntuforums.org/showthread.php?t=571188&highlight=HOWTO%3A+Realtek+RTL8187](http://ubuntuforums.org/showthread.php?t=571188&highlight=HOWTO%3A+Realtek+RTL8187)

If you want to try ndiswrapper and the Windows Driver:
[http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

From the searching I did on the forum it appears that using the Windows Drivers with ndiswrapper
is the way to go for 9.04.

Good Luck.

lkraemer

---

### Post by Windows Nerd on 2009-09-02
> Scott,
Would your laptop be a Gateway?  If you boot into Windows does your Wifi
work correctly? (Assuming you have dual boot Windows with Ubuntu.)
If you enable your Wifi, and leave it enabled in Windows (and don't turn
it off by keystrokes or via a switch) you should be able to make it 
work in Ubuntu.  NOTE: Your LED might not reflect the proper state, just
don't disable the Wifi....forget about the LED.I have a gateway laptop. I can get Wifi perfectly fine in windows, and when I leave everything in the state it is (ie: loading a webpage successfully, then without touching ANYTHING, reboot into Linux) and then it will not work at all.

I will post the output of those commands in a minute.

I am in fact right now booted from my 9.04 LiveCD, and getting internet perfectly fine. 

Scott

Edit: Also, for clarification purposes:

> Your Wifi appears to be wlan0.  Maybe you can try the following:
You should know your essid and a previous command showed wlan0.

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
     
     ```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig 
```Then post the output of iwconfig.So, from what you said, my <interface> is "wlan0". My router's essid is...the name of my network, right? So for me that would be "home1". Just to Clarify, and thank you for being helpful!

Scott

---

### Post by Windows Nerd on 2009-09-03
Bump, and couldnsomeone please clarify what I outlined in the above post?

Scott

---

### Post by Windows Nerd on 2009-09-03
> **lkraemer said:**
> 

I'd like to see the results of each of these commands.

```

lspci
lsusb
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use:
                                  cat /etc/modprobe.d/blacklist.conf

iwconfig

```Your Wifi appears to be wlan0.  Maybe you can try the following:
You should know your essid and a previous command showed wlan0.

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```Then post the output of iwconfig.

Here ya are:

```
scott@scott-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
scott@scott-laptop:~$ lsusb
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
scott@scott-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
i915                   67844  2 
drm                    96424  3 i915
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ipt_LOG                13700  4 
iptable_mangle         10880  0 
iptable_filter         10752  1 
iptable_nat            13700  0 
ip_tables              19600  3 iptable_mangle,iptable_filter,iptable_nat
nf_nat                 25876  1 iptable_nat
x_tables               23044  3 ipt_LOG,iptable_nat,ip_tables
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
pcmcia                 44748  0 
snd_mixer_oss          22656  1 snd_pcm_oss
rtl8187                53376  0 
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
iTCO_wdt               19108  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
iTCO_vendor_support    11652  1 iTCO_wdt
mac80211              217592  1 rtl8187
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
psmouse                61972  0 
tifm_7xx1              13824  0 
video                  25360  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
eeprom_93cx6           10240  1 rtl8187
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_core              15900  1 tifm_7xx1
pcspkr                 10496  0 
serio_raw              13444  0 
joydev                 18496  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
output                 11008  1 video
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               38288  2 rtl8187,mac80211
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
scott@scott-laptop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
scott@scott-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

scott@scott-laptop:~$ 
```

And

```
scott@scott-laptop:~$ sudo ifconfig wlan0 down
scott@scott-laptop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:de:d7:67
Sending on   LPF/wlan0/00:c0:a8:de:d7:67
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
sscott@scott-laptop:~$ sudo iwconfig wlan0 home1
iwconfig: unknown command "home1"
scott@scott-laptop:~$ sudo iwconfig wlan0 "home1"
iwconfig: unknown command "home1"
scott@scott-laptop:~$ sudo iwconfig wlan0 mode Managed
scott@scott-laptop:~$ sudo ifconfig wlan0 up
scott@scott-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:de:d7:67
Sending on   LPF/wlan0/00:c0:a8:de:d7:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

scott@scott-laptop:~$
```

Hope you can figure out my problem :)

Scott

---

### Post by nothingspecial on 2009-09-03
Some people have got this wireless card to work by updating the bios.

Some people also report it works if you boot into windows turn the wireless on then reboot into Ubuntu.

Other people have just gone b*****r this and bought a usb wifi card.

---

### Post by lkraemer on 2009-09-03
OK,
Your commands were incorrect:
sscott@scott-laptop:~$ sudo iwconfig wlan0 home1
iwconfig: unknown command "home1"
scott@scott-laptop:~$ sudo iwconfig wlan0 "home1"

Notice I posted the following:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
So copy and paste these into a text editor.  If you are sure the essid
is home1 then paste this into your text file.  (In fact if you are online
with 9.04, open a terminal window and type:
```

iwconfig

```
and make a note of the essid.)
Modifiy commands with new essid if not home1:
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "home1"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
iwconfig

```
Try it again but, cut and paste the commands into a terminal window.
Maybe you will be lucky and get it operational.
I looked over your postings and it seems to be in order, from my
past experiences.


If you can't get it working you can always use ndiswrapper and the Windows drivers.
Here is another link that might be of help:
[http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+Device+0781+HOWTO%3A](http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+Device+0781+HOWTO%3A)
Just be sure to blacklist the rtl8187 driver.

lkraemer

---

### Post by Windows Nerd on 2009-09-03
> **nothingspecial said:**
> Some people have got this wireless card to work by updating the bios.

Some people also report it works if you boot into windows turn the wireless on then reboot into Ubuntu.

Other people have just gone b*****r this and bought a usb wifi card.

So...as far as updating the bios goes... I have no idea.

Hmm...going to onput that lAs set of commands again too.

Scott

---

### Post by Windows Nerd on 2009-09-03
Okay, so I just did a clean reinstall of Ubuntu (again) and I can get internet perfectly fine at full speed. Since I did not reformat the partition, it even remembered the password I entered in a while ago. This indicates that Ubuntu is perfectly fine with my chipset, and it is a problem elsewhere. I have not upsated or installed anything yet, so lets see if after update manager installs all the important security updates the internet still works.

Scott

---

### Post by Windows Nerd on 2009-09-03
The internet still works after the update. So now I will see if it was a program I installed that messed my wireless up.

Scott

---

### Post by zkriesse on 2009-09-04
Don't see what program that you might have installed that could have messed up your wireless but I'm not saying it isn't possible.

---

### Post by mejohnsn on 2009-09-04
> **Windows Nerd said:**
> The internet still works after the update.

That is good news. If it is still working even after a couple days of use, then that is even better news. What is more, it would then be grounds for marking this thread 'solved'.

Please do so if you still have no more network problems after a couple days of regular use, and if reinstalling programs doesn't make it come back. Otherwise, please feel free to keep us informed on the state of the problem.

---

### Post by Windows Nerd on 2009-09-04
Okay, after a couple of days it still works. This is good.

The only thing I noticed is:

The LED that indicates whether I have enabled or switched the card on is no longer lit up. I still get internet, but I cannot in my windows partition without turning this switch back on. It was set this way after the reinstall, so this problem originally had to do with my hardware...

I'm scared I will turn my card back onto its other "on" state by accident, stuffing my wireless. I will just have to be careful to not do this by accident on my Windows partition. 

Otherwise, I have every single program I need to do just about everything. I am just setting up my IDE for Java. It came downloaded as a .sh. Those are a pain in the ***.

Scott

---

### Post by nothingspecial on 2009-09-05
I still think the  2.6.28-14 kernel broke it and the  2.6.28-15.49 fixed it. You should be fine now.

---

