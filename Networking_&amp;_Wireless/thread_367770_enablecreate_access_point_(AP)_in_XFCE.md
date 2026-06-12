---
title: "enable/create access point (AP) in XFCE"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by miky on 2007-02-22
Hello world! (by the way, why are people using this sentence in many HowTo s or scripts? :-)

I use one PC for connection to the internet and then share the connection among LAN, all works fine so far. I do have here also wifi card and want to make access point (AP) for sharing internet connection through it too. I have installed my card so ubuntu can see it
```

# dmesg | grep wlan
 [17179602.504000] wlan0: ethernet device 00:13:d4:44:c2:46 using NDIS driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
 [17179602.504000] wlan0: encryption modes supported: WEP; TKIP with WPA
 [17179607.652000] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

I have tried to google out answer for my question, but non of them help me, or help me not completely. I found that network-manager and network-manager-gnome is great solution for my problem, but it does not work. I have Xubuntu edgy, so XFCE. those programs are said to work on xfce too...they are supposed to appear as that small icons in area which i do not know name of (next to clock, you know what i mean).
i tried to 
 ```

#NetworkManager
#NetworkManagerDispatcher

``` 
but it did nothing
```

#iwconfig
> lo        no wireless extensions.
> 
> eth0      no wireless extensions.
> 
> eth1      no wireless extensions.
> 
> wlan0     IEEE 802.11b  ESSID:off/any
>           Mode:Managed  Channel:0  Access Point: Not-Associated
>           Bit Rate:54 Mb/s   Sensitivity=-200 dBm
>           RTS thr:2346 B   Fragment thr:2346 B
>           Encryption key:off
>           Power Management max timeout:0us  mode:All packets received
>           Link Quality:0  Signal level:0  Noise level:0
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
> 
> nas0      no wireless extensions.
> 
> sit0      no wireless extensions.
> 
> ppp0      no wireless extensions.
#ifconfig
> wlan0     Link encap:Ethernet  HWaddr 00:13:D4:44:C2:46
>           inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
>           UP BROADCAST MULTICAST  MTU:1500  Metric:1
>           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
>           collisions:0 txqueuelen:1000
>           RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
>           Interrupt:10 Memory:ff8b0000-ff8c0000
> 

```
seams like it is on, but do not even try to send sth like to scan the arae...ping or whatever

anythig i forgot to mention?
please, be patient with me, still new with this stuff
Thanks a lot for any advice
miky

---

### Post by miky on 2007-02-22
anyway, is it possible, that my driver does not support creating AP?
i was trying to follow those steps [http://www.linux.com/article.pl?sid=06/07/10/1729226]("http://www.linux.com/article.pl?sid=06/07/10/1729226")
but i can't set
#iwconfig wlan0 mode master
it gives me
```

$ sudo iwconfig wlan0 mode master
 Error for wireless request "Set Mode" (8B06) :
 SET failed on device wlan0 ; Invalid argument.

```

how to check it?

---

