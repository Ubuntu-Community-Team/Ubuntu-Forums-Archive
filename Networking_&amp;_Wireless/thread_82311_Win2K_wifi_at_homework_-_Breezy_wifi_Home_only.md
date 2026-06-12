---
title: "Win2K wifi at home/work - Breezy wifi Home only"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by theProf on 2005-10-26
Hi all.  This is my first post.  Most issues that I have I'm able to resolve by searching the threads, but this one's got me stumped.

I have a wifi access point at home and another at work (I'm a high school teacher).  Both are configured identically, as far as I can tell. (same SSID, same WEP key, etc...)

Under Win2K (I'm using a dual boot laptop), I can connect wirelessly to my network at home and at school without making changes (IP's are assigned by DHCP).

Under Breezy, I can connect at home, but at school I cannot get out to the internet...I get a signal from the AP, but I can't ping it, I can't ping other IP's on the network, and the only way I can get an IP is by assigning one statically.

If I enable eth0, I can connect to the school's network wired and get an IP assigned and use the internet.  I need your help to get wireless working in my classroom so I can be a full-time Ubuntu user at work.

Here are resolv.conf and ipconfig/iwconfig for when I'm connected wirelessly and wired.

Thanks

Wired & working resolv.conf:
search darwin.mec.edu
nameserver 216.20.63.147
nameserver 216.20.63.145

Wired and working ifconfig:
mrlefebvre101@lxlaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:49:48:8F
          inet addr:172.16.6.96  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::204:76ff:fe49:488f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:261413 (255.2 KiB)  TX bytes:824 (824.0 b)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2546714 (2.4 MiB)  TX bytes:2546714 (2.4 MiB)


Wireless and frustrated resolv.conf:
search darwin.mec.edu
nameserver 216.20.63.147
nameserver 216.20.63.145

Wireless and frustrated ifconfig:
mrlefebvre101@lxlaptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:248986 (243.1 KiB)  TX bytes:248986 (243.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:B3:A6:17
          inet addr:172.16.6.92  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::240:5ff:feb3:a617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:892868 (871.9 KiB)  TX bytes:4928 (4.8 KiB)
          Interrupt:11 Base address:0x4800

Wireless iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"80Westwood"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:09:5B:6F:4C:6A
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Thanks for all of your help.

---

### Post by theProf on 2005-10-27
Sorry to bump, but I really need some direction.
If any of my initial info is unclear, let me know what you need.

Thanks

---

### Post by TimonVO on 2005-10-27
Try wifi-radar, it let's you set up profiles per acces point. Easy to use...
**sudo apt-get install wifi-radar**

---

### Post by theProf on 2005-10-31
I installed wifi radar, turned on SSID broadcast, turned off WEP, and I still cannot get an IP address assigned by the network here at school.

I can connect fine when wired, and my wireless config works perfectly at home.  Can you think of anything else that could be preventing me from getting an IP address while I'm at school?

It just seems so strange that W2K works Ok at home and at school over WiFi without config changes, but Linux is acting differently.  I can't think of what could be causing this.

Thanks for the contuned help.

---

