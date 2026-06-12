---
title: "My driver seems to be working fine, but I can't see any access points"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by anonymoususername on 2006-10-30
OK, so I'm using Edgy with madwifi on an Acer Aspire 5044WLMi, as instructed by another thread here. My Wireless LED is orange, and Ubuntu recognises my card, but when I try to scan I get no results. I'm sitting right next to my Wireless router right now, and it's definately turned on, Windows can pick it up on this computer also. I think my network is open, or at least I don't need to enter any keys on Windows anyway. Anyhow, I guess I should post some more background information:

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:16:D3:47:43:89  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe47:4389/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5367093 (5.1 MiB)  TX bytes:816854 (797.7 KiB)
          Interrupt:201 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any suggestions?

---

### Post by todds on 2006-10-30
looking at your iwconfig you havent any essid id set....

sudo iwconfig ath0 essid (then you essid)

then run iwconfig

regards

todds

---

### Post by eggdeng on 2006-10-30
I have a somewhat similar problem although without the flashing lights. 

iwconfig gives me

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions

sudo ifup wlan0 gives

ifup: interface wlan0 already configured

So it looks to me like everything is working but just not finding the network?

---

### Post by eggdeng on 2006-11-01
I managed to get my wireless sorted. If you still have a problem after setting the essid, it may have to do with the channel / frequency. My device was scanning for the AP on channel 0 or 2.412 GHz (like yours). However the router was broadcasting on channel 11 or 2.462 GHz.
I used:

sudo iwconfig wlan0 freq 2.462G

to change the channel and finally picked up the AP. [You would need to put ath0 where I put wlan0.] 
I got this from a hot-shit walkthrough at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), which also has loads of other useful stuff.
Once I had the AP detected, I had to set up static IPs to get ping & internet working, but I haven't really looked into that thoroughly. Apart from that, the only drawback is having to change the channel again every time I reboot.
Hope this helps. Good luck.

---

