---
title: "Could not get 2Wire PCI card to work with my laptop"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by siddii on 2007-01-22
Hi All,

OK. I need some serious help before I give up on this Linux-Wireless thingy. I am a linux newbie who has been trying very hard to enjoy the pleasure of 
Linux. Unfortunately, there are some obstacles along the way, the most important of all is this. 
Let's get to the business. I installed Kubuntu on one of my IBM laptop which was working perfectly fine with Windows XP, 2 Wire Wireless PCI Card and a 2 Wire router (Shipped with SBC internet). I am able to access internet by wired connection. Whereas, I couldn't succeed being wireless.
I tried KNetworkManager, Wireless LAN Manager & Wifi radar. None of them seem to work for me.
I went through this  troubleshooting guide ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)) and tried each & every steps. 
But, still dunno what I am doing wrong. I copied all the command outputs and pasted here for reference. 
Please give me a detailed steps/procedures on how to configure my Linux work wirelessly.

Please let me know if you have any questions.

Thanks all in advance,

Siddique


me@mymachine:~$ sudo lspci -n
0000:00:00.0 0600: 8086:7190 (rev 03)
0000:00:01.0 0604: 8086:7191 (rev 03)
0000:00:02.0 0607: 104c:ac1b (rev 03)
0000:00:02.1 0607: 104c:ac1b (rev 03)
0000:00:03.0 0200: 8086:1229 (rev 0c)
0000:00:03.1 0700: 11c1:045c (rev 01)
0000:00:05.0 0401: 1013:6003 (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 02)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 03)
0000:01:00.0 0300: 5333:8c12 (rev 13)
0000:02:00.0 0280: 1260:3886 (rev 01)


me@mymachine:~$ lspci -v | grep Ethernet
0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)

me@mymachine:~$ lsmod | grep islsm_pci
islsm_pci              22280  0
islsm_device           12040  1 islsm_pci
islsm                  37644  2 islsm_pci,islsm_device

me@mymachine:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      IEEE 802.11b  ESSID:"2WIRE293"
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

me@mymachine:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:B5:F9:EE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:60:B3:24:02:52
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d8b30000-d8b32000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

me@mymachine:~$ sudo iwlist eth2 scan
eth2      No scan results

me@mymachine:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available

me@mymachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      IEEE 802.11b  ESSID:"2WIRE293"
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

me@mymachine:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:B5:F9:EE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:60:B3:24:02:52
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d8b30000-d8b32000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

---

### Post by geekgod on 2007-02-24
Try installing wpa supplicant it helped me connect to my wep encrypted d link

---

### Post by siddii on 2007-05-09
Alright, I finally got this working. If anyone interested in knowing how, here it is

[http://blogs.boxysystems.com/2007/5/9/enabling-wifi-on-thinkpad-t22-using-2wire-802-11g-wireless-pc-on-ubuntu-6-10]("http://blogs.boxysystems.com/2007/5/9/enabling-wifi-on-thinkpad-t22-using-2wire-802-11g-wireless-pc-on-ubuntu-6-10")

---

