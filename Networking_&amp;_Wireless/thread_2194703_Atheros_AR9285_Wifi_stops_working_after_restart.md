---
title: "Atheros AR9285: Wifi stops working after restart"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by marko.lazaric on 2013-12-20
My wifi works on the live USB and when I reinstall ubuntu and restart it works at first but after the second restart it doesn't show any networks anymore. If you need anything else just tell me which commands to run and I will post the output.

Oh and P.S. I don't know if this matters but I have it as dual boot with windows and the wifi works fine on the windows.

---

### Post by tfrue on 2013-12-20
Would you ever be so kind and post these commands?
```
lspci
```
```
cat /etc/network/interfaces
```
```
ifconfig -a
```
Thanks!

-Chris

---

### Post by marko.lazaric on 2013-12-20
lspci:
> 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce G 103M] (rev a1)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


cat:
> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider


auto wlan0
iface wlan0 inet manual


ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:11:5c:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168336 (168.3 KB)  TX bytes:168336 (168.3 KB)


wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:03:43:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by Iowan on 2013-12-20
Since there is an entry in */etc/network/interfaces* for wlan0, Network Manager *probably* isn't handling it.
One quick thing to try would be to (sudo) edit the file and comment out the two lines for wlan0.
(You can put them back if it doesn't help)
You'll need to restart networking.

---

### Post by marko.lazaric on 2013-12-20
Thanks for the quick response, that fixed it.

---

