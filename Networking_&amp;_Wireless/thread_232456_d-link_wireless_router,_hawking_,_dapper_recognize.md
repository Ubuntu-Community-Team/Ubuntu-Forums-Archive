---
title: "d-link wireless router, hawking , dapper recognizes card, can't connect, iwconfig,etc"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by cillm527 on 2006-08-08
Hello.

I'm using Ubuntu Dapper, and it recognizes my network card (i think).  But I still can't connect.

I'm pretty sure I entered all of the Networking Configuration correctly...
I entered in my ESSID and correct hex key.  I set it to DHCP, but it would turn up the "cannot connect to server" immediately in firefox.  So, I set it to a static IP, and the same thing happened, but the page stalled for much longer.

ifconfig: 

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10094 (9.8 KiB)  TX bytes:10094 (9.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:3B:02:48:CA  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig: 

```

wlan0     802.11b/g NIC  ESSID:"cillmanprop"  
          Mode:Managed  Frequency=2.442 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=4/92  Signal level=20/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:260  Invalid misc:0   Missed beacon:0

```

---

