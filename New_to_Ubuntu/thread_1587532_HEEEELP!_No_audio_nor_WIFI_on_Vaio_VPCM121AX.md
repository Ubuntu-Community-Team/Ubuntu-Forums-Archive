---
title: "HEEEELP! No audio nor WIFI on Vaio VPCM121AX"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Saracho on 2010-10-03
Hi,

I just installed Ubuntu Netbook Remix on a Sony Vaio VPCM121AX Netbook and I can't get my headphone audiojack and my wireless connection to work. 

How can i find the specific drivers to run this?

Thanks in advance

---

### Post by Hippytaff on 2010-10-03
```

lspci

```
paste the output to this

---

### Post by Saracho on 2010-10-03
saracho@saracho-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
02:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
saracho@saracho-laptop:~$

---

### Post by Hippytaff on 2010-10-03
what does this
```

sudo lshw -C network

```

---

### Post by Saracho on 2010-10-03
> **Hippytaff said:**
> what does this
```

sudo lshw -C network

```


how can i enable it?

[sudo] password for saracho: 
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 02
       serial: 54:42:49:61:7a:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=half ip=10.0.0.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:fe800000-fe803fff ioport:e100(size=128) ioport:e000(size=256)
saracho@saracho-laptop:~$

---

### Post by Hippytaff on 2010-10-03
this puts it more succinctly than I can - 

> **ajgreeny said:**
> Right click on the network manager icon in your  panel and choose "Edit Connections" then to the wireless tab.  Click on  the wireless connection and choose Edit.  After entering the password  you will see a window with two small tick boxes top and bottom left for  "Connect automatically" and "Available to all users".  Make sure both  are selected and that should do it for you.

---

### Post by Saracho on 2010-10-03
> **Hippytaff said:**
> this puts it more succinctly than I can -
is there another way to enable it?

it doesn't detect any connection

---

### Post by Hippytaff on 2010-10-03
```

iwconfig

```

what does this bring back?

---

### Post by Saracho on 2010-10-03
> **Hippytaff said:**
> ```

iwconfig

```what does this bring back?



lo        no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

saracho@saracho-laptop:~$

---

### Post by Hippytaff on 2010-10-03
Looks like a driver issue - might be a bug - try this

```

dpkg-reconfigure rt3090-dkms

```

---

### Post by Saracho on 2010-10-03
> **Hippytaff said:**
> Looks like a driver issue - might be a bug - try this

```

dpkg-reconfigure rt3090-dkms

```

saracho@saracho-laptop:~$ dpkg-reconfigure rt3090-dkms
/usr/sbin/dpkg-reconfigure must be run as root
saracho@saracho-laptop:~$

---

### Post by Hippytaff on 2010-10-03
sudo dpkg-reconfigure rt3090-dkms

---

### Post by Saracho on 2010-10-03
Package `rt3090-dkms' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: rt3090-dkms is not installed
saracho@saracho-laptop:~$

---

### Post by Hippytaff on 2010-10-03
no driver, worth looking into ndsiwrapper and search your driver (rt3090) on the forums...I'll do some reading.

---

### Post by Saracho on 2010-10-03
> **Hippytaff said:**
> no driver, worth looking into ndsiwrapper and search your driver (rt3090) on the forums...I'll do some reading.

how can i find the driver?

---

### Post by Saracho on 2010-10-03
i found this

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

---

### Post by Hippytaff on 2010-10-04
Worth a bash

---

### Post by Saracho on 2010-10-05
How can i add the PPA?

---

### Post by spydeyrch on 2010-10-05
forgive me if it has already been mentioned. I skimmed the previous posts so it might have missed my eyes. But ...... have you tried to connect to the inter via a wired connection and install hardware drivers that way?

if your nettop has a wired ethernet port, which most do, can you connect to the internet via that method? If so, then once connected, go to (and again, forgive me as I am trying to remember these menu paths from memory and don't have an ubuntu system in front of me):

system -> admin -> hardware

once you have selected that option, then due to being connected to the net, ubuntu will go and search for any proprietary drivers that would enable specific hardware in your nettop. typically this is how one would go about enabling their wireless, if it wasn't auto-recognized from the get-go. It may also find drivers for your sound card. It may work, it may not.

Again, sorry if this all was already mentioned. Hope it works for you!

-Spydey  :)

---

### Post by Saracho on 2010-10-05
Hi,
the thing is that when I head to hardware drivers it appears empty :(

---

### Post by Hippytaff on 2010-10-05
> **spydeyrch said:**
> forgive me if it has already been mentioned. I skimmed the previous posts so it might have missed my eyes. But ...... have you tried to connect to the inter via a wired connection and install hardware drivers that way?

if your nettop has a wired ethernet port, which most do, can you connect to the internet via that method? If so, then once connected, go to (and again, forgive me as I am trying to remember these menu paths from memory and don't have an ubuntu system in front of me):

system -> admin -> hardware

once you have selected that option, then due to being connected to the net, ubuntu will go and search for any proprietary drivers that would enable specific hardware in your nettop. typically this is how one would go about enabling their wireless, if it wasn't auto-recognized from the get-go. It may also find drivers for your sound card. It may work, it may not.

Again, sorry if this all was already mentioned. Hope it works for you!

-Spydey  :)

do this

---

### Post by Saracho on 2010-10-05
> **spydeyrch said:**
> forgive me if it has already been mentioned. I skimmed the previous posts so it might have missed my eyes. But ...... have you tried to connect to the inter via a wired connection and install hardware drivers that way?

if your nettop has a wired ethernet port, which most do, can you connect to the internet via that method? If so, then once connected, go to (and again, forgive me as I am trying to remember these menu paths from memory and don't have an ubuntu system in front of me):

system -> admin -> hardware

once you have selected that option, then due to being connected to the net, ubuntu will go and search for any proprietary drivers that would enable specific hardware in your nettop. typically this is how one would go about enabling their wireless, if it wasn't auto-recognized from the get-go. It may also find drivers for your sound card. It may work, it may not.

Again, sorry if this all was already mentioned. Hope it works for you!

-Spydey  :)

I fixed the WiFi...
how can I fix the Headphone/Microphone problem?
How can i know which drive to look for?

---

### Post by spydeyrch on 2010-10-05
> **Saracho said:**
> I fixed the WiFi...
how can I fix the Headphone/Microphone problem?
How can i know which drive to look for?


Great!!! I am glad that it got fixed!! How did you do it? :D

-Spydey

---

### Post by Saracho on 2010-10-05
> **spydeyrch said:**
> Great!!! I am glad that it got fixed!! How did you do it? :D

-Spydey
  I found a post in which a user had the same problem with that driver. :) 
i think it was this link [http://ubuntuforums.org/showthread.php?t=1274886&highlight=rt+3090](http://ubuntuforums.org/showthread.php?t=1274886&highlight=rt+3090)

but i still need to fix the microphone/headphone jack issue :(

---

