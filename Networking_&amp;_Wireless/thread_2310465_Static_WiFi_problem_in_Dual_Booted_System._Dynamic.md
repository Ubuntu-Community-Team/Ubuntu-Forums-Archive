---
title: "Static WiFi problem in Dual Booted System. Dynamic WiFi working"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by shahbaz4 on 2016-01-19
I have dual booted my Lenovo laptop with Window 7/Ubuntu 15.10. As I  am new to the Linux OS, I am gradually reading up and learning things (A  big thanks to this forum).
  I have no problem accessing Internet via wired connection now.  Similarly I can also use Internet over wireless connection at my work  (SSID and password are only requirement). But at my hostel I have to  manually enter static ip details (password not required).
  I can access the static wireless connection using window 7, however  it is whole another story with Ubuntu. My laptop does get connected to  SSID:Hostel, but disconnects instantenously. ping returns "Destination  Host Unreachable" result. 
  [Connection Status]("http://i.stack.imgur.com/PPSkz.png")
  I am still to find a solution to my problem. I have even tried  sudojuice static ip procedure and kayodake instructions. It totally  eliminate wifi existance.
  [kayodake]("http://i.stack.imgur.com/ni0Lq.jpg")
  [HR][/HR]  Results of commands:

ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.2.124 icmp_seq=85 Destination Host Unreachable
From 192.168.2.124 icmp_seq=86 Destination Host Unreachable
From 192.168.2.124 icmp_seq=87 Destination Host Unreachable
From 192.168.2.124 icmp_seq=88 Destination Host Unreachable
From 192.168.2.124 icmp_seq=89 Destination Host Unreachable
From 192.168.2.124 icmp_seq=121 Destination Host Unreachable
From 192.168.2.124 icmp_seq=122 Destination Host Unreachable
From 192.168.2.124 icmp_seq=123 Destination Host Unreachable
From 192.168.2.124 icmp_seq=124 Destination Host Unreachable
From 192.168.2.124 icmp_seq=125 Destination Host Unreachable
From 192.168.2.124 icmp_seq=126 Destination Host Unreachable
From 192.168.2.124 icmp_seq=127 Destination Host Unreachable
From 192.168.2.124 icmp_seq=128 Destination Host Unreachable
From 192.168.2.124 icmp_seq=129 Destination Host Unreachable
From 192.168.2.124 icmp_seq=130 Destination Host Unreachable
From 192.168.2.124 icmp_seq=131 Destination Host Unreachable
From 192.168.2.124 icmp_seq=132 Destination Host Unreachable
From 192.168.2.124 icmp_seq=133 Destination Host Unreachable
From 192.168.2.124 icmp_seq=134 Destination Host Unreachable
From 192.168.2.124 icmp_seq=135 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
174 packets transmitted, 0 received, +20 errors, 100% packet loss, time 173205ms
pipe 4
  [HR][/HR]  wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wiriweless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wiriweless-info) && chmod +x wireless-info && ./wireless-info

--2016-01-11 01:22:42--  [https://github.com/UbuntuForums/wireless-info/raw/master/wiriweless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wiriweless-info)
Resolving github.com (github.com)... failed: Connection timed out.
wget: unable to resolve host address ‘github.com’
  [HR][/HR]  sudo lshw -c network
[sudo] password for shahbaz:           
  *-network               
   description: Wireless interface
   product: BCM4312 802.11b/g LP-PHY
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:04:00.0
   logical name: wlp4s0
   version: 01
   serial: *****
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
   configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.*.* latency=0 multicast=yes wireless=IEEE 802.11abg
   resources: irq:18 memory:f4500000-f4503fff
  *-network
   description: Ethernet interface
   product: NetLink BCM5906M Fast Ethernet PCI Express
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:07:00.0
   logical name: enp7s0
   version: 02
   serial: *****
   capacity: 100Mbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
   resources: irq:32 memory:f4600000-f460ffff
  [HR][/HR]  sudo iwconfig
lo        no wireless extensions.

enp7s0    no wireless extensions.

wlp4s0    IEEE 802.11abg  ESSID:"Hostel"  
      Mode:Managed  Frequency:2.422 GHz  Access Point:  D8:67:D9:C4:3B:EF   
      Bit Rate=48 Mb/s   Tx-Power=200 dBm   
      Retry short limit:7   RTS thr:off   Fragment thr:off
      Encryption key:off
      Power Management:off
      Link Quality=44/70  Signal level=-66 dBm  
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  [HR][/HR]  sudo ifconfig wlp4s0 up
dmesg | grep iwlwifi

no results for both
  [HR][/HR]  lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
  00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) 00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) 00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
  [HR][/HR]  ip addr show wlp4s0
3: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
link/ether *:*:*:*:*:* brd ff:ff:ff:ff:ff:ff
inet 192.168.*.*/22 brd 192.168.*.* scope global wlp4s0
   valid_lft forever preferred_lft forever
inet6 fe80::*:*:*:*/64 scope link 
   valid_lft forever preferred_lft forever
  [HR][/HR]  ip link show wlp4s0
3: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DORMANT group default qlen 1000
link/ether *:*:*:*:*:* brd ff:ff:ff:ff:ff:ff
  [HR][/HR]  sudo iw wlp4s0 link
Connected to d8:67:d9:c4:3b:ef (on wlp4s0)
SSID: Hostel
freq: 2422
signal: -66 dBm
tx bitrate: 48.0 MBit/s
  [HR][/HR]  rfkill list all
0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no

---

