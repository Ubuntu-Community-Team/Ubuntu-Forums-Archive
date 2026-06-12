---
title: "ASUS PCE-AC51 WiFi doesn't work in my Ubuntu 14.04 LTS"
date: 2019-03-12
forum: Networking &amp; Wireless
---

### Post by eroa90 on 2019-03-12
I just bought this to have WiFi in my computer but I can't make it work.

Here it is my wireless info: [http://paste.ubuntu.com/p/Kj4P8BmVP7/](http://paste.ubuntu.com/p/Kj4P8BmVP7/)

Any help?

Thanks.

---

### Post by chili555 on 2019-03-12
Your wireless appears to work pretty well. It has a driver, it is connected to a wireless access point and it is even connected at 5 gHz speeds. ```

wlan0     IEEE 802.11abgn  ESSID:"MOVISTAR_D2DB"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'MOVISTAR_D2DB' [AC8]>   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-7 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```What we do see however, is that you are connected to an instance of MOVISTAR_D2DB; there are two instances with the same name available nearby. I am guessing that they are the 2.4 gHz and 5 gH segments of your own router or access point. We see your wirless dropping and reconnecting frequently and I am sure that it is annoying and troublesome. I also suspect that it is dropping to try to connect to a stronger signal.

If this is a router over which you have administrative priveleges, I strongly recommend that you rename the segments to someting like MOVISTAR_2.4 and MOVISTAR_5. Also, be certain that neither segment is set to auto channel select; fixed channels are highly recommended. Here is the 5 gH channel occupancy in your wireless_info:> 
2   APs on   Frequency:5.22 GHz (Channel 44)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      2   APs on   Frequency:5.32 GHz (Channel 64)
      2   APs on   Frequency:5.52 GHz (Channel 104)
      1   APs on   Frequency:5.56 GHz (Channel 112)
Your wireless device does these 5 gHz channels:> Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHzI suggest that you check to see if your router can be set to a fixed channel of 132, 136 or 140.

If you are unable to change the settings in the router, then you might try binding Network Manager to the MAC address of the 5 gHz segment like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Finally, Ubuntu 14.04 will go end-of-life, meaning that no new security updates will be pushed, on April 30, 2019, just a few weeks hence. I recommend that you upgrade to 18.04 LTS soon.

---

### Post by eroa90 on 2019-03-12
Hello again.

First of all, thanks for your help.

As you said, I have two segments (2.4G and 5G) in my router, but the name is not the same as you thought. Their names are MOVISTAR_D2DB and MOVISTAR_PLUS_D2DB.

At this moment I'm no longer connected with ethernet wire. Now I'm connected in the 2.4 segment (MOVISTAR_D2DB), but this wireless connection is not stable. It cames and goes and the speed when it's connected is also variable. Sometimes is difficult to navigate even.

I'm not able to connect with the 5G segment. I don't know how to do that, even in a high use channel.

At this point I just want a stable wireless connection in 2.4G, but as I said, sometimes it didn't work. Do you know what can be causing this?

Here it is another wireless info I just get: [http://paste.ubuntu.com/p/zQw4vZmkq6/](http://paste.ubuntu.com/p/zQw4vZmkq6/)

If it helps. I also have Windows installed in my computer and I have no problems to connect 2.4G segment. And gives me more speed in a quick speed test performed in google. 5G also doesn't work from my Windows OS, so I guess thats an "outside" problem.

Thanks a lot for all your help.

---

### Post by chili555 on 2019-03-12
I must respectfully disagree. Here is what your wireless_info says:> 
wlan0     IEEE 802.11abgn  ESSID:"MOVISTAR_D2DB"  
          Mode:Managed  Frequency:[COLOR="#FF0000"]5.56 GHz [/COLOR] Access Point: <MAC '[COLOR="#FF0000"]MOVISTAR_D2DB[/COLOR]' [AC1]>   
          Bit Rate=300 Mb/s   Tx-Power=26 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1040   Missed beacon:0

As well, the scanned networks are shown:> 
<snip>
MOVISTAR_D2DB:   Infra, <MAC 'MOVISTAR_D2DB' [AC2]>, [COLOR="#FF0000"]Freq 2412 MHz[/COLOR], Rate 54 Mb/s, Strength 57 WPA2
*MOVISTAR_D2DB:  Infra, <MAC 'MOVISTAR_D2DB' [AC1]>, [COLOR="#FF0000"]Freq 5560 MHz[/COLOR], Rate 54 Mb/s, Strength 57 WPA2
<snip>
The asterisk * indicates that you are connected to that segment. Please notice it is a different channel from my first reply indicating that the router is set to auto channel select. Many wireless drivers in Linux struggle to follow an ever changing channel. Please change to a fixed channel now!!!

I see nothing here that changes my recommendations above.> doesn't work from my Windows OS, so I guess thats an "outside" problem.Indeed. There are a great many things that work well in Linux but not Windows and vice-versa. It is, however, useful to know that a wireless device works in Windows; it shows clearly that the hardware is not broken. It reminds us all to check the physical layer first; that is, is the device broken, plugged in, etc.

---

### Post by eroa90 on 2019-03-17
Hi again.

I have been doing some test this week and this is what I get:

First of all, in theroy my router have two segments: MOVISTAR_D2DB (2.4GHz) and MOVISTAR_PLUS_D2DB (5GHz).

This  past days, every time I want to connect to WIFI, I have to try several  times before I can do it. A lot of times the connection doesn't work and  I wasn't able to have internet access.

But when I am able to  connect, there are three different segments, and depending which time,  it connects to one of them or another. This are the three connections I  can stablish:

MOVISTAR_D2DB (2.4GHz) - In which I am now ( [http://paste.ubuntu.com/p/gq2bdmDXTT/](http://paste.ubuntu.com/p/gq2bdmDXTT/) )
MOVISTAR_D2DB  (5GHz) - I don't understand why this is existing in the first place,  when the 5G segment should be called MOVISTAR_PLUS_D2DB.
MOVISTAR_PLUS_D2DB (5GHz)

The  problem is not just that sometimes none of this connections works.  Sometimes even when i'm able to connect, the speed is really low (6Mb/s) and i'm  not capable of use even the internet browser.

This is one example in which i'm  connected to MOVISTAR_D2DB  (5GHz) but I can do anything because of the low speed:[ATTACH=CONFIG]282804[/ATTACH]

Here it is another example, in which i'm connected to MOVISTAR_D2DB (2.4GHz) with a speed of 144 Mb/s. In this case i can navigate, but no very fast: [ATTACH=CONFIG]282805[/ATTACH]

In this last example I'm connected to MOVISTAR_D2DB  (5GHz) and speed 270 Mb/s: [ATTACH=CONFIG]282806[/ATTACH]


As you can see, all this seems weird, at lesast for me. Seems like it choose one connection randomly and connects to it.

I set channels for both segments like you recommended me, because AUTO setting can be troubling. But the problem doesn't disappear.

If you can throw some light to this I will be very grateful. Here they are some questions:

Do you know why there are 3 segments (2 with the same name) when only should be two? Is it possible that this is what it0s causing the problems?

I'm thinking in install Ubuntu 18 LTS. Do you think this could solved the problem or there are no differences in this case?

Thanks a lor for the help

---

### Post by praseodym on 2019-03-17
It loads two drivers:
```

sudo modprobe -rfv rtl8821ae 8812ae
sudo modprobe -v 8812ae
```

---

