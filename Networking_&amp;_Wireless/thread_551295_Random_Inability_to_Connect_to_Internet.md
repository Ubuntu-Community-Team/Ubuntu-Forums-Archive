---
title: "Random Inability to Connect to Internet"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Claude on 2007-09-15
Wireless or wired, I am randomly unable to connect to the Internet, however, I can always connect to my network.

DHCP on Wired - Built-in drivers 
Roaming on Wireless - [These wireless drivers]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated/")

Modem/Router is a 2Wire 2700HG-D

In Windows, i can always connect no problem - so i think its a problem from within Ubuntu.

---

### Post by Claude on 2007-09-15
...

---

### Post by Claude on 2007-09-16
..

---

### Post by noob12 on 2007-09-16
You may have flaky DNS service.  You can see if this HOWTO helps:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by NightCrawler03X on 2007-09-16
As root (su, then type root password), type "iwconfig" and "ifconfig". Then, copy pasta the results here, so we know what we are dealing with.

Also, copy pasta the text from your /etc/network/interfaces file onto this thread.

NOTE
Before you do the, issue (as root) the following:
iwlist scanning
This is fro wireless networking, and if it shows results (i.e. essids+access-points), then your card is working, in which case you specify (as root) "iwconfig your-config essid your-essid" and "ifup your-config".

Seeing your actual settings would be useful if we are to diagnose your problem.

---

### Post by Claude on 2007-09-16
claude@claude-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"LAUDEWIRE"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:3F:B6:8E:91   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:7658-9432-31   Security mode:open
          Link Quality=75/100  Signal level=-53 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:149  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

claude@claude-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7B:A2:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:7E:A7:D7:A5  
          inet addr:192.168.0.65  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fea7:d7a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9348 errors:0 dropped:312 overruns:0 frame:0
          TX packets:10692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2991571 (2.8 MiB)  TX bytes:1042254 (1017.8 KiB)
          Interrupt:4 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:7B:A2:7D  
          inet addr:169.254.8.10  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:279 (279.0 b)  TX bytes:279 (279.0 b)

---

### Post by NightCrawler03X on 2007-09-16
Ok, your radio channel (IEEE 802.11b/g) is functioning, you are connected to your essid, have an access point.

Try "sudo ifup" then go on firefox and try to access a web page.
If that does not work, yo umay have to manually edit your /etc/network.interfaces file.
Show us the content of your /etc/network/interfaces file please.

It could also be (forgive me if I'm wrong, I **use** to use ubuntu, but now use PCLinuxOS) that you haven't configured your network in ubuntu's network config.
I think it's on your ubuntu menu, in "system>adminstration>network". When you find that, try configing it there.

Again, show us (in this thread) all of the results of you doing these things.

---

