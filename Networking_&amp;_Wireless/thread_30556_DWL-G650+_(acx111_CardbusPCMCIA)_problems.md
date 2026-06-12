---
title: "DWL-G650+ (acx111 Cardbus/PCMCIA) problems"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by TheJoker on 2005-04-29
Hi everybody. 

I've recently installed Kubuntu onto my girlfriends machine and my laptop. Girlfriends machine runs like a dream, and so does my laptop, except for that I can't get my wireless network card working.

The laptop is a Sony Vaio C1-MHP (lurverly thingee!), and Kubuntu has detected most of the important things, like the external i.Link DVD/CD-R drive and sound card. It also detects the wireless card, but the setup and following steps fail.

The card is a D-Link (dlink) DWL-G650+ 54G card. I'm not that bothered if it doesn't work in 54mbps mode, as long as I get an internet connection I'm happy. Using "lspci -n" it gets identifed as 104c:9066 which, according to Craig is the acx11 Cardbus/PCI card.

I've spent quite a lot of time searching for information on how to configure this card, but the information I find is either that it works fine or unanswered questions.  :neutral: 

I did find [Craig's ACX100/111 Guide for Linux](http://www.houseofcraig.net/acx100_howto.php)  which is an excellent piece of artwork. I've followed the instructions there and compiled the latest version (acx100-0.2.0pre8_plus_fixes_54.tar.gz) of the driver. 

Everything goes well until 
```

#./start_net
=snip=
Waiting for association...10 9 8 7 6 5 4 3 2 1 .
Error failed to associate (or something - computer is disconnected at home, I'm at work :P)

``` 

Trawling through the  troubleshooting section I get to try
```
iwlist wlan0 scan
```
and the result I get is something along the lines "*no networks found*"

So, here I am...  O:)  

Anyone installed this card successfully?
With what driver? How to do it? How to configure it? Why are we here? Why am I inside when the sun is shing out there and beer is being brewed all day long, just longing for a dry throat like mine...  :roll:  :D

Any help apprecaited! Thanks!

---

### Post by FaQuid on 2005-04-29
I don't have kubuntu but ubuntu so I might be able to help a bit. My card did work but not 100% with the drivers that comes with ubuntu so I used ndiswrapper and it works as a charm. But before it worked I needed to disable the old drivers and I didn't know how but a friend helped me with that so I can't tell you how :( but here is a link to how you install DWL-G650+ with ndiswrapper: [http://www.ndeepak.info/tech/wlansarge.php](http://www.ndeepak.info/tech/wlansarge.php)

---

### Post by TheJoker on 2005-04-29
Tjenare,

[QUOTE=FaQuid]I don't have kubuntu but ubuntu so I might be able to help a bit. My card did work but not 100% with the drivers that comes with ubuntu so I used ndiswrapper and it works as a charm. But before it worked I needed to disable the old drivers and I didn't know how but a friend helped me with that so I can't tell you how :( but here is a link to how you install DWL-G650+ with ndiswrapper: [http://www.ndeepak.info/tech/wlansarge.php](http://www.ndeepak.info/tech/wlansarge.php)[/QUOTE]

Thanks for your reply. If I can't get help with the ACX drivers, I'll try the ndiswrapper path. I reckon I might get it going with that. :) Too bad I spent all evening yesterday trying to get the ACX drivers to work... ahwell...  I could boot into WinXP.... HAHAHAHA... funny... ;-)  :grin:  ;-) 

Thanks again!

---

### Post by dhanjel on 2005-05-02
Does anyone have the information on how to remove the old drivers correctly before installing ndiswrapper?

---

### Post by TheJoker on 2005-06-26
Erhmm....

I finally got round to playing with the WLAN card again. 
Having tried the ACX drivers etc, without any success I turned to NDISWrapper
and followed these instructions [http://www.ndeepak.info/tech/wlansarge.php](http://www.ndeepak.info/tech/wlansarge.php) which got me in the right direction.
After removing the old drivers and making sure that the wlan card actually used the NDISWrapper drivers things were looking up. I somehow managed to get the network up and updated the system etc, but I then turned the machine off, and the #¤%& didn't connect to the AP anymore.
I've now spent two days editing /etc/network/interfaces then doing ifup wlan0, and repeat and repeat and repeat. Sometimes I managed to get the network up, and then I rebooted, and it didn't come up again... *sigh*... Then suddenly for now apparent reason, I got the network up... 

This is in my interfaces file:

```
auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 essid "MySSID"
pre-up iwconfig wlan0 key open MY:HE:XX:WE:PP:KE:YY
wireless-essid MySSID 
```

I tried "thousands" of different combinations... and this one worked... don't know why, but it did. And I'm not going to change it! :D

I hope this might help somenoe else out there... and as for D-Link - YOU #"%¤#&)"%¤% - next  time round; release drivers for the proper OS' too! Till then; Do NOT buy any D-link products (vote with your wallet)

---

### Post by txgeek on 2005-06-26
About a month ago I started playing around with Ubuntu on an old Dell Optiplex we have at the office that I was planning on using as a web server.  I normally use Debian but wanted to try Ubuntu since a lot of the developers on the Gnome list seem to love it.  I had some problems getting java installed correctly so I took the CD home and installed it on a fairly new Dell Dimension 4600 I use as a development machine at the house.  In the machine was a D-Link DWL-G520, the PCI equivelant of the DWL-G650+.

I was suprised to find that Ubuntu Hoary detected and enabled the wireless card out of the box.  All I had to do was enter my WEP key and I was on the net.  I did some research and found that the PC-CARD version supposedly worked as well.  I have a DWL-G650 I used to use before I bought my new laptop (which came with broadcomm 802.11g), so I threw it in and booted to the Ubuntu CD.  Suprise, suprise, the pc-card was detected and worked automatically as well.

Since then I've installed Ubuntu on the laptop and have been using the Ubuntu desktop as my primary instead of the Gentoo system.  Outside of some issues with IPV6 which were resolved by switching to the OpenDNS servers I've had no problem with either wireless card.

I know this isn't much help, but thought I'd mention it.

---

