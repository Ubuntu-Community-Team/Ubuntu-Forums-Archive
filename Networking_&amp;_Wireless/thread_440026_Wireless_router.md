---
title: "Wireless router"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by carbonrodney on 2007-05-11
Hello,

I want to buy a router to maintain a network at home and connect to the internet at the same time. I see a list of supported wireless cards, but I want a compatible wireless router, that will be wired to this computer (it dual-boots Fiesty and XP).
Which routers are smoothly compatible with ubuntu?

---

### Post by wieman01 on 2007-05-11
> **carbonrodney said:**
> Hello,

I want to buy a router to maintain a network at home and connect to the internet at the same time. I see a list of supported wireless cards, but I want a compatible wireless router, that will be wired to this computer (it dual-boots Fiesty and XP).
Which routers are smoothly compatible with ubuntu?
Nearly all commercial routers there are... simply because they rely on standard protocols that all wireless card do comply with. So there is little risk of making the wrong choice.

I can recommend Linksys' WRT54G router which is inexpensive, does both Wireless G + B and has good support for wireless security (i.e. WPA2, WPA, WEP, etc.). You can even use it for DynDNS and others dynamic IP sites. I like it a lot.

---

### Post by chili555 on 2007-05-11
All of the usual suspects, Linksys, Belkin, Netgear, etc., work just fine. The protocols, TCP/IP, FTP, SSH, etc. are the same for everyone. Either Linux correctly follows the protocol, and it does, or it does not and nothing works. The router and wireless adapter manufacturers *must* comply exactly to the protocol so your Linksys card and my Netgear card work in the coffee shop that uses a Belkin router.

Actually, Linksys routers, and possibly many others, run on Linux!

---

### Post by matthew on 2007-05-11
> **wieman01 said:**
> I can recommend Linksys' WRT54G router which is inexpensive, does both Wireless G + B and has good support for wireless security (i.e. WPA2, WPA, WEP, etc.). You can even use it for DynDNS and others dynamic IP sites. I like it a lot.I have one (version 2) that works great. I put a third party firmware on it that I am very impressed with called [DD-WRT]("http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F").

---

### Post by wieman01 on 2007-05-11
> **matthew said:**
> I have one (version 2) that works great. I put a third party firmware on it that I am very impressed with called [DD-WRT]("http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F").
Ah... heard about it as well, Matthew. Somebody said that DD-WRT's QoS is highly efficient, I am very keen on checking it out. How hard was it for you to enable wireless & wireless security? Have you tried QoS by chance?

I am sidetracking, but this is very much in favor of WRT54G (whatever version). :-)

---

### Post by mohnkern on 2007-05-11
The only comment I'd make about the Linksys WRT54G is the built in firmware no longer supports port redirect (the old ones did, and removing a feature is really annoying).

The wrt54G does still support forwarding, which is not bad.

Why is this important?

You may decide you want to run a web server, or several web servers on your home network, and access them from the outside.  With port redirect, you could just tell the router if it was on port X at your router, forward it to port 80 on machine X.  That way you don't have to actually mess with your server configuration, you just configure it at the router level, and then connect through the new port.

---

### Post by matthew on 2007-05-11
> **wieman01 said:**
> Ah... heard about it as well, Matthew. Somebody said that DD-WRT's QoS is highly efficient, I am very keen on checking it out. How hard was it for you to enable wireless & wireless security? Have you tried QoS by chance?

I am sidetracking, but this is very much in favor of WRT54G (whatever version). :-)Everything works quite easily including configuring/enabling QoS, wireless security, or increasing the output power. Stability and speed weren't bad with the LinkSys firmware, but they seem to be improved as well.

---

### Post by carbonrodney on 2007-05-24
Thanks for the replies...

WRT54G you say... So, does it support port forwarding? (this is actually highly desirable).

Will DD-WRT enable this?

---

### Post by wieman01 on 2007-05-25
> **carbonrodney said:**
> Thanks for the replies...

WRT54G you say... So, does it support port forwarding? (this is actually highly desirable).

Will DD-WRT enable this?
Both the original firmware as well as DD-WRT support port forwarding, no problem.

---

### Post by wieman01 on 2007-06-04
Just to say thank you once again, Matthew. You pointed me in the right direction (together with Dmize in another thread). I have replaced the firmware with DD-WRT yesterday which took me about 60 minutes including all security & networks settings that I needed.

--
In order  to close this thread and say a few words concerning [DD-WRT]("http://www.dd-wrt.com/dd-wrtv2/index.php"): It's simply terrific.

Before I had the firmware replaced and while I was running Linksys' native firmware that had come with the router, I had serious troubles browsing and Skype'ing while I was using BitTorrent and listening to Internet radio, etc.

After installing DD-WRT all these troubles belong in the past, I can now happily browse the web, do Skype, radio streaming, and BitTorrent all at the same time. No disruption at all.

DD-WRT rocks... that's all I can say. QoS is very easy to configure and just works. I was deeply impressed.

---

### Post by matthew on 2007-06-04
> **wieman01 said:**
> Just to say thank you once again, Matthew.
You are very welcome. I'm glad to hear it is working well for you!

---

### Post by wieman01 on 2007-06-04
> **matthew said:**
> You are very welcome. I'm glad to hear it is working well for you!
May I ask... What's the feature you like most about it?

---

### Post by matthew on 2007-06-04
> **wieman01 said:**
> May I ask... What's the feature you like most about it?Two things sold me on it; stability and the ability to change the power settings.

The QoS settings are useful, for the reason you described--assigning priority to specific software processes in order to keep the quality high on high-bandwidth-required things like VOIP. It's also cool to have the ability to enable ssh and use that to tunnel into the router and configure it from the command line if desired. I honestly don't use that feature much, but it's nice to have it.

---

### Post by bvanaerde on 2007-06-04
I thought of buying the Linksys WRT54G... nice to hear the positive reactions about it :)

---

### Post by wieman01 on 2007-06-04
> **bvanaerde said:**
> I thought of buying the Linksys WRT54G... nice to hear the positive reactions about it :)
Well, the firmware that comes with the router is pretty useless. But as you can see there are options. Install DD-WRT instead and it will turn into a fairly pleasant experience.

---

### Post by bvanaerde on 2007-06-04
> **wieman01 said:**
> Install DD-WRT instead and it will turn into a fairly pleasant experience.
What difference will this make? A new web interface with more options?

I'm not sure if I understand the advantages of using another firmware...

---

### Post by wieman01 on 2007-06-04
> **bvanaerde said:**
> What difference will this make? A new web interface with more options?

I'm not sure if I understand the advantages of using another firmware...

Yes, probably a greater number of useful options. But then the question is whether you need them or not. QoS is certainly quite helpful when it comes to using VOIP and Internet streaming. See for yourself.

---

### Post by bvanaerde on 2007-06-16
Ok, I bought the WRT54G today.
Everything works, no problem at all.

But... it seems I've got v7... and it's not possible to use DD-WRT on this version.
Seems a bit weird to me though. I mean, it's exactly the same router, only a different firmware version, right?
So when I overwrite the firmware with a 3rd party firmware, it doesn't really matter what the original firmware was. [Click here for more info]("http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE#h31") (scroll down to compatibility). It seems my version uses a different chipset.

I'm a bit angry about it... you can't see on the box what version it is.

Everything works, so it's not that bad. But I just like to use it to the fullest :)

---

### Post by wieman01 on 2007-06-16
> **bvanaerde said:**
> Ok, I bought the WRT54G today.
Everything works, no problem at all.

But... it seems I've got v7... and it's not possible to use DD-WRT on this version.
Seems a bit weird to me though. I mean, it's exactly the same router, only a different firmware version, right?
So when I overwrite the firmware with a 3rd party firmware, it doesn't really matter what the original firmware was. [Click here for more info]("http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE#h31") (scroll down to compatibility). It seems my version uses a different chipset.

I'm a bit angry about it... you can't see on the box what version it is.

Everything works, so it's not that bad. But I just like to use it to the fullest :)
Can't you just ask them for a replacement? Would be a shame if you could not use DD-WRT.

---

