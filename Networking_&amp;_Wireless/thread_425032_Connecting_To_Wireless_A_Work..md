---
title: "Connecting To Wireless A Work."
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Minker17 on 2007-04-27
I just installed Fesity on my Vaio V505BXP and can get on the internet as long as I'm plugged in through eth0. I'm trying to connect to the wireless at work, but I'm having some issues.

The Facts:
1) My wireless connection is showing up as wlan0
2) The connection is encrypted and not broadcast
3) How do I set it up for WPA-PSK-TKIP?
4) I was connected for a split second, but then lost it
5) Should I use the Ubuntu networking conifger or download a different one?

Any help would be appreciated.

---

### Post by dbott67 on 2007-04-27
I would download [NetworkManager]("http://www.gnome.org/projects/NetworkManager/"):
```
sudo apt-get install network-manager-gnome
```It handles WPA without problems.

As for your questions:

1. wlan0 is quite typical, although depending on chipset it may be ethX, or athX.
2. NetworkManager can handle this.  You'll have to 'Connect to Other Wireless Network' and enter the appropriate ESSID & key.
3. NetworkManager
4. Not sure about this one.
5. NetworkManager

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

-Dave

---

### Post by Minker17 on 2007-04-27
I ran that in the terminal and everything went fine.

Question, where did it go to? Forgive me, I'm still learning.

---

### Post by dbott67 on 2007-04-27
No problem.  If you restart the 'gnome-panel', the icon *should* appear by the clock:
```
killall gnome-panel
```

The above command will cause the panels at the top & bottom of your session to disappear & re-appear.  When they re-appear, you should see the escalating bars or a computer icon that you can click on.  When you click on it, the menu pictured above should appear.

You could also just logout & login to achieve the same result.

-Dave

---

### Post by Minker17 on 2007-04-27
And if it didn't?

---

### Post by Minker17 on 2007-04-27
It says 0 upgraded, 0 installed, 0 etc.

DOes that mean it dind't work?

---

### Post by dbott67 on 2007-04-27
> **Minker17 said:**
> It says 0 upgraded, 0 installed, 0 etc.

DOes that mean it dind't work?

This means that it's already installed, which is good.  You can check the status of the process (nm-applet) by issuing the following command:

```
dbott@feisty:~$ **ps aux | grep nm-applet**
dbott     5451  0.0  0.0   2884   752 pts/2    R+   09:52   0:00 grep nm-applet
[COLOR=Red]dbott     5648  0.0  1.4  53024 13532 ?        S    Apr25   0:01 [COLOR=Blue]nm-applet[/COLOR] --sm-disable[/COLOR]

```

[I]Note: this is running on my desktop PC, which does NOT have wireless.  But you should see a process called [COLOR=Blue]nm-applet[/COLOR] running (as well as the grep search).

[/I]Here's a screenshot of my home PC that I just remoted to using NX Machine.  Notice the computer icon in the top right-hand corner.  You should have something like this that you can click on to configure the wireless network.

I've got a meeting to go to now, but I'll check back in a few hours.

-Dave

---

### Post by Minker17 on 2007-04-27
Ok, it is there. When I click on manual, I can adjust the settings of the wireless, however, how do I set it up for WPA and put in the password for the wireless and everything? I can adjust the configuration to static, dhcp, and localzero. I have the options for general, dns, and hosts.

Thank you very much for all your help so far. You have been very helpful!

---

### Post by dbott67 on 2007-04-27
I'll have to give it a try on my laptop at home tonight.

First, you'll probably have to disconnect your wired network (just unplug the cable).

Also, make sure that the wireless card is enabled:
```
sudo ifup wlan0
```
Then try scanning for wireless:
```
iwlist scanning
```

If you see any APs listed, then the wifi card is active.

You can also post the output of the following (with the wired network disconnected):
```
dbott@feisty:~$ [COLOR=Red]**nm-tool**[/COLOR]

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            8139too
  Active:            yes
  HW Address:        00:50:BA:C0:A7:55

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings
    Hardware Link:   yes

  IP Settings:
    IP Address:      192.168.1.106
    Subnet Mask:     255.255.255.0
    Broadcast:       192.168.1.255
    Gateway:         192.168.1.1
    Primary DNS:     192.168.1.1
    Secondary DNS:   0.0.0.0

```

As for the NetworkManager application, under normal circumstances, you would see all broadcasted APs listed that are in range.  Seeing as you're not broadcasting ESSID, I'm not sure if you need to use the "Connect to other wireless network" option or perhaps "Create a New Wireless Network".

-Dave

---

### Post by Minker17 on 2007-04-27
No such device. It just occured to me that I might not have it enabled or that Linux might not support my card? Vaio PCG-V505BXP.

How would I enable it or set up drivers for this? (if applicable)

---

### Post by Minker17 on 2007-04-27
Looks like I'm using LAN-Express 802.11 Wireless LAN Adapter (per Vaio site)

---

### Post by dbott67 on 2007-04-27
Can you post the output of the following commands:
```
dbott@edgy:~$ [COLOR=Red]sudo lshw -C network[/COLOR]
Password:
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: [COLOR=Red]Broadcom Corporation[/COLOR]
       physical id: 0
       bus info: pci@0b:00.0
       logical name: [COLOR=Red]wlan0[/COLOR]
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

``````
dbott@edgy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR=Red] 0b:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)[/COLOR]

```and 
```
dbott@edgy:~$ lspci -n
00:00.0 0600: 8086:27a0 (rev 03)
00:01.0 0604: 8086:27a1 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:2448 (rev e1)
00:1f.0 0601: 8086:27b9 (rev 01)
00:1f.2 0101: 8086:27c4 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 1002:7145
03:00.0 0200: 14e4:170c (rev 02)
03:01.0 0c00: 1180:0832
03:01.1 0805: 1180:0822 (rev 19)
03:01.2 0880: 1180:0843 (rev 01)
03:01.3 0880: 1180:0592 (rev 0a)
03:01.4 0880: 1180:0852 (rev 05)
[COLOR=Red] 0b:00.0 0280: 14e4:4311 (rev 01)[/COLOR]

```This will help determine the NIC and chipset.

-Dave

---

### Post by Minker17 on 2007-04-27
[quote= ]rmueller@rmueller-laptop:~$ sudo lshw -c network
Password:
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

rmueller@rmueller-laptop:~$ 

[/quote]

rmueller@rmueller-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
rmueller@rmueller-laptop:~$ 

rmueller@rmueller-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
rmueller@rmueller-laptop:~$

---

### Post by dbott67 on 2007-04-27
A couple of things:

1. The first command needs a capital '[COLOR=Red]-C[/COLOR]':
 ```
lshw [COLOR=Red]-C[/COLOR] network
```

2. The 2nd lspci needs a '-n' to show PCI vendor and device codes as numbers instead  of  looking them up in the PCI ID list (it helps when trying to find appropriate drivers if you need to use ndiswrapper).

```
rmueller@rmueller-laptop:~$ lspci [COLOR=Red]-n[/COLOR]
```

As for the output of lspci, it indicates that you have a Prism 2.5 Wavelan chipset:

```
rmueller@rmueller-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
[COLOR=Red] 02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)[/COLOR]
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
rmueller@rmueller-laptop:~$ 
```

If you can re-post the 2 commands above we should have enough info to get the wireless working.

-Dave

---

### Post by Minker17 on 2007-04-27
[quote= ]rmueller@rmueller-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=prism2_pci ip=10.1.0.217 latency=64 multicast=yes
       resources: iomemory:f8000000-f8000fff irq:9
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 08:00:46:ac:7d:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=10.1.0.185 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:e8202000-e8202fff ioport:4000-403f irq:9
rmueller@rmueller-laptop:~$ 
rmueller@rmueller-laptop:~$ 
[/quote]

[quote= ]rmueller@rmueller-laptop:~$ lspci -n
00:00.0 0600: 8086:1a30 (rev 04)
00:01.0 0604: 8086:1a31 (rev 04)
00:1e.0 0604: 8086:2448 (rev 42)
00:1f.0 0601: 8086:248c (rev 02)
00:1f.1 0101: 8086:248a (rev 02)
00:1f.3 0c05: 8086:2483 (rev 02)
00:1f.5 0401: 8086:2485 (rev 02)
00:1f.6 0703: 8086:2486 (rev 02)
01:00.0 0300: 1002:4c59
02:02.0 0280: 1260:3873 (rev 01)
02:05.0 0607: 1180:0475 (rev b8)
02:05.1 0c00: 1180:0551
02:07.0 0c03: 1033:0035 (rev 43)
02:07.1 0c03: 1033:0035 (rev 43)
02:07.2 0c03: 1033:00e0 (rev 04)
02:08.0 0200: 8086:1031 (rev 42)
[/quote]


Here

---

### Post by dbott67 on 2007-04-27
What version of Ubuntu are you running?  Dapper 6.06, Edgy 6.10, Feisty 7.04?

A quick search of your card turned up this little fix for Edgy:

Open your blacklist file:
```
sudo gedit /etc/modprobe.d/blacklist
```

Add the following lines to the end:
```
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap
```

Save the file & re-boot.

Try connecting to the wireless again.

-Dave

---

### Post by Minker17 on 2007-04-27
Feisty.

---

### Post by dbott67 on 2007-04-27
I found a post that verifies the fix for Feisty.

Please follow the steps in my post above ([#16]("http://ubuntuforums.org/showpost.php?p=2549142&postcount=16"))

-Dave

---

### Post by Minker17 on 2007-04-27
You Sir, Are AWESOME!! I've been running into this issue when I've installed X/Ubuntu on other machines and no one has been able to help me out.

Thank you very much for your help. I appreciate how nice you were!!

Rick

Also, being new to this, what exaclty did all of the above do?

---

### Post by dbott67 on 2007-04-27
Hey Rick,

Glad it's working! :)

The blacklist file is a list of modules (*aka drivers in the Windows world*) that are prevented from loading.  Linux is modular, meaning that it automatically loads modules when it detects the hardware in the system.  Some modules can cause problems/conflicts, so we are telling Ubuntu to NOT load them.

From what I can tell, the card you have can use either the [COLOR=Red]prism2[/COLOR] module or the [COLOR=Red]orinoco[/COLOR] modules (Orinoco is a wireless card manufacturer).  By blacklisting the prism2 drivers (and related modules) we're forcing Ubuntu to use the orinoco drivers.

If you post the output of lsmod, it will list all currently loaded modules.  The file is kind of long, so you can 'grep' it for orinoco:
```
lsmod | grep orin
```For example, my computer uses the 8139too module, so I can search to see if the module is loaded:
```
dbott@feisty:~$ lsmod | grep 8139
8139too                27648  0 
mii                     6528  1 8139too

```You'll notice that I'm only searching for part of the name (just '8139' rather than  '8139too'), as grep will return anything that has 8139 in it.

Anyhow, glad I could help.  Feel free to keep asking questions if you need more clarification.

-Dave

---

### Post by Minker17 on 2007-04-27
Here is what came out:

[quote= ]orinoco_pci             8064  0 
orinoco                43028  1 orinoco_pci
hermes                  8448  2 orinoco_pci,orinoco
[/quote]

So I take it that it is orinoco.

---

### Post by dbott67 on 2007-04-27
Yep.  You may also want to keep a written log of this blacklist hack for future reference/upgrades.

-Dave

---

