---
title: "Can't access internet using firefox, epiphany, or chromium"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by bledsoe on 2010-06-25
Not long after updating one of my desktop PCs to 10.04, I opened my firefox browser and was confronted with a screen that said "The connection was reset".  Every website I try gives me the same error.  My email client, Thunderbird, seems to work just fine, however; I have three IMAP accounts and I can send/receive/view messages on all of them with no problem.

I used the Ubuntu Software Center to download and install the Epiphany and Chromium browsers, but neither of them will display a website, either.  Chromium tells me "This web page is unavailable" and Epiphany just sits there displaying a little spinning wheel icon.

FWIW, I have another desktop PC with Ubuntu(10.04)/Firefox and it's working fine.  I also have a Toshiba netbook with Ubuntu Netbook Remix and Firefox, and it's working fine.  The PC in question will also boot to Windows/Firefox and it's working fine.

Any suggestions greatly appreciated.  Thanks in advance.

---

### Post by mk1w86 on 2010-06-25
Does the machine connect to the internet via wireless?

Could you please post the output of:

```
ifconfig
```

---

### Post by Windows Nerd on 2010-06-25
In addition to above, can you ping Google or any other site?

```
 ping -c 5 www.google.ca
```

---

### Post by bledsoe on 2010-06-25
Hi, and thanks for the replies.

mk1w86, yes, this machine connects via a wireless card.  Here's the output from the ifconfig command:

homer@homer-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:22:19:2c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56294 (56.2 KB)  TX bytes:56294 (56.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:93:92:79  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe93:9279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112103 (112.1 KB)  TX bytes:30153 (30.1 KB)

Windows Nerd, here's the output from the ping command:

homer@homer-desktop:~$ ping -c 5 [www.google.ca](www.google.ca)
PING [www.l.google.com](www.l.google.com) (74.125.159.99) 56(84) bytes of data.
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_seq=1 ttl=52 time=21.8 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_seq=2 ttl=52 time=32.3 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_seq=3 ttl=52 time=24.0 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_seq=4 ttl=52 time=20.8 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_seq=5 ttl=52 time=21.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4011ms
rtt min/avg/max/mdev = 20.823/24.022/32.387/4.333 ms

Hope this helps,

---

### Post by bodhi.zazen on 2010-06-25
Your internet connection seems fine.

what is in /etc/resolv.conf ?

did you configure a firewall ?

---

### Post by bledsoe on 2010-06-25
oh. yeah.

The "Did you configure a firewall" question reminded me that a while back I installed fireHOL and played around with it a little before abandoning it, and then promptly forgetting about it.  It was still installed, however, and apparently when I upgraded to 10.04, something broke or didn't get updated or something.

So I uninstalled fireHOL, restarted the computer, and presto, all my browsers work just fine.

Thanks to all for the assistance,

---

