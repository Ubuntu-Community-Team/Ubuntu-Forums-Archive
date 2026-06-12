---
title: "Wireless stops working but says it is connected"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by c_squisher on 2008-09-07
I can connect to my wireless network without any problem, but after some use everything stops working: web pages won't load, IM won't work, downloads stop but I'm told that I'm still connected to my network in the top panel.
It seems to stop working more quickly when I'm downloading more, and will only start working again when I re-boot.

I looked at the Ubuntu help and followed the steps:

ifconfig shows me I have an "inet addr" under the "wlan0" heading.
I tried pinging to 82.211.81.158 (as told in the troubleshooting) and I get a line repeated that suggested to me that it wasn't working, though I can't remember what it said off-hand.
I then tried pinging to [www.ubuntu.com](www.ubuntu.com) (as told) and it failed.
Finally I used the command "cat /etc/resolv.conf" which told me the ip of my router.

Well that's all the information I think will be relevant I can think of, but please ask if you need anything else to work on.
Cheers, guys.

---

### Post by Lex_x64 on 2008-09-13
I feel your pain c_squisher; as I have the same problem. I can get it to work again for a short period of time by manually configuring the wireless; then letting it autodetect when it craps out again. I'm still searching for answers myself but will mark this post to let you know if I find anything.

---

### Post by kakyoism on 2008-09-13
I have the exact same problem.
And that's why i'm here!!!!!!

---

### Post by xaenyx on 2009-01-12
Bumping an old thread.

I have the same exact problem.  Are there any fixes?

---

### Post by superprash2003 on 2009-01-12
post output of the following when wireless stops working
1)ifconfig
2)ping google.com

---

### Post by pvilleSE on 2009-01-12
I am also having the same issue.  I'm using a Gateway T-1628 running 8.10 fully up to date.  It does appear to be based on how much data you are pulling over your connection.  I was randomly checking pages over the last 45 min. and it kept working fine and then I began to watch a video and it quickly stopped working.  I closed the video and tried to load a very basic page and nothing.  I did the ifconfig and ping google.com and then while still recieving data from the ping tried to reload a web page and it is working again.  Then while trying to send the output from ifconfig in an email it stopped working again.  I have this issue on both an open wireless network and a 64-bit WEP enabled wireless network.  Steps that I can usually take to get it working are:
disable wireless, enable wireless, open connection editor and edit the connection I appeared to be connected to and then it reconnects.

Thanks for any help.  Here is my output.  

Here is my ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:03:25:5a:03:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52589 (52.5 KB)  TX bytes:52589 (52.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:16:44:ad:06:f5  
          inet addr:10.102.1.108  Bcast:10.102.255.255  Mask:255.255.0.0
          inet6 addr: fe80::216:44ff:fead:6f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5024399 (5.0 MB)  TX bytes:958399 (958.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-AD-06-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Here is the google.com ping output:
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=240 time=111 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=240 time=110 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=6 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=7 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=8 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=11 ttl=240 time=89.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=12 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=13 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=14 ttl=240 time=94.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=15 ttl=240 time=110 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=16 ttl=240 time=113 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=17 ttl=240 time=111 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=18 ttl=240 time=118 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=19 ttl=240 time=101 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=20 ttl=240 time=118 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=21 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=22 ttl=240 time=96.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=23 ttl=240 time=128 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=24 ttl=240 time=98.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=25 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=26 ttl=240 time=101 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=28 ttl=240 time=93.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=29 ttl=240 time=98.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=30 ttl=240 time=92.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=31 ttl=240 time=89.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=32 ttl=240 time=115 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=33 ttl=240 time=100 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=34 ttl=240 time=96.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=35 ttl=240 time=94.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=36 ttl=240 time=92.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=37 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=38 ttl=240 time=116 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=39 ttl=240 time=100 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=40 ttl=240 time=106 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=41 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=42 ttl=240 time=96.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=43 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=44 ttl=240 time=115 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=45 ttl=240 time=106 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=46 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=47 ttl=240 time=98.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=48 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=49 ttl=240 time=98.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=50 ttl=240 time=93.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=51 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=52 ttl=240 time=87.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=53 ttl=240 time=92.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=54 ttl=240 time=99.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=55 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=56 ttl=240 time=111 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=57 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=58 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=59 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=60 ttl=240 time=116 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=61 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=62 ttl=240 time=95.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=63 ttl=240 time=97.9 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=64 ttl=240 time=114 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=65 ttl=240 time=100 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=66 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=67 ttl=240 time=121 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=68 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=69 ttl=240 time=114 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=70 ttl=240 time=91.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=71 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=72 ttl=240 time=91.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=73 ttl=240 time=88.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=75 ttl=240 time=90.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=76 ttl=240 time=100 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=77 ttl=240 time=95.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=78 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=79 ttl=240 time=88.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=80 ttl=240 time=90.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=81 ttl=240 time=90.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=82 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=83 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=84 ttl=240 time=116 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=85 ttl=240 time=88.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=86 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=87 ttl=240 time=87.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=88 ttl=240 time=97.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=89 ttl=240 time=94.9 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=90 ttl=240 time=117 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=91 ttl=240 time=93.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=92 ttl=240 time=98.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=93 ttl=240 time=2067 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=94 ttl=240 time=1066 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=95 ttl=240 time=106 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=96 ttl=240 time=89.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=97 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=98 ttl=240 time=98.9 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=99 ttl=240 time=92.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=100 ttl=240 time=109 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=101 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=102 ttl=240 time=92.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=103 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=104 ttl=240 time=92.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=105 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=106 ttl=240 time=101 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=107 ttl=240 time=108 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=108 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=109 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=110 ttl=240 time=85.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=111 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=112 ttl=240 time=96.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=113 ttl=240 time=92.9 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=114 ttl=240 time=90.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=115 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=116 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=117 ttl=240 time=91.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=118 ttl=240 time=96.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=119 ttl=240 time=91.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=120 ttl=240 time=119 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=121 ttl=240 time=121 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=122 ttl=240 time=93.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=124 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=125 ttl=240 time=89.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=126 ttl=240 time=94.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=127 ttl=240 time=94.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=128 ttl=240 time=105 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=129 ttl=240 time=96.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=130 ttl=240 time=110 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=131 ttl=240 time=89.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=132 ttl=240 time=113 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=133 ttl=240 time=98.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=135 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=136 ttl=240 time=93.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=137 ttl=240 time=95.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=138 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=139 ttl=240 time=92.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=140 ttl=240 time=98.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=141 ttl=240 time=93.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=142 ttl=240 time=89.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=143 ttl=240 time=102 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=144 ttl=240 time=117 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=145 ttl=240 time=100 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=146 ttl=240 time=108 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=147 ttl=240 time=92.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=148 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=149 ttl=240 time=93.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=151 ttl=240 time=96.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=152 ttl=240 time=94.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=153 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=154 ttl=240 time=98.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=155 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=156 ttl=240 time=93.1 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=157 ttl=240 time=87.2 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=158 ttl=240 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=159 ttl=240 time=107 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=160 ttl=240 time=118 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=161 ttl=240 time=110 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=162 ttl=240 time=98.0 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=163 ttl=240 time=94.9 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=164 ttl=240 time=98.4 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=165 ttl=240 time=103 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=166 ttl=240 time=98.5 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=167 ttl=240 time=91.3 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=169 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=170 ttl=240 time=113 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=172 ttl=240 time=112 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=173 ttl=240 time=96.6 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=175 ttl=240 time=111 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=176 ttl=240 time=108 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=178 ttl=240 time=90.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=179 ttl=240 time=115 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=180 ttl=240 time=98.7 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=181 ttl=240 time=96.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=182 ttl=240 time=100 ms
From pvillese-linux-laptop.local (10.102.1.108) icmp_seq=212 Destination Host Unreachable
From pvillese-linux-laptop.local (10.102.1.108) icmp_seq=213 Destination Host Unreachable
From pvillese-linux-laptop.local (10.102.1.108) icmp_seq=214 Destination Host Unreachable
From pvillese-linux-laptop.local (10.102.1.108) icmp_seq=215 Destination Host Unreachable

--- google.com ping statistics ---
215 packets transmitted, 169 received, +4 errors, 21% packet loss, time 296448ms
rtt min/avg/max/mdev = 85.303/119.445/2067.460/167.749 ms, pipe 3

---

### Post by superprash2003 on 2009-01-14
if you are able to ping a website but not open it , then its mostly a DNS issue.. try changing your dns servers to opendns. their ips are 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

