---
title: "WPA problem Jaunty on Sony FZ21s"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by ken1234 on 2009-06-09
I am totally new to Linux and have just loaded Jaunty on a USB disc attached to a Sony FZ21S machine with Vista loaded on the internal disc. When the USB disc is attached the unit boots into Ubuntu otherwise Vista is loaded. I have no problems using wireless on Vista but need help please with Ubuntu when logging on through WPA secured router. When I try to log on I click the double screen icon which shows a wired and wireless option. Wired works very well. Wireless shows the ssid of my router and an excellent signal strength. Selecting the router and the double icon is replaced by a circulating icon which then asks for my WPA password. (Wireless network authentication required).

No matter how many times I enter this the same request reappears and I never get on line. 

Output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"router"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1a:80:18:48:9d  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:fe18:489d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5513888 (5.5 MB)  TX bytes:599231 (599.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:a1:1d:f3  
          inet6 addr: fe80::213:e8ff:fea1:1df3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36273 (36.2 KB)  TX bytes:38622 (38.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-A1-1D-F3-64-66-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have tried disconnecting the wired connection and rebooting with just wireless enabled but the result is the same.

Many thanks for any help.

---

### Post by ken1234 on 2009-06-10
Please can anyone help with this. Is there any way to get on line wireless with 4965 and Ubuntu? 

Thanks.

---

