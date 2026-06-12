---
title: "Generally having problems getting Ubuntu to work"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Muttz on 2011-02-01
I am sorry for the vague subject line but that pretty much sums it up.  I am really having problems with getting a version of Ubuntu to work.

I have a Toshiba Satellite L300D notebook.  It has a dual core Athlon 64 processor and 4 gb of memory.  I am starting to wonder if the hardware in this notebook just isn't compatible with Ubuntu.  It works perfectly with Vista.

I first installed 10.10 32 bit alongside Vista.  After a couple of days, I could no longer boot into Windows.  Ubuntu ate NTLDR.  So, I decided to dump windows and just go with the Ubuntu install.

That install worked for a few days as well.  I booted up yesterday and there were updates, so I installed them.  After the updates installed, I rebooted and all was fine until I entered my password.  The machine froze and I had to hold down the power button to shut it down.  That's all I could do.

I thought that there was some sort of system restore like Windows, but after checking it out, apparently there isn't.   I reinstalled 10.10 again.  This time, I set it up so that I didn't have to log in when I booted.  Well, as soon as I entered the password for my wireless router, it froze again.  I read somewhere that people with Satellites were having a lot of problems with 10.10, so I downgraded to 10.04, 64 bit.

Again, all was fine until I did the updates.  I was able to connect to the wireless network before updating, but after, I could connect but not load any web pages.  I have full signal strength.   I disconnected from the wireless and plugged in a LAN cable.  The Internet was working, so I restarted the machine and tried to connect via the  wireless connection again.  No go.  The wireless connection is working fine with my XP netbook.

I really like the Ubuntu and don't want to uninstall it.  Would anyone be able to offer troubleshooting advice?  I know that the wireless card is made by Atheros.

Thank you so much.

---

### Post by wojox on 2011-02-01
What if you open your terminal and ping with wireless:

```
ping -c 3 google.com
```

Also try disabling IPV6 in firefox. Type **about:config** in the Location Bar.

Enter **network.dns.disableIPv6** and set it to **true**, restart Firefox.

---

### Post by TBABill on 2011-02-01
One of the updates may have brought in an update or change to the driver or configuration. It's usually best to install, then download and install updates via ethernet (if available) and then install proprietary drivers. That way you are installing post-updates. But that doesn't stop a fresh set of updates from borking something, which may be what happened to you.
 
Which wireless adapter is it? Can you provide the output of this in a terminal ```
lspci
``` if it's internal or ```
lsusb
``` if it's a USB device? And the output of ```
iwconfig
``` and ```
sudo lshw -C network
``` Then we can take a look at what you're working with and what could be going on.

---

### Post by asmoore82 on 2011-02-01
The smoking gun here is this:
> **Muttz said:**
> After a couple of days, I could no longer boot into Windows.  Ubuntu ate NTLDR.
Ubuntu simply does not do this.

It sounds like you have a failing hard drive, but
even if not, it never hurts to test it.

Boot the liveCD and try this:
```
sudo badblocks -sv /dev/sda
```
If the percentage complete doesn't grow steadily and smoothly leading up to
the message "*Pass completed, 0 bad blocks found.*" then you've got a bad drive.

A half-dead drive can run smooth as silk for *years* until you do something
heavy such as installing/updating/upgrading/downgrading your OS.

---

### Post by Muttz on 2011-02-02
Thank you so much.  The wireless card was working when I booted the notebook today, so I may be ok.That was my only issue with 10.04, so I'm going to stick with that. 

asmoore82 - I checked for bad blocks.  Everything is ok.  I don't really know what happened to the Vista partition.  It just disappeared from the boot menu, so I just got rid of it.  I'll run it in a VM if I need it later on.

I am going to post the logs anyway and please let me know if everything looks ok.

lspci  (looks like everything has a driver)

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

lsusb

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


 iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Android"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:AF:F7:DF:58:8F   
          Bit Rate=78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -C network

[sudo] password for*******: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:94:09:9f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:3000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f103ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:dd:50:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f3100000-f310ffff

Thanks again.  Hope that everyone got through the snow storm ok.

---

