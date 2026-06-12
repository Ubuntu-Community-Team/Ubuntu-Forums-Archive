---
title: "eth0:avahi (no internet connection)"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by tcherno on 2007-08-31
i installed yesterday the latest version of UBUNTU on my toshiba laptop with windows XP. When i tried to configure the internet connection, (i use ppoe) with username & password and proxy server... it worked fine, i suspend the laptop, after 1 hour, i couldnt reconnect, i spent 2 hours till i put everything in order again.
i discovered that i have internet connection when there's no etho:avahi in the device list in network.

now i can't connect to the internet, i have in the device list l0, eth0, & eth0:avahi
in eth0, i have an IP (IPv4) - i put a static IP for my home network (PC to PC) but when i want to connect to the internet, i change to Dynamic
in eth0:avahi i have (IPv6) (when i click to configure, it gives me a message that i cant, cause there's something missing... or something like that)

i searched the net and i found that i have to bring the two IP versions in eth0. but how?
i need to resolve this problem so i can download the latest updates cause if it does not work, i will consider reformatting the laptop and install only XP.

here's some command results...


lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:7F:1C:F3  
          inet6 addr: fe80::202:3fff:fe7f:1cf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116022 (113.3 KiB)  TX bytes:52016 (50.7 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:02:3F:7F:1C:F3  
          inet addr:169.254.7.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6135 (5.9 KiB)  TX bytes:6135 (5.9 KiB)


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



 cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0:avah

iface eth0:avah inet manual





iface eth0 inet dhcp
address 192.168.1.2
netmask 255.255.255.0



auto eth0





 ping -c6 64.223.269.103
ping: unknown host 64.223.269.103

---

