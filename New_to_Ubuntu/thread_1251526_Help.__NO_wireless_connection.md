---
title: "Help.  NO wireless connection"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by amarumayo on 2009-08-27
Hi all, 

I am trying to get my wireless working on my presario compaq with ubuntu 9.4.  I was able to connect to my router directly and do the updates as well as to enable the broadcom b43 wireless driver however I still cannot connect to the internet.  Any ideas.  Thanks for the help

---

### Post by tuxxy on 2009-08-27
Try the Wifi guide and report what you find.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by amarumayo on 2009-08-27
octavia@octavia-laptop:~$ sudo lspci -v
[sudo] password for octavia: 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30ae
    Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device 5950
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
    Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: 66MHz, medium devsel
    I/O ports at 8400 [size=16]
    Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0200000-c02fffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Kernel modules: radeonfb

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1355
    Flags: bus master, fast devsel, latency 64, IRQ 21
    Memory at c0200000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 30a4
    Flags: bus master, medium devsel, latency 128, IRQ 22
    I/O ports at a000 [size=256]
    Memory at c0202000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

octavia@octavia-laptop:~$ Thanks

---

### Post by amarumayo on 2009-08-27
Also here is my card and it says it works with ndiswrapper, but I cannot figure out how to get it to work.  I installed ndiswrapper from synaptic but no luck.

Thanks for all your help folks

---

### Post by amarumayo on 2009-08-27
here is the link i meant to send:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318)

---

### Post by tripolitan on 2009-08-27
> **amarumayo said:**
> ...I was able to connect to my router directly and do the updates as well as to enable the broadcom b43 wireless driver however I still cannot connect to the internet.

If you were able to connect to your router wirelessly and do the updates on Ubuntu, this means you're connected, unless there is something missing from your post? Can you clarify and post your ifconfig output? Thanks.

---

### Post by amarumayo on 2009-08-27
sorry i connected using the cable to my modem, but wireless networks are not detected

Chris

---

### Post by Grifulkin on 2009-08-27
> **amarumayo said:**
> sorry i connected using the cable to my modem, but wireless networks are not detected

Chris

I have that same card, so here is how I enabled it while connected to via Ethernet.

```
sudo apt-get install b43-fwcutter
```

then followed by

```
b43-fwcutter
``` 

then it should do the rest of the work for you.  Restart and you should have wireless.

EDIT: I don't even think that last step is needed, after you install I believe it asks to Fetch and Install firmware.

Also if you have trouble connecting to wireless networks, I would suggest using Wicd which is a network manager that I think is better than the bundled gnome-network-manager.

---

### Post by amarumayo on 2009-08-27
Ok I did that.  Restarted but still no internet. Here is the output:

octavia@octavia-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for octavia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
octavia@octavia-laptop:~$ b43-fwcutter
b43-fwcutter version 011

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware
octavia@octavia-laptop:~$

---

### Post by Grifulkin on 2009-08-27
> **amarumayo said:**
> Ok I did that.  Restarted but still no internet. Here is the output:

octavia@octavia-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for octavia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
octavia@octavia-laptop:~$ b43-fwcutter
b43-fwcutter version 011

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware
octavia@octavia-laptop:~$

Okay yeah, I don't know what happened, so one more thing I can think of is run

```
sudo apt-get remove b43-fwcutter
```

then run

```
sudo apt-get autoremove && sudo apt-get install b43-fwcutter
```

That should prompt you again then click yes when it asks to Fetch and Install Firmware.  And it should work, at least I hope thats all I needed to do on mine.

---

### Post by amarumayo on 2009-08-27
Nope still not working,  I was prompted and I selected yes and it installed, but still not wireless networks are connected.  Any other ideas?

---

### Post by Grifulkin on 2009-08-27
> **amarumayo said:**
> Nope still not working,  I was prompted and I selected yes and it installed, but still not wireless networks are connected.  Any other ideas?

Thats all I got but feel free to try [this.](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

---

### Post by tripolitan on 2009-08-27
Your wireless driver is already installed. How about the output of that ifconfig?

---

### Post by amarumayo on 2009-08-27
octavia@octavia-laptop:~$ ifcinfug
bash: ifcinfug: command not found
octavia@octavia-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:32:ad:bc  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe32:adbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16613727 (16.6 MB)  TX bytes:730894 (730.8 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:6f:e6:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-6F-E6-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

octavia@octavia-laptop:~$

---

### Post by tripolitan on 2009-08-27
Fantastic, now open your /etc/network/interfaces and comment out (insert #) everything that pertains to eth0, leave everything else the same:

#auto eth0
#iface eth0 inet dhcp

Physically disconnect your wired connection and restart

---

### Post by amarumayo on 2009-08-27
my /etc/network/interfaces only contains:

auto lo
iface lo inet loopback

not sure what to do from here

---

### Post by tripolitan on 2009-08-27
add

auto wlan0
iface wlan0 inet dhcp

disconnect wired connection and restart

---

### Post by amarumayo on 2009-08-27
ok did that, restarted and still no connection although under my wireless connections icon in gnome which is still greyed out it now reads "device not managed"

---

### Post by tripolitan on 2009-08-27
Your wifi card is properly detected, module loaded and was assigned wlan0
I'm hoping that your router's wireless connection is working (do you have other wifi devices/PCs to test it with?)

If so, 

Here is a shot in the dark, for the hell of it, I would uninstall gnome-network-manager and install wicd, physically disconnect wired cable and restart, then try configuring wifi through wicd again. You need not edit /etc/network/interfaces

---

### Post by amarumayo on 2009-08-27
hey thanks for all your help.  Could you provide codes for the above mentioned steps?  i am learning linux, but still not very competent.  Oh and i have another laptop in the room that is connected to the wireless.

---

### Post by tripolitan on 2009-08-27
Sorry I couldn't go any further but if you get connected (hopefully with wicd and no gnome-network-mangler), please come back and let us know.

---

### Post by amarumayo on 2009-08-27
I dont know how to uninstall gnome-network manager or to install wicd.  Can anyone help me with that?
Thanks

---

### Post by amarumayo on 2009-08-27
Ok I got WICD installed and now my connection is showing but when i go to connect i get:

This network requires encryption to be enabled

Any ideas anyone... I feel so close

Thanks

---

### Post by amarumayo on 2009-08-27
works with wicd

---

### Post by Grifulkin on 2009-08-27
I am glad you got it working, Wicd is way better IMHO than gnome-network-manager.

---

### Post by tripolitan on 2009-08-28
I guess they don't call it network-mangler for nothing! :]

---

