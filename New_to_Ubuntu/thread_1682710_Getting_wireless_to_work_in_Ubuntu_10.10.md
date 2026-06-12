---
title: "Getting wireless to work in Ubuntu 10.10"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by veroslav on 2011-02-06
Hi all,

I've just finished installing Ubuntu 10.10 on my new computer (dual boot with WIndows 7) and I am struggling to get the wireless Internet connection to work. The wired connection is working with no problem though.

I recall that It actually worked directly when I was testing it out with Live CD before the installation, but now it wont.

I checked that "Enable Wireless" and "Enable Networking" both were checked from within Network Manager,  and they are, but it does not help.

Below are the outputs from lspci -v and iwconfig respectively, could somebody have a look and see what might be the cause for the issues I am having? Thank you in advance.

```
user@user-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f8000000-fbcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Subsystem: Device 003c:009c
    Flags: fast devsel

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7fffc00 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7ffc000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbd00000-fbdfffff
    Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbe00000-fbefffff
    Prefetchable memory behind bridge: 00000000ce000000-00000000ce1fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 00000000ce200000-00000000ce3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7ff6000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 50
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=32]
    Memory at f7ff4000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: medium devsel, IRQ 11
    Memory at f7fff800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 0753
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fbc80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at d800 [size=256]
    Memory at fbdff000 (64-bit, non-prefetchable) [size=4K]
    Memory at f6ffc000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbdc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 2a9c
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fbeff800 (64-bit, non-prefetchable) [size=2K]
    I/O ports at e800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

04:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Lite-On Communications Inc Device 6632
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci

``````
user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by odysseusjak on 2011-02-06
From my limited experience, that all looks fine. Do you see any wireless networks from which you can choose?

---

### Post by veroslav on 2011-02-06
Thank you for replying.

I cant see any wireless networks what so ever, and I know that there are at least two here.

Also, I've found this that might explain it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

I've tried to create the folder/files that were mentioned there but with no luck (it works in Ubuntu 10.04 though).

I am reading through that bug report in hope I find something interesting (like reply #103 there, but I am not sure if it will help in this case)

Please do keep suggestions coming, if you have any, I am starting to become desperate for this to work.

Thanks.

Kind Regards,
Veroslav

---

### Post by bkratz on 2011-02-06
Here is a pretty good thread with a lot of people reporting success.

[http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)

---

### Post by odysseusjak on 2011-02-06
Try this: run 10.10 from the disc / usb key and take a look at the wifi networks. Try to connect to one. If connected, copy that information down. Then boot into your hd 10.10 and go to your network connections and see if you can either create a new network with the information you took down or join a hidden network with the info you to down.

Also, see if there are any additional drivers that may be needed. System > Administration > Additional Drivers

---

### Post by veroslav on 2011-02-06
Thank you both for your replies, will try both the "boot from Live CD and note wireless settings" and "install new driver" tips.

The only thing I am unsure of in the solution mentioned in the thread to which bkratz's link was pointing to, is whether I should install the newest, or the older version of this driver (the one to which somebody posted a direct link to)?

Thanks again.

/V

---

### Post by veroslav on 2011-02-06
Taking note of the connection settings from the Live CD did not work unfortunately, still no connection :(

I find the solution provided in the link above to be quite a difficult one for a novice like myself, I am in a doubt on what version of the driver to download, someone said 2.4.0.1 but the newest is 2.4.0.4 and someone couldn't get it to work with versions newer than 2.4.0.1. Also, the rapidshare link pointed to a version for 3390 and not 3090.

Very confused at the moment :(

/V

---

### Post by TBABill on 2011-02-06
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add these lines to the end of the file and save...
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```

Then you need to edit your modules file (drivers to load at boot)...```
gksudo gedit /etc/modules
```

At the end of that file add ```
rt2860sta
``` Then save and restart. That should get you back in business.

Note: The RT3090 uses the same driver as the RT2860. All these instructions are doing is making the system use the RT2860sta driver and ignore the RT2800 variants.

---

### Post by veroslav on 2011-02-06
TBABill, you are my hero man! It is working, as I am writing this post from my brand new wireless connection!! :)

Thanks again!

Kind Regards,
Veroslav

---

### Post by TBABill on 2011-02-06
You are truly welcome!! Glad you have it sorted out. Save a copy in case of a reinstall or distro hopping :)

---

