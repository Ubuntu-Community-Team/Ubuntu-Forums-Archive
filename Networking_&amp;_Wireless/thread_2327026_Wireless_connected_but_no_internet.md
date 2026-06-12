---
title: "Wireless connected but no internet"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by alessandro38 on 2016-06-07
Hi all,

I have an issue with one specific wireless network at my workplace. I'm able to connect to it, but then I have no internet. Other wireless networks such as my home network are working properly, it's just this one I'm having troubles with.
The network itself works, because other people here are able to navigate using it.

I'm on Ubuntu 16.04 LTS. The IPv6 setting for that network is set to "Ignore".

```
$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr 9c:5c:8e:40:52:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:70656 (70.6 KB)  TX bytes:70656 (70.6 KB)


wlp3s0    Link encap:Ethernet  HWaddr b0:c0:90:2c:94:ca  
          inet addr:10.127.0.77  Bcast:10.127.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b2c0:90ff:fe2c:94ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80050 (80.0 KB)  TX bytes:52983 (52.9 KB)

```

```
$ iwconfig
enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:"xxx"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: E4:F4:C6:0F:D1:10   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ ping google.it
ping: unknown host google.it

```

Before writing here I've been through a bunch of possible resolutions found on this forum but none worked so far (unfortunately I can't link them because I was browsing from my mobile and I didn't bookmarked them). Thanks in advance for your help.

---

### Post by alessandro38 on 2016-06-07
Yesterday, it seemed nobody had a solution for this on the internet. Today, the first google search I did after opening this thread solved my issue.
My solution has been to install a Realtek driver according to the answer to this post: [http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem](http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem)

---

### Post by winecoding on 2016-06-07
Hi alessandro38, I also posted a thread related to wireless connection, [http://ubuntuforums.org/showthread.php?t=2326900](http://ubuntuforums.org/showthread.php?t=2326900)   My problem is that I can ping an IP address like 8.8.8.8  but I cannot ping google.com , which will have ping: unknown host google.com   Do you have the similar problem? Any suggestions are very appreciated.

---

