---
title: "Wireless on Hardy 8.04"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Canobuntu on 2008-05-08
Hi. 
I have been using Ubuntu for about a month, so am still a relative newbie. I got the Wireless working with Gutsy Gibbon, but the upgrade to Hardy Heron has rather set me back. I cannot seem to get it working again.

I am trying to get a Wireless Network going with WPA (PSK/TKIP) protocols. I have installed ndiswrapper and the Windows Wireless Drivers interface in Hardy. I have run the "Windows Wireless Drivers" tool and pointed it to the same drivers as worked for Gutsy. 

I have Configured the wireless network for the SSID and Password, as well as DHCP, but although the green light flashes on the card, I cannot use the connection. I think the problem is that I seem to have two wireless interfaces defined:-
[LIST]
[*]wlan0 - which seems to be an IPV6 Interface
[*]wlan0:avahi - which seems to be the working interface, but is not used by the browser etc.[/LIST]

iwconfig only lists wlan0
ifconfig lists wlan0 and wlan0:avahi (The avahi interface has an IP address associated with it!)

If I use "System>Administration>Network Tools" then it lists 4 Network Devices - lo, eth0, wlan0, wlan0:avahi. I suspect this is giving the same information as ifconfig.

Any help would be greatly appreciated.

Thanks

---

### Post by superprash2003 on 2008-05-08
it could be that your router has DHCP disabled which is not giving an ip to your machine.. you could try typing the ip address manually

---

### Post by Canobuntu on 2008-05-09
Thanks for the response. 
DHCP seems to be working fine with other machines on the network, both wireless and wired. Also, the interface advertising itself as wlan0:avahi seems to have picked up an IP address.

What I don't understand is why a second interface seems to have been created for the wireless card and how I can remove it?

Thanks again.

---

### Post by superprash2003 on 2008-05-09
well the ip wlan0:avahi is mostly 169.x.x.x this happens when you arent getting an ip address from your router..Have you tried entering a static ip

---

### Post by Canobuntu on 2008-05-09
Thanks Superprash. 
You are absolutely correct - when I defined a Static IP address, the wlan:avahi port went away, but Wireless is still not working.

I have configured a Static IP address (192.168.1.3 - DHCP is configured from 64 upwards on my router) The Card is now flashing a green light, and the iwconfig command lists wlan0 with IP address, SSID etc. 

But, the browser still fails to connect. (works OK wired). Any ideas?

Thanks

---

### Post by Canobuntu on 2008-05-09
Oh. And I have reset both the computer and the router.

---

### Post by superprash2003 on 2008-05-09
try pinging your router and post output here.. go to the terminal and type ping 192.168.1.1 replace 192.168.1.1 with your router's ip address..also type ifconfig in the terminal and post output here

---

### Post by Canobuntu on 2008-05-10
Firstly, thanks for your continued support - it is much appreciated. Also, please be aware that I will be offline from tomorrow PM until Friday, but will be backl trying to get this to work then.

Now to the Post.

******************************
First, the results over a wired connection to the same router

laptop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=1.56 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=0.879 ms

[1]+  Stopped                 ping 192.168.1.254
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:2b:e7:f0  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:613459 (599.0 KB)  TX bytes:97168 (94.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4966 (4.8 KB)  TX bytes:4966 (4.8 KB)

****************************
Now, with the Wireless Card inserted and ethernet cable removed. 

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BTHomeHub-7FD0"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:18:F6:5C:10:2B   
          Bit Rate=125 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:2b:e7:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:615079 (600.6 KB)  TX bytes:97502 (95.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6112 (5.9 KB)  TX bytes:6112 (5.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:49:db:86:9c  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2468 (2.4 KB)  TX bytes:1460 (1.4 KB)
          Interrupt:11 Memory:34020000-34022000 

laptop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable

[1]+  Stopped                 ping 192.168.1.254
laptop:~$ ping -I wlan0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.3 wlan0: 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable

[2]+  Stopped                 ping -I wlan0 192.168.1.254
laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

Hope this helps.

---

### Post by Canobuntu on 2008-05-10
Just remembered how to do a hardware listing - this may also be useful.

laptop:~$ sudo lshw -C network
*-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:c0:49:db:86:9c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+usr11g driverversion=1.52+U.S. Robotics,06/28/2004,6. latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by superprash2003 on 2008-05-10
while entering the static ip.. have you made sure that you entered the gateway ip as 192.168.1.254? and also make sure that the subnet is the same.. and try pinging again.. if it gives destination unreachable..Try using Roaming Mode or DHCP mode..

---

### Post by tak1150 on 2008-05-10
Your problem may be related to the new problem associated with how the ssb module is built in the new kernel for Hardy.

If you google ssb, ndiswrapper, hardy, etc, you'll get more info, but here is an example:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558)

I'm working on this problem right now :(
I'm fairly sure that this problem applies to everybody who wants to use ndiswrapper (and ethernet at the same time) in Hardy. Or am I wrong?

---

