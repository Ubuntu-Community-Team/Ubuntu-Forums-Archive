---
title: "Hsaring internet  among 1 xubuntu and two winxp home machines"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by anewbieuser on 2006-12-22
hi all,
I am completely new to xubuntu. I have installed it on a P-II 333 system with three network cards (eth0, eth1 and eth2) installed. I got internet running no problem (connected through eth0, and I am using an ADSL modem connecting to it, my ISP uses a DHCP connection) and I am planning to network it with the two other windows machines and sharing the internet connections through the Xubuntu machine at the same time (ie, the three machines can sharing files and go on-line at the same time) I am wondering if that's possible? I have been searching through the forum and didn't find something that I understand =P Anyone have similar experience with this? I hope someone will be able to give me a hand, thank you!

---

### Post by anewbieuser on 2006-12-23
hi,

I have setup a network and established ICS by viewing this post on the forum:

[http://ubuntuforums.org/showthread.php?t=91370&page=10](http://ubuntuforums.org/showthread.php?t=91370&page=10)

However, I could only get one of the connection (eth2) running. It doesn't work with eth1

Bascially, the physical setup of my network is:

www --> ADSL modem (eth0) --> Xubtunu machine (ip 192.168.0.1) with three network cards
--> (eth1) winXP ip 192.168.0.3
--> (eth2) winXP ip 192.168.0.2

I have used the following command to setup the ip addresses:

$ sudo ifconfig eth2 192.168.0.1

$ sudo ifconfig eth1 192.168.0.1

but only eth2 works, I am wondering why is that happening. Is there any additional setting to the iptable that I need to make if I want to share the internet among the three computers?.. but it seems that it should not be the problem because the computer connecting to eth1 is not showing up even on the network.

this is what shown in the terminal when I execute $ ifconfig (please note that the info for eth0 is not posted here and eth0 is my connection the a ADSL modem to the internet:

eth1 Link encap:Ethernet HWaddr 00:50:BA:5B:CC:37
          inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe5b:cc37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87896 (85.8 KiB) TX bytes:8928 (8.7 KiB)
          Interrupt:9 Base address:0x8000

eth2 Link encap:Ethernet HWaddr 00:50:BF:78:B0:FB
          inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe78:b0fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:14471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2220017 (2.1 MiB) TX bytes:11304742 (10.7 MiB)
          Interrupt:10 Base address:0xe000

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14992 (14.6 KiB) TX bytes:14992 (14.6 KiB)

another question of mine is, since I have installed three network cards on xubuntu machine with no hub connecting the the other two computers, I wondering if I can setup my network with the configuration that I currently. Please help... I have stucked in this situation for quite a while

---

### Post by 0MG on 2006-12-26
anew, you can't have multiple interfaces with the same IP address. Try changing the address of eth1 or eth2. They can't both be 192.168.0.1.

---

### Post by anewbieuser on 2006-12-26
hi, thanks alot for the reply, yeah I have been researching for a while too and I fond that I need a different IP for the other interface, I have also found that I need IP masquerade for ICS. 

I have been trying around by following this post: [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

However, I still couldn't get it work, and I have post my more details for my problem on page two of that thread, so if you don't mind, please have a look and really appreciate if you can provide me with some ideas..... Thanks alot!!!!!! Thanks you help even at this time of the year!

---

