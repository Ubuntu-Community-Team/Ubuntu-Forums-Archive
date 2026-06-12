---
title: "Need help in Getting Atheros AR5006X WLAN Working in Ubuntu 8.04.01 64-bit"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by lightninglord2000 on 2008-08-27
I need help in getting my Compaq F756NR laptop with **Atheros** Wi-Fi chipset working in **Ubuntu 8.04.1 64-bit** (Hardy Heron). I can't seem to make the WLAN working.

In Windows XP Pro SP3, the ***Device Manager*** lists the WLAN as **Atheros AR5006X Wireless Network Adapter**. Also, I'm currently using in Windows XP Pro SP3 the **[Atheros v7.6.0.239 for Windows 9x, 2000 and XP]("http://www.laptopvideo2go.com/forum/index.php?showtopic=14858")**

I have also installed all of the updates listed in the **Update Manager** as of this posting

Here's some screen outputs that might be useful in finding a solution with my problem:

[IMG]http://www.imageflux.net/uploads/408821ubuntu_hardware_drivers.jpg[/IMG]

[IMG]http://www.imageflux.net/uploads/953837ubuntu_network_settings.jpg[/IMG]

```
**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1b:24:dc:e2:af  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fedc:e2af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6765 (6.6 KB)  TX bytes:18519 (18.0 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7000 (6.8 KB)  TX bytes:7000 (6.8 KB)
```

```
**lspci -v**

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:30ea
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: f6100000-f61fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 509
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 508
	Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
	Memory at f6489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f6000000-f60fffff
	Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f6280000 [disabled] [size=128K]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f6100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f6100400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f6100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30ea
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

---

### Post by sephiroth2212 on 2008-08-27
I believe for the 64bit OS you need to use Ndiswrapper.
Otherwise try this:
[http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x)

---

### Post by lightninglord2000 on 2008-08-27
**@sephiroth2212:** The instructions in your link are for **32bit Hardy Only**

---

### Post by Awfulwaffle on 2008-12-16
> **sephiroth2212 said:**
> I believe for the 64bit OS you need to use Ndiswrapper.
Otherwise try this:
[http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=795984&highlight=AR242x)

Hey, having the same problem as this. It's my first day (technically a day and a half) using linux, although I did a bit of research first so I'm familiar with a few of the basic terminal commands. I'm using a Compaq F750US with an Atheros ar5006x wifi card and Intrepid Ibex dual booting with WinXP. The wifi is the only thing that is not working. The computer is an AMD64. The weird thing is, I didn't get prompted as to whether or not I wanted to install 32 or 64 bit during the install. Is it safe to assume that it went ahead and installed the 64 bit version?
If so, I'm having the same issue. I actually had 8.04 installed last night, but couldn't get wireless running. It gave me the same output as the OP, where ifconfig didn't even see the card. When I ran Hardware Testing, however, the card shows up as Atheros 802.11 wireless or something close to it. wlanconfig cannot find ath0 or wifi0 (that's what i think the device would register as, correct me if I'm wrong). I tried installing madwifi, which didn't work. I'm assuming this is because this is a 64 bit system, as I've seen quite a few posts in my search for a solution that said it worked on a 32 bit system. I then tried Ndiswrapper to use the WinXP driver for this card. When I loaded the .inf using ndiswrapper -l and opened ndisgtk it said that the hardware was present, or something along those lines, but I still couldn't find the adapter in ifconfig or wlanconfig. I don't know if it had anything to do with it, but the first time I tried to install the .inf ubuntu became entirely unresponsive and I had to reboot. After this point, it actually froze during load AND stopped dead when I ran recovery mode. It looks like it stopped reading from the drive, because all progress would instantly stop and then the drive spin light on the front of the laptop stopped blinking.

Now, we get to the 8.10 install. The reason I updated was because I had heard that 8.10 was updated with native drivers for the Atheros family of wifi cards. The drivers ARE there (I can actually get a wireless option in the network manager) but they still do not work. I still cannot see ath0 in ifconfig or wlanconfig, although the Hardware Testing program still shows it as one of my network connectors. I downloaded and installd WifiRadar in a last ditch attempt, but when I try to launch it I get the following error:
Failed to execute child process "su-to-root" (No such file or directory)

I honestly have no idea how to proceed (being a very inexperience linux user). This forum helped me get the rest of my hardware working properly, which is awesome, so I was hoping one of y'all would know what I need to do.

Please help, as this is the only thing keeping me from choosing Ubuntu over WinXP.

Thanks a lot in advance, and sorry for the noobishness

Alex

---

### Post by growler on 2008-12-16
Awfulwaffle

Try the release notes.

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Atheros ath5k wireless driver not enabled by default

growler

---

### Post by Awfulwaffle on 2008-12-16
Thanks for the idea growler. I checked it out, downloaded the proper package and everything else that was suggested in the release notes, and still nothing. I DID manage to find a definite fix though, after I found several tutorials and other google search hits that didn't work and decided to take parts of em that made sense and combine em. Here's the procedure I used that ended up finally making my WLAN work:

Disabled the limited drivers in System>Administration>Hardware Drivers and rebooted.

su

mkdir /etc/lib

mkdir /etc/lib/wireless

cd /etc/lib/wireless

apt-get install build-essential

wget [http://sourceforge.net/project/downloading.php?groupname=madwifi&filename=madwifi-0.9.4.tar.gz&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=madwifi&filename=madwifi-0.9.4.tar.gz&use_mirror=internap)

tar -xf madwifi-hal-0.10.5.6-r3879-20081204.tar.gz

cd madwifi-hal-0.10.5.6-r3879-20081204

make

make install

modprobe ath_pci



I immediately got both a wireless lan option in my connections manager and my AR5006x showed up in ifconfig and wlanconfig. I tested it on my persistent flash drive install of 8.04 after I got it running in 8.10, and it worked in both.

---

