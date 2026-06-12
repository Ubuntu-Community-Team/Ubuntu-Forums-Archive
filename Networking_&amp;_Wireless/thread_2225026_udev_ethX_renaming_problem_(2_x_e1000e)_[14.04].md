---
title: "udev ethX renaming problem (2 x e1000e) [14.04]"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by the kaz on 2014-05-19
Hello all,
I'm trying to get a board with two Intel Gigabit network devices both supported by the e1000e driver in the correct order. To be exact, I need to configure the 14.04 server version I installed in such a way that a specific of those to devices is eth0 (the other one is not connected to anything and can therefore be any device, just not eth0).** I can't use mac addresses, however, because the finished installation will be cloned and run on a number of different mainboards (of the same model). **

This isn't the first time I have to accomplish something like this - in previous cases, I just disabled the net-generator (with "touch /etc/udev/rules.d/75-persistent-net-generator.rules") and then manually added a line like this

```
SUBSYSTEM=="net", DRIVERS=="8139too", ATTR{address}=="?*", NAME="eth0"
```

This time, it's a little more difficult, however, because I can't use "DRIVERS==" to select the network interface, as they're both using e1000e. 

Here is the disconnected device, which is named "eth0" by the kernel

```

        00:19.0 Ethernet controller: Intel Corporation 82567V-3 Gigabit Network Connection (rev 04)
        Subsystem: Intel Corporation Device 0000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 42
        Region 0: Memory at feac0000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at c400 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0100c  Data: 4142
        Kernel driver in use: e1000e

```

This is the second one, which is called "eth1" but needs to be "eth0":

```

03:00.0 Ethernet controller: Intel Corporation 82583V Gigabit Network Connection
        Subsystem: Intel Corporation Device 0000
        Physical Slot: 36
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 43
        Region 0: Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at ec00 [size=32]
        Region 3: Memory at febdc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0200c  Data: 4162
        Capabilities: [e0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <128ns, L1 <64us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [a0] MSI-X: Enable- Count=1 Masked-
                Vector table: BAR=3 offset=00000000
                PBA: BAR=3 offset=00002000
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Device Serial Number 00-0b-ab-ff-xx-xx-xx-xx-xx
        Kernel driver in use: e1000e

```

I've using "ATTR{device}==" (one is "0x1501", the other "0x150c"), with and without DRIVER, with SUBSYSTEM "pci" and "net" - my most recent try is this:

```

SUBSYSTEM=="net", KERNEL=="0000:00:1c.0", NAME="eth9"
SUBSYSTEM=="net", KERNEL=="0000:03:00.0", NAME="eth0"

```

but nothing seems to do anything. 0000:00:1c.0 always remains eth0, and 0000:03:00.0 remains eth1. 

What do I have to do in order to get the device names I need for the rest of the software on the system to run correctly? Can anyone give me any pointers?

Greetings, kaz

P.S: this is the output of udevadm for the two devices:


```
  looking at device '/devices/pci0000:00/0000:00:1c.0':
    KERNEL=="0000:00:1c.0"
    SUBSYSTEM=="pci"
    DRIVER=="pcieport"
    ATTR{irq}=="40"
    ATTR{subsystem_vendor}=="0x8086"
    ATTR{broken_parity_status}=="0"
    ATTR{class}=="0x060400"
    ATTR{enabled}=="1"
    ATTR{consistent_dma_mask_bits}=="32"
    ATTR{dma_mask_bits}=="32"
    ATTR{local_cpus}=="ff"
    ATTR{device}=="0x283f"
    ATTR{msi_bus}=="1"
    ATTR{local_cpulist}=="0-7"
    ATTR{vendor}=="0x8086"
    ATTR{subsystem_device}=="0x283f"
    ATTR{d3cold_allowed}=="0"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

```
  looking at device '/devices/pci0000:00/0000:00:1c.4/0000:03:00.0':
    KERNEL=="0000:03:00.0"
    SUBSYSTEM=="pci"
    DRIVER=="e1000e"
    ATTR{irq}=="43"
    ATTR{subsystem_vendor}=="0x8086"
    ATTR{broken_parity_status}=="0"
    ATTR{class}=="0x020000"
    ATTR{enabled}=="1"
    ATTR{consistent_dma_mask_bits}=="64"
    ATTR{dma_mask_bits}=="64"
    ATTR{local_cpus}=="ff"
    ATTR{device}=="0x150c"
    ATTR{msi_bus}==""
    ATTR{local_cpulist}=="0-7"
    ATTR{vendor}=="0x8086"
    ATTR{subsystem_device}=="0x0000"
    ATTR{d3cold_allowed}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.4':
    KERNELS=="0000:00:1c.4"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{irq}=="41"
    ATTRS{subsystem_vendor}=="0x8086"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x060400"
    ATTRS{enabled}=="1"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="ff"
    ATTRS{device}=="0x2847"
    ATTRS{msi_bus}=="1"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x2847"
    ATTRS{d3cold_allowed}=="0"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Hadaka on 2014-05-19
hi, try this simple excersize see what happens

remove the second eth card..the one now marked eth0
then do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
then BOOT
this should rename what was eth1...to....eth0
then of course replace the eth card...now going to be eth1..was...eth0 before removal
insert...power back up and cross your fingers....should work.

---

### Post by the kaz on 2014-05-19
> **Hadaka said:**
> remove the second eth card..the one now marked eth0
then do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
then BOOT
this should rename what was eth1...to....eth0
then of course replace the eth card...now going to be eth1..was...eth0 before removal
insert...power back up and cross your fingers....should work.

This won't work. First of all, as I said, I need a solution that works without any modification when I clone the drive and connect it to a different mainboard (of the same make and model). Ubuntu's auto-numbering uses the MAC addresses of the devices for its udev rules which fail when changing the board. So this might be a solution, but unfortunately not for my problem. 

Apart from that, I should have made clearer that both ethernet interfaces are on the mainboard itself, not on any NIC. 

Cheers, kaz.

---

### Post by the kaz on 2014-05-21
Is there really no one who knows how to write udev rules that work in this case? I'm really at a loss how to deal with the fact that udev rules that look perfectly okay (and are in fact copied straight from the udevadm output) do absolutely nothing. It's as if they weren't even there! 

Is there any way to debug this so that I can at least find out why those udev rules do nothing? The mainboard is useless for me unless I can get the device that's now called eth1 to be called eth0. 

Did I perhaps post in the wrong subforum? 

Greetings, kaz.

---

### Post by bab1 on 2014-05-21
> **the kaz said:**
> Is there really no one who knows how to write udev rules that work in this case? I'm really at a loss how to deal with the fact that udev rules that look perfectly okay (and are in fact copied straight from the udevadm output) do absolutely nothing. It's as if they weren't even there! 

Is there any way to debug this so that I can at least find out why those udev rules do nothing? The mainboard is useless for me unless I can get the device that's now called eth1 to be called eth0. 

Did I perhaps post in the wrong subforum? 

Greetings, michael.

Sometimes its just a matter of patience.

See here: [http://ubuntuforums.org/showthread.php?t=2219332]("http://ubuntuforums.org/showthread.php?t=2219332")

See the links that @Doug S provided in post#3.

---

### Post by the kaz on 2014-05-21
Thanks for the pointers. I'm still confused, however; the conversations suggests that 14.04 udev doesn't write anything to 70-persistent-net.rules anymore, but that exactly what happens here unless create an empty 75-persistent-net-generator.rules, as stated in all HowTos I found on the subject. Plus, one of the links mentioned ([http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/]("http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/")) explicitely states: 
>  If the user has added udev rules which change the name of the kernel devices these will take precedence too. 
which means my added udev rules should change the interface names. Yet they don't.

Actually, I don't see any evidence at all that this Predictable Network Interface Naming is really working on my system, as the two interfaces are just called eth0 and eth1, as they have been since the dawn of time (linux time, anyway 8-) ). No sign of enXX devices anywhere, not present after boot, not mentioned in the kernel log. Nothing. 

That means I'm still at a loss what to do now, as the links by all evidence aren't applicable to my 14.04 server LTS installation (which was release-upgraded from a 12.04 LTS version, in any case that is relevant, by the way). Why is that so, and why can't I rename the ethernet devices?

More confused now, kaz.

---

### Post by bab1 on 2014-05-21
It's really a biosdevname and udev problem.  Read the man pages on biosdevname.  A you can read a good overview of biosdevname [here]("http://www.arachnoid.com/linux/network_names/index.html") and [here]("http://fedoraproject.org/wiki/Features/ConsistentNetworkDeviceNaming").

In the future it may be that eth names will not be widely supported.  Ubuntu is still making init changes.  They will be using systemd instead of Upstart from what I hear in 14.40.

---

### Post by the kaz on 2014-05-21
I don't see network device names called emX, either. Plus, your link again suggest I can repair this by just adding udev rules, which I already mentioned don't do anything here, unless they are the ones the udev generator writes which include the mac addresses of the devices (which I can't). So, I again see no evidence whatsoever that 14.04 behaves at all like mentioned in those **Fedora** documents - plus, they offer no remedy for my problem. 

Cheers, kaz.

---

### Post by bab1 on 2014-05-21
> **the kaz said:**
> I don't see network device names called emX, either. Plus, your link again suggest I can repair this by just adding udev rules, which I already mentioned don't do anything here, unless they are the ones the udev generator writes which include the mac addresses of the devices (which I can't). So, I again see no evidence whatsoever that 14.04 behaves at all like mentioned in those **Fedora** documents - plus, they offer no remedy for my problem. 

Cheers, kaz.
I'm not into hand holding.  What the links point out is that you can remove the biosdevname and revert back to the previous (13.10) configuration.  But all of that is up to you.  Ubuntu 14.04 only 3 months from it's general release.  Most of the time in these cases you are on your own until there is more knowledge.  Your problems however, are helping us find those answers.  I'm most likely not moving my 12.04 servers over for at least another 6 months or so.

---

### Post by the kaz on 2014-05-21
> **bab1 said:**
> I'm not into hand holding. 
And I wouldn't want that. 

> **bab1 said:**
> What the links point out is that you can remove the biosdevname and revert back to the previous (13.10) configuration.
Yes, by adding udev rules **which I already did before I first posted here, to no effect. **

Furthermore, the sections stipulate that my ethernet devices under biosdevname should have certain names **which they have not**. 

My logical conclusion is that biosdevname is either inactive, not working properly or not present at all. Can I find any evidence to the contrary, and if so, where?

I don't want to be spoon-fed a solution, but all I'm getting so far a documents which state facts that are just plain wrong (at least in regard to my 14.04 installation), and don't offer any means of going forward, as they all suggest writing or rewriting udev rules, which I have already done. Doing the same things again expecting a different result is a definition of insanity (plus, I never deleted those non-working udev rules I metioned in post #1, so they are still there and still doing nothing). 

> **bab1 said:**
>   Ubuntu 14.04 only 3 months from it's general release.

I was under the impression that 14.04 was released roughly five weeks ago.  

To make this about solutions again: ***I couldn't find any way to test whether any of those naming schemes mentioned in these articles are actually present/at work in my 14.04 installation. Can anyone give me any pointers how to do so?** *

Any other **working** way to rename my eth1 to eth0 (which doesn't use the mac address or any other attribute which would change when using a different mainboard of the same make and model) would be fine, too. 

Cheers, kaz.

---

### Post by Marcus_Wellnitz on 2014-06-06
hallo kaz,

I had similar problems with ubuntu 14.04. 
My Configuration:
2x onboard (igb) NIC
1x 4-port (e1000e) NIC

After installation there were rules in [FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules[/FONT] for my onbord NICs only. Each reboot the e1000e kernel module did a random renaming (p1p1, p1p2, renamed4, p1p4) or similar. 
Even rules (copied from onboard NICs) for the e1000e at [FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules[/FONT]  were ignored.
It seems that the e1000e driver could not handle ATTR{address}=="00:30:48:b4:33:df" .
Digging arount for 2 Days I found a solution:
```

## show udev informations for specific NIC
udevadm info --query=all -a --path='/sys/class/net/eth2'

[...]
looking at parent device [...]
KERNELS=="0000:04:00.0"
[...]

# PCI device 0000:04:00.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:04:00.0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="?*", NAME="eth3"

```

* Get Informations for your specific device via /sys/class/net/
* let udevadm taverse down to get the device specific PCI-ID (It's unique for each NIC)
* set udev rules to the device-id instead of MAC-Address.

For me it works like a charm. 
This solution is very cool if you have a server farm with lots of similar Hardware. Each server can have the same udev-rules because NICs in the same (Hardware) slot will have the same ethX device.

I don't know which component is buggy. I think it's the e1000e kernelmodule, the udev rules script or a kernel timing problem.

Some good informations will begiven by a blog post of Murat Demirten
[http://linux-tips.org/article/73/persistent-device-naming-with-udev](http://linux-tips.org/article/73/persistent-device-naming-with-udev)

---

