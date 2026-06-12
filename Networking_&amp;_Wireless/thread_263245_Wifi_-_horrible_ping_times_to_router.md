---
title: "Wifi - horrible ping times to router"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by dwoloz on 2006-09-22
I have a Presario 900 with a Netgear WG511T PCMCIA card

I get a connection to my router but the ping times are awful.  Ranges from 1ms up to 2000ms.  Transferring files is incredibly slow.

Is there anything I can do?
Im pretty much a newbie so I may be overlooking something


Thanks in advance for any help

---

### Post by wieman01 on 2006-09-22
Do you use a firewall by change (e.g. Firestarter)? And what card are you using?

---

### Post by tagra123 on 2006-09-22
I get a similar problem with the belkin card I'm using: fd5XXX recognized as a Ralink RT2500 802.11g.

It's usable just very slow.

The ethernet transfer time for about a 500MB file take 30 seconds. A similar size file on the wireless is taking 3 to 5 minutes.

---

### Post by wieman01 on 2006-09-22
> **tagra123 said:**
> The ethernet transfer time for about a 500MB file take 30 seconds. A similar size file on the wireless is taking 3 to 5 minutes.
Now that is no surprise, buddy. Wireless is considerably slower than Ethernet. One reason being that wireless allows 50 MBit at max if you happen to have wireless g, and Ethernet usually runs at 100 MBit.

Plus wireless is subject to noise, closed doors, bad weather, etc. Don't expect the same performance as with Ethernet.

---

### Post by dwoloz on 2006-09-23
> **wieman01 said:**
> Do you use a firewall by change (e.g. Firestarter)? And what card are you using?

I do not believe Im using a firewall.  The installation is the default Ubuntu (is firewall on by default?)

The card is a Netgear WG511T

---

### Post by wieman01 on 2006-09-23
Well... Just a question before we try anything "sophisticated"... Have you tried moving the router closer to your computer?

And is there a chance that you are pinging one of your neighbors' router rather than your own? Happens...

---

### Post by dwoloz on 2006-09-23
> **wieman01 said:**
> Well... Just a question before we try anything "sophisticated"... Have you tried moving the router closer to your computer?

And is there a chance that you are pinging one of your neighbors' router rather than your own? Happens...


Im connected to my own router and its sitting about a foot away from the card right now

Im a newbie to Linux but not to computers

---

### Post by wieman01 on 2006-09-23
> **dwoloz said:**
> Im connected to my own router and its sitting about a foot away from the card right now

Im a newbie to Linux but not to computers
Ok, meant no offense but sometimes the answers are as obvious as that. :-)

Can you execute the following 2 commands and post the output (using a terminal):
> iwlist <your_wireless_device> scan
> iwconfig
You can highlight the output in the terminal with your mouse to copy and then press the scroll-wheel to paste.

Please also show us the contents of the "interfaces file":
> gedit /etc/network/interfaces
That'll help.

---

### Post by dwoloz on 2006-09-23
Output of iwlist scan (sure are a lot of APs
```
ath0      Scan completed :
          Cell 01 - Address: 00:18:3F:67:49:F1
                    ESSID:"2WIRE258"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0C:41:B3:B9:58
                    ESSID:"dclemensen"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:15:E9:D1:BC:88
                    ESSID:"dlink"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:12:88:BD:3B:89
                    ESSID:"2WIRE687"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:16:B6:DC:71:7F
                    ESSID:"Julia"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:D0:9E:F5:63:B9
                    ESSID:"2WIRE351"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:18:3F:9B:D7:31
                    ESSID:"2WIRE322"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 08 - Address: 00:14:95:0B:86:91
                    ESSID:"2WIRE474"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:14:6C:19:9D:94
                    ESSID:"SPACEMONKEY"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 10 - Address: 00:14:6C:13:FD:32
                    ESSID:"UnderwearGoesInsideThePants"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2
          Cell 11 - Address: 00:14:6C:95:01:AC
                    ESSID:"Timon & Pumba"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f20 20000
```

Our AP is "SPACEMONKEY"




Output of iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SPACEMONKEY"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:19:9D:94
          Bit Rate:24 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
          Rx invalid nwid:123  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


Contents of interfaces file
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid SPACEMONKEY

auto wlan0
iface wlan0 inet dhcp
```





Thank you for your help, I appreciate it

---

### Post by wieman01 on 2006-09-23
This does not look good:
> Rx invalid nwid:123  Rx invalid crypt:0  Rx invalid frag:0
The "nwid" value is kind of high.

Can you also post this please:
> gedit /etc/resolv.conf
If you're using DHCP there is a possibility that your system does not set the DNS server correctly. Have you tried changed playing around with your routers settings? E.g. beacon interval, fragmentation threshold.

I suspect it has to do with the routers configuration.

---

### Post by wieman01 on 2006-09-23
Perhaps you are too close to the router... My "nwid" value is 0.

---

### Post by dwoloz on 2006-09-23
/etc/resolv.conf contains:
```
nameserver 192.168.1.1
```

Ive moved the laptop around and I still get lagged ping times

---

### Post by wieman01 on 2006-09-23
I think it's not an issue with Ubuntu but the router. Did you have the same problem under Windows?

---

### Post by wieman01 on 2006-09-23
You could try static IPs... That's worth a try, perhaps there is an issue with DHCP. You can config this using the Gnome networking application.

---

### Post by dwoloz on 2006-09-23
Interesting

I disabled the routers feature for 108mbps connections and pings are now much more reasonable.  It ocassionally spikes as high as 14ms but most are within 1-3ms

I never had this problem in Windows but I suppose the Netgear driver coped with this feature where the Linux driver does not

---

### Post by wieman01 on 2006-09-23
108 mbps... Wow, hell-of-a router. :-) Yes, this could be the issue because your wireless card is a Wireless G (54 mbps), correct?

Glad you solved it, buddy. :-)

---

### Post by dwoloz on 2006-09-23
Both the card and router are 108mbps capable (at least in marketing terms).  They were sold as a bundle.
The Netgear driver Im assuming has to be used for this functionality though.

Thanks for sorta guiding me to the answer :)

Hope maybe someone else out there who comes across this problem will find this solution

---

### Post by wieman01 on 2006-09-23
> **dwoloz said:**
> Both the card and router are 108mbps capable (at least in marketing terms).  They were sold as a bundle.
The Netgear driver Im assuming has to be used for this functionality though.

Thanks for sorta guiding me to the answer.
Wecome.

The problem could lie with the RT2500 Linux driver (RT2500 **[COLOR="Red"]802.11g[/COLOR]**). I don't think it supports 108 MBit at the moment. That's why it says "wireless G"... So it IS a Linux problem after all! ;-)

Nice talking to you. Learned a lot today.

---

### Post by tagra123 on 2006-09-23
> **wieman01 said:**
> Now that is no surprise, buddy. Wireless is considerably slower than Ethernet. One reason being that wireless allows 50 MBit at max if you happen to have wireless g, and Ethernet usually runs at 100 MBit.

Plus wireless is subject to noise, closed doors, bad weather, etc. Don't expect the same performance as with Ethernet.


I will partially agree but it stand to reason if 100MBit connection can transfer the 500MB file in 30 seconds shouldn't the 54MBit transfer the same file in about 60 seconds.

The router and computer in question are aless than 10 feet (same room) from each other with nothing that should be causing interference.

My real question is would I get better performance with ndiswrapper and where do I blacklist the rt2500

---

### Post by puppy on 2006-09-23
I'm pretty sure I know *exactly* what the problem is.

I haven't been able to get wireless working in linux yet (the os can "see" my router by scanning but I can't connect... anyways)

Under windoze, at default my wireless network card had "RTS" and "Fragment" settings (these may have other names on your card) of 2347 (the range goes from 256-2347). With these two set at 2347 I was getting pings of anything from 50 - 2500ms ping!!!

When I changed *both* of these to 256 I then got pings from <1ms to 2ms every time. I don't know how you get to these settings on the card in linux unfortunately (if you find out please tell me as I will need to sort this out soon)

I hope you manage to sort it out

---

### Post by Starlight on 2006-09-23
Hi! I think I have a similar problem, but I can't change anything in the wireless router, because it belongs to the ISP and it's on another building... So I think the only way to fix it would be to find those "RTS" and "Fragment" settings which puppy posted in the post above... but I don't know where to look for them...

---

### Post by puppy on 2006-09-23
Sorry, just to clarify they are settings for the wireless card - I now have wireless and am searching for a solution to exactly the same problem - ping to router varies from between <1ms to 100ms  :(   Gaming is impossible :-({|=

---

### Post by wieman01 on 2006-09-23
The point of this thread was that this problem is hardly software/driver/Linux problem but has to do with the router's settings. Dwoloz could resolve the issue by limiting the router's transfer rate to 54 MBit, but there are other settings you can play with as well.

---

### Post by Starlight on 2006-09-24
> **puppy said:**
> Sorry, just to clarify they are settings for the wireless card - I now have wireless and am searching for a solution to exactly the same problem - ping to router varies from between <1ms to 100ms  :(   Gaming is impossible :-({|=
For me, ping to router varies between <1 ms and 2500 ms...  But only on Linux. I have no problem with browsing websites, but it's impossible to play most games. :(

> **wieman01 said:**
> The point of this thread was that this problem is hardly software/driver/Linux problem but has to do with the router's settings. Dwoloz could resolve the issue by limiting the router's transfer rate to 54 MBit, but there are other settings you can play with as well.
Unfortunately, I can't change any settings in the router, so I hope there are some settings I can change on my computer to make it work better...

---

### Post by tagra123 on 2006-09-24
The problem is not limited to this router, I have a belkin with the same problem as before.

As I said before I can live with it, but would not consider it to be working corectly.When a 54Mbit is 5 to 6 times slower than the lan cable. Shouldt it be closer to 2 times slower?

The internet works correctly, very fast, but network transfers are slow and ping times too. I think it is a ubuntu/linux problem or at least a settings  problem.

---

### Post by wieman01 on 2006-09-24
> **tagra123 said:**
> The problem is not limited to this router, I have a belkin with the same problem as before.

As I said before I can live with it, but would not consider it to be working corectly.When a 54Mbit is 5 to 6 times slower than the lan cable. Shouldt it be closer to 2 times slower?

The internet works correctly, very fast, but network transfers are slow and ping times too. I think it is a ubuntu/linux problem or at least a settings  problem.
Do router & wireless network card run on the same bit rate (e.g. 54 MBit)? If not put them in sync for a minute & check if the performances improves.

---

### Post by tagra123 on 2006-09-24
I have the router set to "g" only that would be 54 I believe. In my network setup "/etc/network/interfaces"

Here are the settings except mine are set to static:

[http://ubuntuforums.org/showpost.php?p=1538590&postcount=15](http://ubuntuforums.org/showpost.php?p=1538590&postcount=15)

---

### Post by wieman01 on 2006-09-24
> **tagra123 said:**
> I have the router set to "g" only that would be 54 I believe. In my network setup "/etc/network/interfaces"

Here are the settings except mine are set to static:

[http://ubuntuforums.org/showpost.php?p=1538590&postcount=15](http://ubuntuforums.org/showpost.php?p=1538590&postcount=15)
Is your network card wireless G as well? Or B?

---

### Post by tagra123 on 2006-09-25
> **wieman01 said:**
> Is your network card wireless G as well? Or B?

The wireless card is g too.

I can get good speed through the internet, its the computer to computer that slows the speed down. I really don't get it. It just seems like it should be faster.

Heres a good example.

I have aptproxy set up so I only have to download programs for updates once. Right now the normally slow computer is running 30 to 52 kB/s doing an update through the aptproxy on the same machine I use mainly as a general purpose server -- its also the mythtv backend.

Now normally on the ethernet computers this would be closer to 96 to 124 (about the max speed of my actual internet conection.
So I'm getting what I expect  aptproxy runs through http and as I said http actions seem to be much faster. 

Now switch over to NFS or samba and the speed falls to a crawl.

My ping times are not awful, but the NFS and even Samba are just seeming to be slower then others on this machine. 

I believe it should be faster.

---

### Post by tagra123 on 2006-09-25
wieman01

Could you help us help the person in this forum. I've exhausted my ideas.

[http://ubuntuforums.org/showthread.php?t=263543](http://ubuntuforums.org/showthread.php?t=263543)

---

### Post by Starlight on 2006-09-26
so... does anyone know how to fix the really high pings to router without changing any settings in the router?

---

### Post by wieman01 on 2006-09-26
> **Starlight said:**
> so... does anyone know how to fix the really high pings to router without changing any settings in the router?
I am afraid this is a dead-end.

---

