---
title: "3G mobile Broadband connected but cannot surf"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by estanlow on 2008-06-17
Hi,

I am a Ubuntu(Hardy) user at home, Windows XP/Kubuntu(Hardy) user at work. I started using 3G mobile broadband few days ago. The USB Modem is Samsung Z800, works fine in Windows XP. As for ubuntu/kubuntu the initial setup is ok, able to connect but I cannot surf the internet.

I google for solutions, try different settings for wvdial.conf, /etc/ppp/options, try using gnome-ppp and Kppp still unable to surf the internet. Below are the information from Ubuntu/Kubuntu and Windows XP.

_Information_

***Ubuntu/Kubuntu***
```
~$lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Bus 001 Device 001: ID 0000:0000

~$cat /etc/wvdial.conf
[Dialer SingTel]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 921600
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99**1*1#
Password = ''
Username = '65IDEAS'
Carrier Check = no
Stupid Mode = on

~$egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
noipx
replacedefaultroute

~$sudo wvdial SingTel
SingTel 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99**1*1#
--> Waiting for carrier.
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jun 16 20:26:07 2008
--> Pid of pppd: 15697
--> Using interface ppp0
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]
--> local  IP address 10.111.18.25
--> pppd: (©[06][08]È©[06][08]
--> remote IP address 10.64.64.64
--> pppd: (©[06][08]È©[06][08]
--> primary   DNS address 165.21.100.88
--> pppd: (©[06][08]È©[06][08]
--> secondary DNS address 165.21.83.88
--> pppd: (©[06][08]È©[06][08]
--> pppd: (©[06][08]È©[06][08]

~$ifconfig
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.111.18.25  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:4 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1311 (1.2 KB)  TX bytes:2191 (2.1 KB)

~$tracepath [www.google.com](www.google.com)
1:  10.111.18.25 (10.111.18.25)                            0.205ms pmtu 1500
 1:  10.110.0.1 (10.110.0.1)                              289.168ms asymm  2 
 1:  10.110.0.1 (10.110.0.1)                              297.388ms asymm  2 
 2:  10.110.0.12 (10.110.0.12)                            287.724ms 
 3:  no reply
 4:  165.21.95.150 (165.21.95.150)                        286.606ms 
 5:  GE-1-1-0.bishan.singnet.com.sg (165.21.12.36)        316.049ms asymm  7 
 6:  203.208.192.221 (203.208.192.221)                    288.931ms asymm  8 
 7:  ge-1-0-0-0.sngtp-dr1.ix.singtel.com (203.208.173.133) 319.022ms asymm  9 
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 
```

***Windows XP***
```
>ipconfig
PPP adapter Z800 RAS Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.111.2.207
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.111.2.207
        DNS Servers . . . . . . . . . . . : 165.21.100.88
                                            165.21.83.88
        Primary WINS Server . . . . . . . : 10.11.12.13
        Secondary WINS Server . . . . . . : 10.11.12.14
        NetBIOS over Tcpip. . . . . . . . : Disabled

>tracert [www.google.com](www.google.com)
Tracing route to [www.l.google.com](www.l.google.com) [209.85.175.104]
over a maximum of 30 hops:

  1   622 ms   119 ms   129 ms  10.110.0.1
  2    90 ms   109 ms    99 ms  10.110.0.12
  3    98 ms     *        *     58.185.62.109
  4    99 ms    99 ms   110 ms  165.21.95.150
  5    93 ms    99 ms   109 ms  GE-0-1-0.bishan.singnet.com.sg [165.21.12.100]
  6    82 ms    99 ms    99 ms  203.208.192.221
  7    85 ms    99 ms   119 ms  ge-0-0-0-0.sngtp-dr1.ix.singtel.com [203.208.149.78]
  8    92 ms    99 ms    99 ms  203.208.169.34
  9    79 ms   129 ms   109 ms  209.85.254.166
 10   138 ms   149 ms   159 ms  209.85.241.221
 11   150 ms   159 ms   159 ms  209.85.250.101
 12   149 ms   199 ms   169 ms  209.85.252.65
 13   141 ms   149 ms   159 ms  tc-in-f104.google.com [209.85.175.104]

Trace complete.
```

[ATTACH]74440[/ATTACH]
Windows XP HSDPA Connection Manager info

[ATTACH]74441[/ATTACH]
Windows XP HSDPA Connection Manager info

[ATTACH]74442[/ATTACH]
Windows XP Modem Configuration

[ATTACH]74443[/ATTACH]
Windows XP Advanced Security Settings

Any pointers?

Though I can live without 3G broadband for Ubuntu/Kubuntu, I am pissed at stumbling in what seems to be the last hurdle. It will bring me great satisfaction in solving this obstacle. Thanks in advance!

---

### Post by estanlow on 2008-06-22
Well, the issue seems to be solved for unknown reasons. Thanks guys and gals for taking the time to read my post.

---

