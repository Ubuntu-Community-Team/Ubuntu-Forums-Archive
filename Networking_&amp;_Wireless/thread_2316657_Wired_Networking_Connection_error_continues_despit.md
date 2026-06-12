---
title: "Wired Networking Connection error continues despite trying all fixes.."
date: 2016-03-09
forum: Networking &amp; Wireless
---

### Post by Eric_Bruce on 2016-03-09
So I have been using various Ubuntu based distros for a couple of months. Recently had a freeze on an installation of Zorin OS 10 ult and did a hard reboot. Ever since then I am unable to connect to internet using any distro. have erased and reinstalled a couple distros but still get the "Disconnected-you are now offline" message only a couple of seconds after booting to any distro. 

I've spent past couple of days trying many of the "fixes" I've found online with no sucess. Currently,. I just reinstalled Zorin 11 core 64bit with the same issues. 

I'm going to post the output of many of the previous "fixes" to see if anyone here can spot an issue. I also thought that my original Intel ethernet port was bad and added a pci ethernet port but all i have now are two ethernet ports that are not connecting:(.

```
eric@eric-OptiPlex-760:~$ lspci -nn | grep -i eth
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit 


Network Connection [8086:10de] (rev 02)
04:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 


PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)


 eric@eric-OptiPlex-760:~$ ifconfig -a
enp0s25   Link encap:Ethernet  


HWaddr 00:23:ae:70:37:d7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:975 


errors:0 dropped:0 overruns:0 frame:0
          TX packets:1645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 


txqueuelen:1000 
          RX bytes:242565 (242.5 KB)  TX bytes:322907 (322.9 KB)
          Interrupt:21 Memory:f7fe0000-


f8000000 


enp4s2    Link encap:Ethernet  HWaddr c4:e9:84:02:5e:2b  
          inet6 addr: fe80::c6e9:84ff:fe02:5e2b/64 


Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1091 errors:0 


dropped:0 overruns:0 frame:0
          TX packets:1685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 


txqueuelen:1000 
          RX bytes:268024 (268.0 KB)  TX bytes:323166 (323.1 KB)


lo        Link encap:Local Loopback  
          


inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  


Metric:1
          RX packets:10949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10949 errors:0 dropped:0 


overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:815259 (815.2 KB)  TX bytes:815259 (815.2 KB)


eric@eric-OptiPlex-760:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 


Gigabit Network Connection [8086:10de] (rev 02)
	Subsystem: Dell Device [1028:027f]
	Kernel driver in use: e1000e
--
04:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller 


[10ec:8169] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC 


[10ec:8169]
	Kernel driver in use: r8169


eric@eric-OptiPlex-760:/media$ dmesg | egrep 'eth0|b44'
[    1.672270] 


r8169 0000:04:02.0 eth0: RTL8169sb/8110sb at 0xffffc90000e62f00, c4:e9:84:02:5e:2b, XID 10000000 IRQ 18
[    1.672274] 


r8169 0000:04:02.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    1.750252] r8169 0000:04:02.0 


enp4s2: renamed from eth0
[    2.124466] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:23:ae:70:37:d7
[    


2.124469] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.124501] e1000e 0000:00:19.0 eth0: 


MAC: 8, PHY: 8, PBA No: 8021FF-0FF
[    2.125295] e1000e 0000:00:19.0 enp0s25: renamed from eth0




```

---

### Post by Eric_Bruce on 2016-03-09
Here are the /etc/network/interfaces and /etc/NetworkManager/NetworkManager.conf files:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false



```

I've tried adding the changes suggested in prev posts for:

auto eth0
#iface eth0 inet dhcp
to the interfaces file and I had changed the 
[ifupdown]
managed=false

to managed=true

and neither had any effect. I can't tell what the current connections are named as i see the lines that say "renamed from eth0" etc but I don't know what the names for the ethernet connections are now.

I also tried setting IPV6 to ignore and IPV4 to DHCP Automatic with no effects noted.

---

