---
title: "[SOLVED] Please help me set up my wireless"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Obeide on 2008-11-03
Hello,
I've posted this on the absolute beginners site, and I thought perhaps someone over here would be good enough to help me.
I've just installed the latest version of ubuntu on my old laptop and I can't get it to see the wireless connection at home.

I'm using a Belkin wireless card using the BCM4318 chipset. I did 'lspci' and it can see it, but it won't find my connection.

Fass suggested I try this:
> 
Hi!

Have you installed the firmware for the device yet? If what I just said makes no sense to you, try running the following command in a terminal (Applications -> Accessories -> Terminal):

Code:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

It will ask you for the password you use to login to your user account. Enter it (it will not show up on the screen, so don't be alarmed that you can't see any asterisks) and press enter. You should see some output.

You will need a working internet connection for that, so hook up your computer to a wired connection before you run it. Once that command has run, reboot. You should now be able to see your AP/Wireless router in network manager.

I've tried this and it says command not found. It doesn't ask me for my password either.

I don't know if any of this info will help:
lspci
> :
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig
> :
lo no wireless extensions.

eth0 no wireless extensions.

irda0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

lspci -v
> :
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Subsystem: Belkin Device 7011
Flags: bus master, fast devsel, latency 64, IRQ 11
Memory at c4000000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

Any/all help gratefully received

---

