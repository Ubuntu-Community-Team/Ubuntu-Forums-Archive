---
title: "Bridging USB Tether to Ethernet Connection for PS4"
date: 2020-03-07
forum: Networking &amp; Wireless
---

### Post by oddlybrewed on 2020-03-07
Hello,

This is my first time on the forums and while I have done a little bit of research, knowing my luck there is a duplicate of this issue so sorry in advance!  Please bear with my noobness....

So **my overall goal right now is to gain better internet connectivity to my PS4**.  My current living condition requires me to use my phone for internet so I generally have my Android based phone connected to my laptop with Ubuntu Studio 18.04 using the EasyTether app (on my phone) and the easytether interface (the makers of the app, MobileStream, required their program to be downloaded and installed on my laptop in order for it to interface properly, I can provide the steps I did to do so if it's relevant.

So before you say why don't you just try x,y,z:
1. The EasyTether app lets me use my usb tethering functionally without any major hindrances from my cell phone's service provider (yeah I still get throttled to hell and back but it's manageable in my area during certain times)

2. I have used my phone as a wifi hotspot for my PS4 and it works but my cell phone provider limits hotspot with a hard data cap that can't be bypassed (trust me I've tried with many apps like FoxFi and the like lol).

3. **My current solution is to tether my phone to my laptop through usb, have my laptop emit a hotspot wifi signal with internet sharing and have my PS4 connect to that which I have had success with, but the degradation of the signal causes my speeds to be just slow enough that my PS4 thinks it doesn't have an internet connection (due to consecutive timeouts) even though I can access the web on the PS4 just fine....it basically prevents me from using the internet to download system/game updates and access certain network features, it's silly I know. ** Even worse is that when I connect my phone to a strong wifi signal at my university for internet instead of through my cell phone service provider, the speeds there are so great that this setup works fine and my PS4 sees that it does in fact have an internet connection (my PS4 can't connect to their wifi devices so yeah I still have to make my laptop the hotspot, also I would like to not have to go to my university lugging around my PS4 every time I need to do a system/game update lol)

**I believe that bridging my usb internet connection to ethernet and having that connect to my PS4 will increase my speeds significantly to the point where I won't have the timeout issue as often.** While I know there are going to be those people that will just say "get better internet", I would like to at least try this first.

One strange thing about the way the usb tether is setup on my computer is that it doesn't show up on my Network Connections manager but does show up under Connection Information.  I've install the bridge-utils and while I'm able to add my ethernet connection (eth0) to the bridge just fine when I try to add my usb connection (tun-easytether) it says it's an Invalid argument: ```
# brctl addif br0 tun-easytether
can't add tun-easytether to bridge br0: Invalid argument

```

My list of network interfaces is (when I type ifconfig): ```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 10:1f:74:1d:9e:70  txqueuelen 1000  (Ethernet)
        RX packets 728  bytes 84315 (84.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 163  bytes 32097 (32.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4845  bytes 450515 (450.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4845  bytes 450515 (450.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun-easytether: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 192.168.117.0  netmask 255.255.255.254  destination 192.168.117.1
        inet6 fe80::6cc9:70f9:ab3d:3110  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 500  (UNSPEC)
        RX packets 18500  bytes 17479627 (17.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 12905  bytes 1503650 (1.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 60:d8:19:0c:11:8e  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)

```

Do I have to configure the tun-easytether interface to have a certain property in order for me to add it? And if so how would I do it? I noticed it doesn't have a MAC address and have no clue how to fix that...I'm terrible when it comes to networking if you couldn't tell....

---

### Post by oddlybrewed on 2020-03-15
Welp posting guidelines have no problems with bumping if there are no answers and I haven't gotten any new views or answers in a week....so.....bump.

I did manage to figure out how to connect my PS4 directly to my university's wifi but yeah....still trying to bridge my connection here at home via ethernet and usb tethering...

---

### Post by oddlybrewed on 2020-03-15
Soooo._._messing around after I bumped the thread._.I got it working!! Well not using the bridge util but simply going into the edit connections gui for Ubuntu Studio, edited the ethernet connection to my PS4 by making the IPv4 and IPv6 set to shared to other computers (my PS4 is on and not configured for lan yet), and then going to my PS4 and set up internet for lan using the easy method.  I'm not sure if it was order of events that wasn't making this work or me deleting  the orional ethernet connection after numerous failed attempts but fyi I DID TRY THIS BEFORE with shared to other computers and it didn't work (I couldn't see my usb tether in the edit connections/network manager gui as I stated before so I assumed there was no conventional way to enable connection sharing for it).  So as a bit of cartharsis, I'm writing this via my PS4 web browser while finally letting it download updates as well as KH1.5&KH2.5 in 5hrs instead of 5 weeks (well PS4 said 99+ hours and then promptly fails due to a timeout).  :guitar: Feels good...

---

### Post by Ihatethiscomp on 2020-07-24
> **oddlybrewed said:**
> Soooo._._messing around after I bumped the thread._.I got it working!! Well not using the bridge util but simply going into the edit connections gui for Ubuntu Studio, edited the ethernet connection to my PS4 by making the IPv4 and IPv6 set to shared to other computers (my PS4 is on and not configured for lan yet), and then going to my PS4 and set up internet for lan using the easy method.  I'm not sure if it was order of events that wasn't making this work or me deleting  the orional ethernet connection after numerous failed attempts but fyi I DID TRY THIS BEFORE with shared to other computers and it didn't work (I couldn't see my usb tether in the edit connections/network manager gui as I stated before so I assumed there was no conventional way to enable connection sharing for it).  So as a bit of cartharsis, I'm writing this via my PS4 web browser while finally letting it download updates as well as KH1.5&KH2.5 in 5hrs instead of 5 weeks (well PS4 said 99+ hours and then promptly fails due to a timeout).  :guitar: Feels good...

Hey, I'm trying to do this with a router. Is it possible that you can look to see what the Auto settings in your PS4 ended up getting configured to?

---

