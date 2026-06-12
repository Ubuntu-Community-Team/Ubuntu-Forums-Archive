---
title: "Wireless randomly renews IP"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by ZeroYuy on 2007-10-30
Okay..This is REALLY strange, and I only found it via watching my system log. I'm, for all intent and purposes, a Ubuntu newbie. I'm not new to computers though. I fail networking like a noob but I do know a few things. I'm running DHCP, and I know that it should not renew until A: I tell it to or B: Something else does (normally, the timeout on the lease). I tried Static, but for some reason, it STILL uses DHCPRELEASE, and tries to renew the IP without ANY noticeable cause cause.

Okay, so I looked at a couple of threads, and looked at the info they provided. Soo..

This comes from lsmod |grep at76 (I'm using an at76 adapter, Belkin FD5060 to be exact, I think.)
```

at76_usb               95076  0 
usbcore               134280  3 at76_usb,uhci_hcd

```

This is the information about my computer:
```

Linux PenPen 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

```

And this is what happens. Just remember, I do NOT use the ifup/ifdown commands, and do not use any type of network manager to take it down/bring it back up.
```

Oct 29 23:22:24 PenPen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 29 23:22:27 PenPen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 29 23:22:32 PenPen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct 29 23:22:41 PenPen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 29 23:22:51 PenPen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 29 23:22:51 PenPen ntpdate[12920]: step time server 91.189.94.4 offset 0.003233 sec
Oct 29 23:22:55 PenPen dhclient: No DHCPOFFERS received.
Oct 29 23:22:55 PenPen dhclient: No working leases in persistent database - sleeping.

```

I just noticed it's doing this on my built in wired card, eth0, which is disconnected. Not my main, wlan0. But however, it still crashes my wlan0 while it does it.

Sorry if I've been overly noobish or anything with this. I'm still trying to learn. Four or five years on windows and just about six months ago I was able to switch. I REALLY love Ubuntu and I'd hate to have to move to another Linux OS or, even worse, more to Windoze again. So I'd really appreciate any help anyone can give me.

Here's a little more, from my ifconfig and iwconfig, respectively. (I've removed my IP's, just for my own security's sake.)
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:41:E6:40:9D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8090 (7.9 KiB)  TX bytes:8090 (7.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:30:BD:64:1A:A6  
          inet addr:***.***.*.*  Bcast:***.***.*.*  Mask:255.255.255.0
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:1050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:610508 (596.1 KiB)  TX bytes:127371 (124.3 KiB)

```

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Belkin_G_Plus_MIMO_E25D53"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:E2:5D:53   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=38/100  Signal level=38/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by ZeroYuy on 2007-10-31
Well..It's been a day or two, so I assume that it isn't completely against the rules to bump this thread so that it can move back to the top?

I'm getting pretty discouraged. I know I probably didn't put things right but even someone who just wants me to put it a different way to make it easier to understand would be nice..I'm starting to fear I may have to leave Ubuntu, for the fact I can't get my internet to function properly.

It IS a pain to have to click the connect button every three or four page laods..

---

### Post by ZeroYuy on 2007-11-02
So here again, I had no luck with the above methods and I'm starting to get very discouraged. I've spent an hour looking at the forums, and looking at topics that seemed to have something relative, but really didn't. I've gotten as far as getting this from dmesg |grep wlan0

```

[   22.012000] ubuntu/wireless/at76/at76c503.c: wlan0 disconnecting
[   22.428000] ubuntu/wireless/at76/at76c503.c: registered wlan0
[   34.088000] ubuntu/wireless/at76/at76c503.c: wlan0: ignored AuthFrame in state 0

```

However, before it was complaining about a time-out. I restarted and lost most of that part. I also get this with dmesg |grep wireless

```

[   22.428000] ubuntu/wireless/at76/at76c503.c: registered wlan0
[   24.460000] ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[   25.936000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[   34.088000] ubuntu/wireless/at76/at76c503.c: wlan0: ignored AuthFrame in state 0
[   36.116000] ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[   37.624000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[ 2215.200000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[ 3237.796000] ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[ 3239.272000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[ 3722.836000] ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[ 3724.328000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed
[ 4509.336000] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed

```

I really need some help now..I'm actually considering going back to windows because I can't keep working like this.

---

### Post by chiques on 2007-11-17
Make sure your wifi adapter is configured to connect to your router. I was getting this error because for some reason my ssid and my key got wiped out. I re-entered the information and I booted right up.

---

