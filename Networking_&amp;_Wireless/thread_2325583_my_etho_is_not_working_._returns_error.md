---
title: "my etho is not working . returns error"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by Deepesh_Thapa on 2016-05-23
[COLOR=#242729][FONT=Arial]i was trying to add IP alias but i cannot add etho:0 because it is not working.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]$ lsusb[/FONT][/COLOR]
unable to initialize libusb: -99
[COLOR=#242729][FONT=Arial]$ lspci -nn | grep 'Wireless Brand'[/FONT][/COLOR]
> pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
[COLOR=#242729][FONT=Arial]$ifconfig[/FONT][/COLOR]
> lo        Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:2483 errors:0 dropped:0 overruns:0 frame:0
      TX packets:2483 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:2230287 (2.2 MB)  TX bytes:2230287 (2.2 MB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
      UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
      RX packets:153914 errors:0 dropped:0 overruns:0 frame:0
      TX packets:61195 errors:0 dropped:16 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:179746346 (179.7 MB)  TX bytes:7583715 (7.5 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
      inet addr:162.213.195.196  P-t-P:162.213.195.196  Bcastxx.213.195.196  Mask:255.255.255.255
      UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
[COLOR=#242729][FONT=Arial]$iwconfig[/FONT][/COLOR]
> The program 'iwconfig' is currently not installed. You can install it by typing:
apt-get install wireless-tools
> [COLOR=#242729][FONT=Arial]$ iwconfig wlan0 - program not installed[/FONT][/COLOR]
sudo lshw -C network
  > *-network DISABLED
   description: Ethernet interface
   physical id: 1
   logical name: gretap0
   capabilities: ethernet physical
   configuration: broadcast=yes driver=ip_gre link=no multicast=yes
[COLOR=#242729][FONT=Arial]UBUNTU 15.04 running in VPS[/FONT][/COLOR]

---

