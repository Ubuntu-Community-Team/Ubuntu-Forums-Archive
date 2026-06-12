---
title: "wireless broken after update: Ubuntu 12.04.3 LTS on acer aspire one 725-0488"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by wXPnHse on 2013-10-13
Hello, pretty new to Ubuntu. I'm having trouble getting my wireless internet to work after a software update last night (Oct. 12). Unfortunately, I'm traveling for a long time and don't have access to a wired internet connection for the moment.

What happens is after entering the network's password, it will sometimes say "connection established" but no signal bars will appear nor will Firefox or Chrome be able to load anything. Then it'll drop the connection and make several failed attempts to connect again. Occasionally, it will successfully reconnect and a couple of bars appear, but Firefox or Chrome still fail to load anything. Everything was working fine up until I updated last night. Computers running Windows on the same network work without issue.

After the classic turn it off/on troubleshooting failed, I've tried the advice posted in the following threads:
[http://ubuntuforums.org/showthread.php?t=2180335](http://ubuntuforums.org/showthread.php?t=2180335)
[http://askubuntu.com/questions/128269/wireless-connection-drops-every-30-seconds-on-an-asus-eee-pc-with-an-atheros-car](http://askubuntu.com/questions/128269/wireless-connection-drops-every-30-seconds-on-an-asus-eee-pc-with-an-atheros-car)
[http://www.linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://www.linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

And here is some information as requested on other similar threads:
```
**s****udo  lshw -Cnetwork**
 
 *-network               
       description:Ethernet interface
       product:RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: RealtekSemiconductor Co., Ltd.
       physical id: 0
       bus info:pci@0000:01:00.0
       logical name:eth0
       version: 05
       serial:04:7d:7b:c4:02:ef
       size: 10Mbit/s
       capacity:100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt10bt-fd 100bt 100bt-fd autonegotiation
       configuration:autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPIduplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yesport=MII speed=10Mbit/s
       resources:irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description:Wireless interface
       product: AR9485Wireless Network Adapter
       vendor: QualcommAtheros
       physical id: 0
       bus info:pci@0000:02:00.0
       logical name:wlan0
       version: 01
       serial:e0:06:e6:23:6a:73
       width: 64 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration:broadcast=yes driver=ath9k driverversion=3.9.0-030900rc8-generic firmware=N/Aip=192.168.1.101 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources:irq:17 memory:f0100000-f017ffff memory:f0300000-f030ffff
 
 
**lspci -v**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 14h Processor Root Complex
            Subsystem:Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
            Flags: busmaster, 66MHz, medium devsel, latency 32
 
00:01.0 VGA compatible controller: Advanced Micro Devices,Inc. [AMD/ATI] Wrestler [Radeon HD 6290] (prog-if 00 [VGA controller])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, fast devsel, latency 0, IRQ 44
            Memory ate0000000 (32-bit, prefetchable) [size=256M]
            I/O ports at3000 [size=256]
            Memory atf0200000 (32-bit, non-prefetchable) [size=256K]
            ExpansionROM at <unassigned> [disabled]
            Capabilities:<access denied>
            Kerneldriver in use: radeon
            Kernelmodules: radeon
 
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI]Wrestler HDMI Audio
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, fast devsel, latency 0, IRQ 46
            Memory atf0244000 (32-bit, non-prefetchable) [size=16K]
            Capabilities:<access denied>
            Kerneldriver in use: snd_hda_intel
            Kernelmodules: snd-hda-intel
 
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family14h Processor Root Port (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0
            Bus:primary=00, secondary=01, subordinate=01, sec-latency=0
            I/O behindbridge: 00002000-00002fff
            Prefetchablememory behind bridge: 00000000f0000000-00000000f00fffff
            Capabilities:<access denied>
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family14h Processor Root Port (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0
            Bus:primary=00, secondary=02, subordinate=02, sec-latency=0
            Memorybehind bridge: f0100000-f01fffff
            Prefetchablememory behind bridge: 00000000f0300000-00000000f03fffff
            Capabilities:<access denied>
            Kerneldriver in use: pcieport
            Kernelmodules: shpchp
 
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, fast devsel, latency 0, IRQ 18
            Memory atf0248000 (64-bit, non-prefetchable) [size=8K]
            Capabilities:<access denied>
            Kerneldriver in use: xhci_hcd
 
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD]FCH SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 64, IRQ 45
            I/O ports at3118 [size=8]
            I/O ports at3124 [size=4]
            I/O ports at3110 [size=8]
            I/O ports at3120 [size=4]
            I/O ports at3100 [size=16]
            Memory atf024f000 (32-bit, non-prefetchable) [size=2K]
            Capabilities:<access denied>
            Kerneldriver in use: ahci
            Kernelmodules: ahci
 
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atf024e000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci_hcd
 
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 17
            Memory atf024d000 (32-bit, non-prefetchable) [size=256]
            Capabilities:<access denied>
            Kerneldriver in use: ehci-pci
 
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atf024c000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci_hcd
 
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 17
            Memory atf024b000 (32-bit, non-prefetchable) [size=256]
            Capabilities:<access denied>
            Kerneldriver in use: ehci-pci
 
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBusController (rev 14)
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags:66MHz, medium devsel
            Kernelmodules: i2c-piix4
 
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCHAzalia Controller (rev 01)
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, slow devsel, latency 32, IRQ 47
            Memory atf0240000 (64-bit, non-prefetchable) [size=16K]
            Capabilities:<access denied>
            Kerneldriver in use: snd_hda_intel
            Kernelmodules: snd-hda-intel
 
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCHLPC Bridge (rev 11)
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 0
 
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCHPCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
            Flags: busmaster, 66MHz, medium devsel, latency 64
            Bus:primary=00, secondary=03, subordinate=03, sec-latency=64
 
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, 66MHz, medium devsel, latency 32, IRQ 18
            Memory atf024a000 (32-bit, non-prefetchable) [size=4K]
            Kerneldriver in use: ohci_hcd
 
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 0 (rev 43)
            Flags: fastdevsel
 
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 1
            Flags: fastdevsel
 
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 2
            Flags: fastdevsel
 
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 3
            Flags: fastdevsel
            Capabilities:<access denied>
            Kerneldriver in use: k10temp
            Kernelmodules: k10temp
 
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 4
            Flags: fastdevsel
 
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 6
            Flags: fastdevsel
 
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 5
            Flags: fastdevsel
 
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD]Family 12h/14h Processor Function 7
            Flags: fastdevsel
 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
            Subsystem:Acer Incorporated [ALI] Device 0740
            Flags: busmaster, fast devsel, latency 0, IRQ 43
            I/O ports at2000 [size=256]
            Memory atf0004000 (64-bit, prefetchable) [size=4K]
            Memory atf0000000 (64-bit, prefetchable) [size=16K]
            Capabilities:<access denied>
            Kerneldriver in use: r8169
            Kernelmodules: r8169
 
02:00.0 Network controller: Qualcomm Atheros AR9485 WirelessNetwork Adapter (rev 01)
            Subsystem:Foxconn International, Inc. Device e047
            Flags: busmaster, fast devsel, latency 0, IRQ 17
            Memory atf0100000 (64-bit, non-prefetchable) [size=512K]
            ExpansionROM at f0300000 [disabled] [size=64K]
            Capabilities:<access denied>
            Kerneldriver in use: ath9k
            Kernelmodules: ath9k
 
**uname -mr**

3.9.0-030900rc8-generic i686
```

Any advice? Or is there a way to "undo" updates? Please let me know if I'm missing any info here.

---

### Post by Bucky Ball on 2013-10-13
Welcome. Also the output of:

```
iwconfig
```

Thanks. The card has a driver installed and appears to be fine, but this has me a bit bemused:

```
driverversion=_3.9.0-030900rc8-generic_ firmware=N/Aip=192.168.1.101
```

Are you running a custom/newer kernel than the default 12.04 LTS kernel? Have you installed one manually or you have a third-party PPA for the kernel installed? Maybe this is a result of one of the things you tried from the links you supplied, but this doesn't add up:

```
3.9.0-030900rc8-generic
```

12.04 does not use that kernel by default. You should be seeing something like this:

```
3.2.0-53-generic
```

Might not be your issue, but might not be helping.

---

### Post by wXPnHse on 2013-10-13
Thanks for the fast reply. Here is the output of *iwconfig*:

> wlan0     IEEE802.11bgn  ESSID:off/any 
         Mode:Managed  Access Point:Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7  RTS thr:off   Fragment thr:off
          PowerManagement:on
          
lo        no wirelessextensions.
 

eth0      no wirelessextensions.

Yes, I should have mentioned that I replaced (downgraded? unsure of the proper word here) the kernel because of an unrelated issue I was having with brightness settings (seems to be a common problem with the Acer Aspire One and Ubuntu 12.04... the brightness was stuck on the highest setting). Though I did this several months ago and it didn't seem to affect my wireless connectivity at all until last night's update. Maybe something is interacting here that's causing the problem?

---

### Post by Bucky Ball on 2013-10-13
Could be. Could you right click on the network icon and 'Edit Connections'. Try setting that up to the exact details required. The result of 'iwconfig' is showing 'not associated'. When you left click the network icon do you see a list of available networks or nothing? If something, can you see yours and what exactly happens when you try and connect (if you can see it)?

---

### Post by wXPnHse on 2013-10-13
Apologies but I'm having some trouble understanding what you mean by "setting that up to the exact details required." Do you mean simply adding the network name and password to the list?

Right and left clicking appear to bring up the same menu, which includes both a list of connections (which I can see in full) and the Edit Connections menu. Attempting to connect to my network results in a couple of different things:
1. A notification appears that says "disconnected from network" or something to that effect. Will then attempt to reconnect automatically.
2. I'm prompted to enter the encryption key again.
3. This is the most confusing. A notification appears that says "connection established", but my signal indicator icon is empty (occasionally it will display 1 or 2 bars, once it actually displayed all 5). Browsers are unable to display anything, and reopening the list of connections indicates that I'm not actually connected. After a few minutes, it will disconnect and attempt to reconnect automatically.

---

### Post by Bucky Ball on 2013-10-13
Ok. Try all this with your Network Manager GUI open at the 'Wireless' tab.  That should tell you what's connected to what and when. Just wondering if it might be getting confused as to which network to connect to. Also, when it says it is connected, run the 'iwconfig' again and see what it is associated with, if anything.

I mean: set up the wireless connection manually in the Network Manager>Wireless tab rather than letting it connect automatically. Might stop any confusion, might not. 

Edit Network>Wireless>Click your network or add it if it doesn't already exist (if it doesn't already exist then we could be on the right track). 
Fill in its details; ESSID (name of network) under the Wireless tab, security type and details, etc. under the wireless security tab, the correct IPv4 details under there, and set IPv6 to 'ignore' if you're not using it (automatic should also work but just to be sure).

You'll need to find these details out if you don't know them.

When done, make sure 'Available to all users' is ticked at the bottom and 'Connect Automatically' is ticked at the top. This might prevent it connecting with any other available networks.

Reboot and see if it connects (associates) automatically with *your* network.

---

### Post by wildmanne39 on 2013-10-13
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
does it connect now?
Thanks

---

### Post by wXPnHse on 2013-10-13
Bucky Ball: Manually setting the details as you described didn't seem to do anything. I think it's possible to rule out confusion as to what network to connect to: it only ever tries to automatically connect to ones that it has connected to in the past. It continues to do exactly as it's been doing for the last couple of days. Those few moments when it does connect doesn't give me quite enough time to run *iwconfig* but I'll keep seeing if I can catch it.

Wild Man:
> [COLOR=#000000][FONT=Ubuntu Mono]echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf[/FONT][/COLOR]
resulted in: 
> tee: /modprobe.d/ath9k.conf: No such file or directory
options ath9k nowhcrypt=1

Perhaps I'm missing a file that I need here?

---

### Post by wildmanne39 on 2013-10-14
Please do it this way then:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Add one line:

```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by wXPnHse on 2013-10-14
Still no good. Everything is exactly the same as before.

---

### Post by wildmanne39 on 2013-10-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wXPnHse on 2013-10-14
Here's the file you'd requested.

---

### Post by wildmanne39 on 2013-10-14
There is a bug in the kernel 3.9 and there is no fix for it yet, I recommend dropping back to the 3.8 kernel.
Also the signal strength of the AP'S you are trying to connect to are to weak to connect to them, that might be a side effect of the bug also though.
Thanks

---

