---
title: "suggestions for using xbox as wireless media player"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by keratos on 2008-11-28
hi

just wondering what people's view was on how best to setup a wireless media network within my home.

this is the kit that i have:

1. linux PC running ubuntu situated in home office.
2. xbox (the 'old' one - not 360) with modchip and stock 20GB HDD. this is situated in the home living room.
3. 2 wireless routers.

what i would like to do is stream video from the PC to the xbox, wireless, and play on my TV.

the PC is connected to one wireless ADSL router. I have a DSL wireless 4 port router free to use. 

have seen these "xbox adaptors" for around 35GBP but was wondering whether I could use the free wireless router I have to connect the xbox to the wireless LAN.

not sure how best to do this. One issue springs to mind and that is that the two routers would be on different SSIDS? is this the case?

if I could, I would like to connect the PC in the office to one wireless router (well infact it is already connected and working) and connect the xbox to the second router and somehow attach this to the wirless LAN.

can this be done, how?

also, its some years since I've done this but I remember having to get hold of a CD image to boot from on the xbox and install some new S/W in order that XBMC can be loaded.

Does anyone recall how to do this , I've forgot.

thanks in advance
D

---

### Post by lenswipe on 2008-11-29
> **keratos said:**
> hi

just wondering what people's view was on how best to setup a wireless media network within my home.

this is the kit that i have:

1. linux PC running ubuntu situated in home office.
2. xbox (the 'old' one - not 360) with modchip and stock 20GB HDD. this is situated in the home living room.
3. 2 wireless routers.

what i would like to do is stream video from the PC to the xbox, wireless, and play on my TV.

the PC is connected to one wireless ADSL router. I have a DSL wireless 4 port router free to use. 

have seen these "xbox adaptors" for around 35GBP but was wondering whether I could use the free wireless router I have to connect the xbox to the wireless LAN.

not sure how best to do this. One issue springs to mind and that is that the two routers would be on different SSIDS? is this the case?

if I could, I would like to connect the PC in the office to one wireless router (well infact it is already connected and working) and connect the xbox to the second router and somehow attach this to the wirless LAN.

can this be done, how?

also, its some years since I've done this but I remember having to get hold of a CD image to boot from on the xbox and install some new S/W in order that XBMC can be loaded.

Does anyone recall how to do this , I've forgot.

thanks in advance
D


You can have 2 wireless routers on the same network, although i dont think you can pair them together wirelessly, but if you give them differnet LAN IP addresses and then connect them both via ethernet cable, that should work :)

They will need different IPs though, eg

router#1: 192.168.1.1
router#2: 192.168.1.2

like that


hope this helps

-L

---

### Post by keratos on 2008-11-29
thanks for that.

i actually think I need them pairing.

i definitely need wireless. cable is not an option.

the objective is to stream media from a PC to the Xbox over wireless.

I have a spare wireless router and thought maybe I could connect that to the xbox with a short patch lead.

perhaps not?

---

### Post by odinb on 2008-11-29
Duplicate, just ignore.

---

### Post by odinb on 2008-11-29
Hi Keratos!

You need to set up the second W-Router as a bridge:
[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

For booting/reinstalling your Xbox, you need either the old classic slayers evox installer, 2.7 is the latest, and it is from 2006, or the newer AIDeluxe (auto installer deluxe). The latest is from July of this year.
Both can be found on bittorrent search engines.
Remember to burn on CD-RW at the slowest speed your burner can handle, or to DVD. If not you will have problems booting from the media.

Good luck!

---

### Post by keratos on 2008-12-04
thanks odinb.

What I want to do here is have a single LAN with two wireless AP on it. Any client connected to either AP can 'see' any other client and/or be routed out to the net.

I managed to get hold of some 'C' code for telnetenable and compile it. This opened up telnet ports on my Netgear WGT624. The WGT624 has four operating modes:

AP
Client
Bridge
Repeater

I tried Client which would not allow any wireless connections from laptop or Xbox.

Bridge didnt seem to work at all ... the WGT624 could not 'see' anything.

I had intermittent success with Repeater mode. Only WEP seemed to work .. any other security option seemed to lock out the router.

Didnt try AP.

What I am looking for here I guess is :

a)How do I need to set these two routers up such that:
- both act as Access Points.
- both are on the same subnet (i.e. 192.168.0.x) single shared LAN
- all internet traffic is routed via the DG834
- the WGT624 acts as a "slave" to the "master" DG834.


anyone ?

---

### Post by mantelo on 2008-12-05
Hi Keratos,

I was reading about the AP option in the Netgear router (I have a 614), and it seems that only works if both router are Netgear. In such a case, one would be configured as "base station" and the other would be the repeater.

Anyway, a workaround for your problem would be using a separate wireless card in your PC, connecting the second router to the Xbox and hooking your second wi-fi card to it with a different SID and network. If you need to access the internet from the Xbox, you'll have to configure your adapters to bridge.

good luck!

---

### Post by keratos on 2008-12-07
two networks...but that is not what I require see first post.

there must be a way.

incidentally, I have some progress...

the router connected to the xbox is configured as a client and is communicating with the other router connected to the PCs on the LAN. all is okay except that the xbox router is not accepting wireless connections. I wanted to extend the range of the wireless LAN using this as a repeater , but I cant get it to work.

Does anyone know how to setup a netgear WGT624 as a repeater?

---

