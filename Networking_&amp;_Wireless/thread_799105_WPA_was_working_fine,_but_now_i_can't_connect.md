---
title: "WPA was working fine, but now i can't connect"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by exactopposite on 2008-05-18
I have 2 laptops running hardy 32. My router is an asus 520gu running dd-wrt. Both laptops habe been working fine with wpa since I installed hardy without me having to do anything at all. Today I made some changes to my lan settings (lan dns stuff) and restarted the router. Since then I haven't been able to connect with either of the laptops. If I turn off wpa I can connect with no problem. I have tried restarting the router again several times, changing the ssid and password, and rebooting the laptops. None of this has made any difference. It's strange to me because it was all working fine before. I have been using wpa and dd-wrt with ubuntu since at least feisty with no issues. 

Does anybody have any idea what's going on here?

---

### Post by nicedude on 2008-05-18
You need to list your PC models & series along with output of lspci and iwconfig to help everyone see whats going on. If you know for sure what wireless chipset you are using please include that as well since it saves on the google time :-)

---

### Post by exactopposite on 2008-05-18
> **nicedude said:**
> You need to list your PC models & series along with output of lspci and iwconfig to help everyone see whats going on. If you know for sure what wireless chipset you are using please include that as well since it saves on the google time :-)

Both machines are the same model: Dell Vostro 1400. The output below is from the one that I'm using right now. Both have broadcom wireless chipsets.  One is a dell 1390, and the other is a dell 1395 (I forget which one is which right now). The other laptop is in use  right now and  I don't want to disturb the person using it. For now I'm connected to my router with no encryption.

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"MY SSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: MY MAC ADDRESS   
          Bit Rate=48 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

