---
title: "unable to connect BSNL broadband modem through wifi"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by sjalan on 2010-05-02
I am new to Linux. I have a BSNL broadband modem (Indian) and I am able to connect it through wire. On wired connection, Internet is running fine.But as soon as I switch to wireless option, it detects the modem and gets connected to it, but don't go any further. That means it doesn't connect to Internet through that modem. I am having Windows-XP also on the same laptop and Internet is running fine on that in wireless mode. I think it must be something very small but tricky:confused:
I have searched a lot on Internet but all in vain.
Please help me out with this as I am stuck and no professional help is available here.

Thanks in advance

sjalan

---

### Post by dineshs on 2010-05-03
Are you able to ping your modem when ethernet cable is removed?(ie via wireless)?Assuming that the modem IP is 192.168.1.1
```
ping 192.168.1.1
```

---

### Post by sjalan on 2010-05-03
yes, it seems so
this is the output I am getting

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.41 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.19 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.93 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.53 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.86 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=3.25 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=1.72 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=3.61 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=3.10 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=1.79 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1.79 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=1.58 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=1.58 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=2.91 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=1.55 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=1445 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=437 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=1.49 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=1.58 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=3.34 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=2.69 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=64 time=1.56 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=64 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=64 time=1.87 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=64 time=3.05 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=64 time=1.56 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=46 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=47 ttl=64 time=1.69 ms
64 bytes from 192.168.1.1: icmp_seq=48 ttl=64 time=2.34 ms
64 bytes from 192.168.1.1: icmp_seq=49 ttl=64 time=2.34 ms
64 bytes from 192.168.1.1: icmp_seq=51 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=52 ttl=64 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=64 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=55 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=57 ttl=64 time=6.98 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=59 ttl=64 time=1.72 ms
64 bytes from 192.168.1.1: icmp_seq=60 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=61 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=62 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=63 ttl=64 time=1.56 ms
64 bytes from 192.168.1.1: icmp_seq=64 ttl=64 time=1.90 ms
64 bytes from 192.168.1.1: icmp_seq=65 ttl=64 time=5.10 ms
64 bytes from 192.168.1.1: icmp_seq=67 ttl=64 time=1.87 ms
64 bytes from 192.168.1.1: icmp_seq=68 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=69 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=70 ttl=64 time=2.79 ms
64 bytes from 192.168.1.1: icmp_seq=71 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=72 ttl=64 time=3.82 ms
64 bytes from 192.168.1.1: icmp_seq=73 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=74 ttl=64 time=2.67 ms
64 bytes from 192.168.1.1: icmp_seq=75 ttl=64 time=2.69 ms
64 bytes from 192.168.1.1: icmp_seq=76 ttl=64 time=2.69 ms
64 bytes from 192.168.1.1: icmp_seq=77 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=78 ttl=64 time=2.67 ms
64 bytes from 192.168.1.1: icmp_seq=79 ttl=64 time=2.18 ms
64 bytes from 192.168.1.1: icmp_seq=80 ttl=64 time=1.89 ms
64 bytes from 192.168.1.1: icmp_seq=81 ttl=64 time=1.89 ms
64 bytes from 192.168.1.1: icmp_seq=82 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_seq=83 ttl=64 time=1.89 ms
64 bytes from 192.168.1.1: icmp_seq=84 ttl=64 time=2.22 ms
64 bytes from 192.168.1.1: icmp_seq=85 ttl=64 time=2.41 ms
64 bytes from 192.168.1.1: icmp_seq=86 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=87 ttl=64 time=3.72 ms
64 bytes from 192.168.1.1: icmp_seq=88 ttl=64 time=3.64 ms
64 bytes from 192.168.1.1: icmp_seq=89 ttl=64 time=2.20 ms
64 bytes from 192.168.1.1: icmp_seq=90 ttl=64 time=2.06 ms
64 bytes from 192.168.1.1: icmp_seq=91 ttl=64 time=1.89 ms
64 bytes from 192.168.1.1: icmp_seq=92 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=93 ttl=64 time=1.82 ms
64 bytes from 192.168.1.1: icmp_seq=94 ttl=64 time=1.75 ms
64 bytes from 192.168.1.1: icmp_seq=95 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=96 ttl=64 time=11.0 ms
64 bytes from 192.168.1.1: icmp_seq=97 ttl=64 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=98 ttl=64 time=1.82 ms
64 bytes from 192.168.1.1: icmp_seq=99 ttl=64 time=2.60 ms
64 bytes from 192.168.1.1: icmp_seq=100 ttl=64 time=1.80 ms
64 bytes from 192.168.1.1: icmp_seq=101 ttl=64 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=102 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=103 ttl=64 time=1.55 ms
64 bytes from 192.168.1.1: icmp_seq=104 ttl=64 time=1.79 ms
64 bytes from 192.168.1.1: icmp_seq=105 ttl=64 time=1.69 ms
64 bytes from 192.168.1.1: icmp_seq=106 ttl=64 time=1327 ms
64 bytes from 192.168.1.1: icmp_seq=107 ttl=64 time=327 ms
64 bytes from 192.168.1.1: icmp_seq=108 ttl=64 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=109 ttl=64 time=2.82 ms
64 bytes from 192.168.1.1: icmp_seq=110 ttl=64 time=1.56 ms
64 bytes from 192.168.1.1: icmp_seq=111 ttl=64 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=112 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=113 ttl=64 time=3.18 ms
64 bytes from 192.168.1.1: icmp_seq=114 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=115 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=116 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=117 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=118 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=119 ttl=64 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=120 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=121 ttl=64 time=2.57 ms
64 bytes from 192.168.1.1: icmp_seq=122 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=123 ttl=64 time=1.81 ms
64 bytes from 192.168.1.1: icmp_seq=124 ttl=64 time=2.09 ms
64 bytes from 192.168.1.1: icmp_seq=125 ttl=64 time=2.23 ms
64 bytes from 192.168.1.1: icmp_seq=126 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=127 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=128 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=129 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=130 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=131 ttl=64 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=132 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=133 ttl=64 time=2.55 ms
64 bytes from 192.168.1.1: icmp_seq=134 ttl=64 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=135 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=136 ttl=64 time=1.57 ms
64 bytes from 192.168.1.1: icmp_seq=137 ttl=64 time=2.66 ms
64 bytes from 192.168.1.1: icmp_seq=138 ttl=64 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=139 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_seq=140 ttl=64 time=1.81 ms
64 bytes from 192.168.1.1: icmp_seq=141 ttl=64 time=1.78 ms
64 bytes from 192.168.1.1: icmp_seq=142 ttl=64 time=1.93 ms
64 bytes from 192.168.1.1: icmp_seq=143 ttl=64 time=2.66 ms
64 bytes from 192.168.1.1: icmp_seq=144 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=145 ttl=64 time=2.74 ms
64 bytes from 192.168.1.1: icmp_seq=146 ttl=64 time=2.66 ms
64 bytes from 192.168.1.1: icmp_seq=147 ttl=64 time=2.67 ms
^C
--- 192.168.1.1 ping statistics ---
147 packets transmitted, 145 received, 1% packet loss, time 146256ms
rtt min/avg/max/mdev = 1.492/26.513/1445.187/167.087 ms, pipe 2


But how can one be sure that my OS is connected to my modem only?
I am raising this doubt because it seems when I ran this ping my system was catching some other broadband network also. I am very much confused.

Please help me.

Sjalan

---

### Post by dineshs on 2010-05-04
open browser and type 192.168.1.1 on the address bar and hit enter.
You will be prompted to enter a user id and password
type [COLOR="Blue"]admin[/COLOR] for both
You will get a modem menu.Does it match with the model you have?
Also pl let me know which modem you are using(model name) and how you are connecting in windows.(do you use a pppoe connection that stores username and password)

---

### Post by sjalan on 2010-05-04
I am having modem ZXDSL 531B.
After connecting to 192.168.1.1, it is showing the same model name.
Let me tell u, one more interesting thing which is happening, that my laptop is connecting to Internet using someone else's BSNL network in range, in wireless mode. Currently, I am writing to you using that network only.
I checked the settings of that network and found just one difference that of security key.
I disabled my security option and then tried again but of no use.

Sounds very strange, isn't it?

Pls let me know how to resolve this? I am badly stuck in it.

Thanks in advance,
sjalan

---

### Post by sjalan on 2010-05-04
And yes, I am using a pppoe connection that stores username and password in windows XP.
Thankful to you for your help.
sjalan

---

### Post by dineshs on 2010-05-05
Try disabling Wireless option in the other modem(untick enable wireless)and apply.Are you able to use your modem now?

---

### Post by sjalan on 2010-05-08
Actually I tried it through pppoeconf, and it started, but now the problem is of speed. I checked iwconfig and it was 1M there, so tried sudo iwconfig wlan0 rate 54M.

I found these solutions from some of the older thredas posted here.
But still the speed is very slow.
seems to be an endless procedure to fix it.

Thanx in advance

sjalan

---

### Post by dineshs on 2010-05-09
If there is a delay in pages getting loaded I think it is a DNS issue.What is the speeed when you try this
[www.speakeasy.net/speedtest](www.speakeasy.net/speedtest)
and what is in
```
cat /etc/resolv.conf
```

---

### Post by dmdfoss on 2010-08-04
Hello friends
I have  BSNL EVDO MMX 300C HSIA USB Modem and working on Ubuntu 10.04.
When connect this modem to my Labtop, It is not connect...
I have a following output.....
dmd@dmd-laptop:~$ lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 05c6:2001 Qualcomm, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:01a2 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Please help
...DMD

---

### Post by dineshs on 2010-08-04
Did you try configuring the connection via Network Manager?
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab mobile broadband -add ...
If there is no progress start a new thread with the output of the following command when modem is connected and ON
```

dmesg | grep -e "modem" -e "tty"
```
You may read this guide by alexfish 
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

---

