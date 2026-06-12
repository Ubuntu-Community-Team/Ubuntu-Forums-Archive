---
title: "I have a one-way wireless connection?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2007-11-11
For some bizarre reason, I can no longer use my wireless connection. It is there, the Network Monitor displays it in the panel, and when I click on it it brings up "status: Idle, signal strength: ca 90%, lots of packets sent, and zero packets received".

It used to work great, until I installed a number of software updates either yesterday or the day before. I've been insane busy lately and the days are a blur of pain and hard work so I don't remember exactly when I did the update, but I do know that I did not have this problem before the updates were installed. That's the only major change I am aware of making.

I'm on the laptop listed in my sig, with the W200 wireless card and the driver that link leads to. Other  wireless devices in the house work connect without problems. Any help is appreciated... being able to see the connection but not use it, is very frustrating.

Oh, and when I type in "iwconfig eth1" in the terminal, it brings up this:

> mimsy@plaything:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:<my essid>  Nickname: <do not recognize the nickname>
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:50:BF:B1:E0:15   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=59/92  Signal level=-33 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:36  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by Mimsy on 2007-11-13
No one?

---

### Post by intelligentfool on 2007-11-13
whats 'ifconfig' give you? sounds like an addressing/subnetting issue if your not receiving any traffic.

---

### Post by Mimsy on 2007-11-14
ifconfig returns this:

> mimsy@plaything:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:C6:88:F7  
          inet addr:192.168.63.102  Bcast:192.168.63.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fec6:88f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:719164 (702.3 KiB)  TX bytes:142074 (138.7 KiB)

eth1      Link encap:Ethernet  HWaddr 00:08:02:44:6C:80  
          inet6 addr: fe80::208:2ff:fe44:6c80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5085 (4.9 KiB)

eth1:avah Link encap:Ethernet  HWaddr 00:08:02:44:6C:80  
          inet addr:169.254.5.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


---

### Post by intelligentfool on 2007-11-14
sorry i didnt catch it before, but it looks like your WEP/WPA key got wiped or something....

> Rx invalid nwid:0 **Rx invalid crypt:36** Rx invalid frag:0

that and your wireless eth1 interface doesnt have an IP address, most likely because it cant recieve a DHCP request due to the bad key.

edit: ok, your eth1 does have an IP address, but its a private address reserved for when DHCP requests fail... 169.254.x.x
[http://en.wikipedia.org/wiki/Private_ip_address#Link-local_addresses_.28Zeroconf.29](http://en.wikipedia.org/wiki/Private_ip_address#Link-local_addresses_.28Zeroconf.29)

---

### Post by Mimsy on 2007-11-15
That's very strange. I re-entered the WEP key, and now I'm online with the laptop again, which makes me very happy. Thank you! :)

I don't suppose you have a theory on where it went? I have re-entered it several times over the past few days, in an effort to get online, without much success. At least now I know how to fix it if it happens again.

---

### Post by intelligentfool on 2007-11-16
unfortunately i dont. i'm still learning the inner workings of linux, i just happen to be a network engineer though, and networking is more or less universal. glad i could help at least find the cause.

---

