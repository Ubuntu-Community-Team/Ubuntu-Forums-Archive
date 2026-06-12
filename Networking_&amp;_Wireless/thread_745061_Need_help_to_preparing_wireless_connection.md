---
title: "Need help to preparing wireless connection"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by Mehashi on 2008-04-04
[COLOR=#ff22ff]Hey guys![/COLOR]
I am moving on monday to a new hostel, but this one has no wired broadband connection. Norwich (Where I am staying) in Norfolk has free wireless internet in the city centre, so I have bought a wireless card off of a friend. I have installed the firmware and activated the restricted driver. I need to make sure that I sort everything out now while I have wired connection as once i've moved I will not be able to come here for help unless the card works!
My problem is that where I am currently there is no wireless connection to test with, so I guess I wont know until the last moment. >:-(
When I do iwconfig I get this result, which doesnt look right to me, but I dont know what right should be?!
```

mehashi@mehashi-desu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mehashi@mehashi-desu:~$ 
```

Eth0 is my current wired connection. Any help to make sure i'm fully prepared would be appreciated! I dont want to lose you guys! >_<
Thank you!
[COLOR=#ff22ff]^_^[/COLOR]

---

### Post by superprash2003 on 2008-04-04
eth1 is your wireless card..and there seems to be a network there already called "Broadcom 4306"

---

### Post by Mehashi on 2008-04-04
I too thought it was a network, but that appears to be the name of my card I think?!
I tried...
```
mehashi@mehashi-desu:~$ sudo iwlist eth1 scan
```
and that came up with the result...
```
eth1      No scan results
```

And thats about all I know how to do...

The Access point: Invalid part of iwconfig seems out of place to me. Any knowledge there?
^_-

---

### Post by brian_p on 2008-04-04
> **Mehashi said:**
> [COLOR=#ff22ff]Hey guys![/COLOR]
I am moving on monday to a new hostel, but this one has no wired broadband connection. Norwich (Where I am staying) in Norfolk has free wireless internet in the city centre, so I have bought a wireless card off of a friend. I have installed the firmware and activated the restricted driver. I need to make sure that I sort everything out now while I have wired connection as once i've moved I will not be able to come here for help unless the card works!
My problem is that where I am currently there is no wireless connection to test with, so I guess I wont know until the last moment. >:-(
When I do iwconfig I get this result, which doesnt look right to me, but I dont know what right should be?!
```

mehashi@mehashi-desu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mehashi@mehashi-desu:~$ 
```

Eth0 is my current wired connection. Any help to make sure i'm fully prepared would be appreciated! I dont want to lose you guys! >_<
Thank you!
[COLOR=#ff22ff]^_^[/COLOR]

You need a wireless network to connect to to test. The eth1 data tells you there isn't one. But at least you do know the interface exists.

---

### Post by Mehashi on 2008-04-04
Ok, my friend now put a wireless card in his pc too, so i'm trying to make a wireless lan to test with but I cant set one up. When I look at eth1 connection I see the attached picture.
Would I be able to copy over ip settings from my wired connection? If so how should I do this? Would that be the 'access point'?
Any help appreciated, as like I say once I move if this doesnt work I wont have internet anymore! >:-(
Thank you! [color="#ff22ff"]^_^[/color]

---

### Post by brian_p on 2008-04-04
> **Mehashi said:**
> Ok, my friend now put a wireless card in his pc too, so i'm trying to make a wireless lan to test with but I cant set one up. When I look at eth1 connection I see the attached picture.
Would I be able to copy over ip settings from my wired connection? If so how should I do this? Would that be the 'access point'?
Any help appreciated, as like I say once I move if this doesnt work I wont have internet anymore! >:-(
Thank you! [color="#ff22ff"]^_^[/color]

Seems like you want to set up an ad-hoc network. I've never done one of those so cannot guide you in any detail. I can, however, give you this:

[http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)

---

### Post by ubuntu-freak on 2008-04-04
Personally, I'd do a fresh install of Ubuntu to make sure the wifi card is detected and setup correctly. With something as tempermental as a wifi card, installed after Ubuntu, I don't consider that an extreme thing to do. 
 
Nathan

---

### Post by brian_p on 2008-04-04
> **reassuringlyoffensive said:**
> Personally, I'd do a fresh install of Ubuntu to make sure the wifi card is detected and setup correctly. With something as tempermental as a wifi card, installed after Ubuntu, I don't consider that an extreme thing to do. 
 
Nathan

It's about as extreme as you can get, short of going back to Windows! modprobe should get the card recognised. Ok, setting it may  not be straight forward but the reading involved is a learning experience.

---

### Post by ubuntu-freak on 2008-04-04
> **brian_p said:**
> It's about as extreme as you can get, short of going back to Windows!

 
Is it? Doesn't take me long to install and setup Ubuntu to my liking, but I see your point.
 
Nathan

---

### Post by Mehashi on 2008-04-04
> modprobe should get the card recognised
Thanks, ill look in to this.

I have my live cd at stand by if all options are exhausted, but if that doesnt work and i have reformatted, i wont be able to use anything other than included on the live cd! Because of this it is very much a last resort. (I am used to reinstalling windows plenty and linux some, but not while staying in hostels without internet!)

I'm downloading a few extra programs to keep me busy just in case, and everything I can find to do with networking and wireless...

I hope this works *Gulp*
>.<

---

### Post by ubuntu-freak on 2008-04-04
> **Mehashi said:**
> Thanks, ill look in to this.

I have my live cd at stand by if all options are exhausted, but if that doesnt work and i have reformatted, i wont be able to use anything other than included on the live cd! Because of this it is very much a last resort. (I am used to reinstalling windows plenty and linux some, but not while staying in hostels without internet!)

I'm downloading a few extra programs to keep me busy just in case, and everything I can find to do with networking and wireless...

I hope this works *Gulp*
>.<

 
Hope it all goes well. 
 
Might be worth burning Hardy Heron, fedora and Linux Mint discs, gives you something to fall back on and test out if it all goes pear shaped with Gutsy.
 
Nathan

---

