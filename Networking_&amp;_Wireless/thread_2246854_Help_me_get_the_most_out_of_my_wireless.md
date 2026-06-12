---
title: "Help me get the most out of my wireless"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2014-10-03
I will preface this with why I am asking this question. My ISP recently upgraded our speed to 50 Mbps. I currently have a wireless a/b/g/n card on my laptop using 12.04. My router is a WRT54G. I had to upgrade my modem to a DOCSIS 3.# in order to get the 50 Mbps speed. I verified by connecting directly to the modem. The most I can get with my router is 25Mbps.

I plan on upgrading the networking equipment in the house to gigabit (switches and router), and was planning on buying an Intel card that works 'out of the box'. I then looked into what I currently have as a wireless card in the laptop. The reason is I never get above 802.11b speeds(11 Mbps). 

lspci shows that the wireless apadpter is an Qualcomm Atheros AR9287. iwconfig shows:
```
IEEE 802.11bgn  ESSID:####
          Mode:Managed  Frequency:2.437 GHz  Access Point: ####   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  

``` 
I forgot how I got the wireless working in the first place, as it was about 2 years ago, but I do remember having to take some steps in order to get it working. Could it be that I using the wrong driver for it? Theoretically, with the info given, shouldn't I be getting better speeds from the laptop?

Is there anyway to tell which driver I am using for the wireless card? Is there anything I can do in order to up my wireless speed?

Thanks in advance!

---

### Post by Bucky Ball on 2014-10-03
*Thread moved to **Networking & Wireless**.*

Possibly have more luck here.

---

### Post by weatherman2 on 2014-10-03
Start by upgrading that ancient WRT54G.  Even though it is in theory 54Mbps, in practice you will get far less than that even under ideal conditions.  (I'd hang on to it though - those things are workhorses .  You can use them for neat projects like repeaters if you put DD-WRT or TomatoUSB firmwareon them.)  Get a good 802.11n router, which has a theoretical max of 300Mbps (though again, far less in practice but probably better than the 50Mbps you need to get max speed).  If you want to spend a tad more, get an 802.11ac router ("ac" is the newest consumer wireless technology just starting to come into wide use).  You won't see a lot of benefit yet from 802.11ac but someday you will.

Meantime, if you move up to 802.11n speeds, you should get much better wireless performance.  It looks like AR9287 is only a single band 2.4GHZ 802.11n card.  So if you get a dual band 802.11n router (which can use both 2.4GHZ and a separate 5GHZ frequency for WiFi), your laptop will only be able to use 2.4GHZ.  

You may be able to upgrade the laptop wireless card to a dual band wireless card (that could do 5GHZ) - unless you have a Lenovo or HP laptop, then I wouldn't bother, because those manufacturers "whitelist" their wireless cards, making it difficult to install anything but a few "approved" cards that were sold with that model laptop.  If your laptop is a Dell, Toshiba, Acer, Sony, etc. upgrading the wireless card shouldn't be a problem as long as you can access the card physically.  Often the card is under a panel on the bottom of the laptop, and you need to unclip a couple of antenna wires then swap out the card.  In some laptops it's much harder to get to the card.

[Edit: OK, I see your laptop is an Acer - so you should not be blocked from upgrading the wireless card if you really want to.]

---

### Post by lsutiger on 2014-10-03
Thanks for your reply. I plan on upgrading everything, but just wanted to know if there is something I can do presently to get more out of what I have. Yes the WRT54G is quite a nice piece of equipment - plan on using it for something around here. I am planning on getting the Intel N 6200 for the laptop..easy replacement. As far as the router, geez...it seems like it's a crapshoot. Even the expensive good ones seem to have bad reviews. A lot of ppl say Asus, but their CS is awful, though they do have a good community (nothing like Ubuntu) to fall back upon.
How do I find out what driver the wireless card is currently using?

---

### Post by grahammechanical on 2014-10-03
> [COLOR=#000000]How do I find out what driver the wireless card is currently using?[/COLOR]

```
nm-tool
```

```
lshw -C network
```

Look for 
Driver: 
Driver=

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)


Regards.

---

### Post by weatherman2 on 2014-10-03
You can see what driver is in use for your wireless card by going to a terminal and typing:

```
sudo lshw -C network
```

but I personally doubt you're going to be able to update a driver and get any faster speeds.  Instead, try booting a Ubuntu 14.04 live USB on your laptop and check the wireless speed - which should have a much newer driver than what is installed in 12.04.  If connection speeds seem to be a lot faster, then maybe some tuning with the driver in 12.04 could help; if connection speeds are exactly the same in 14.04, I wouldn't waste your time.  But getting any decent N router should boost your connection speeds instantly.

I installed an Intel 6235 card in my Acer laptop.  It's 2x2 dual band + bluetooth and has worked beautifully for me with Ubuntu 12.04.2.  But it looks like your AR9287 is 2x2 (so it can handle two 2.4GHZ channels, up to "theoretical" 300Mbps on an N router).  Unless you want to try 5GHZ and will get a dual band router - or you want bluetooth - I wouldn't even upgrade your wireless card.  Not yet.

I have a couple of different routers I use for different functions.  I buy only routers that are supported by open source firmware like TomatoUSB or DD-WRT (lately I prefer the former but it doesn't run on as many routers - only on Broadcom-based routers).  To me, the manufacturer of the router is largely irrelevant if you install different firmware, just like Microsoft is irrelevant once you install Ubuntu.  TomatoUSB adds some neat features you won't find on consumer routers.   I find cheap Linksys/Cisco routers at local thrift stores and pick up the good ones when I find them.  The Linksys/Cisco E3000 (dual band, gigabit wired) works great with Tomato.  Also the E2500 (dual band, not gigabit) works fine for other projects.

---

### Post by varunendra on 2014-10-05
> **lsutiger said:**
> A lot of ppl say Asus, but their **CS** is awful, though they do have a good community

What is CS?

Probably 'Customer Support'...? Using shortcuts like this that are not terribly common is not a good practice either, especially when you are asking for help. ;)

By the way, who needs customer support if the piece of equipment is good. And I don't yet know of ANY reputed hardware vendor who provides good support for Linux anyway, they are all about windows. :/

I personally have found the features, capabilities and signal quality of an Asus 150N router to be far-far better than a Netgear one with equal specs, inferior features (no repeater mode, lack of some other useful features) and higher price. But that's all as far as my experience with 'testing & comparing' goes. Never used a 300Mbps or higher speed router/AP, so can't say how good the routers of that category of Asus are.

---

### Post by lsutiger on 2014-10-08
OK I am back just for a question. I am going to buy a new wireless card - a dual band card.I like the Intel N7260. Will that work out of the box?

---

### Post by weatherman2 on 2014-10-08
Some problems have been reported here with it, but others say the card works great. I've never had any problem with most of the Intel 802.11n cards I've used in Linux but I've not yet tried the N7260.

What kind of router are you buying to go with it?  It would be a shame to force that dual band ac wireless card to go the same slow G speed as your current card...

---

### Post by lsutiger on 2014-10-08
I bought the Netgear WNDR3700 - dual band a/b/g/n. The N7260 is N not AC.
Edit - just saw there is an N and AC 7260

---

### Post by jeremy31 on 2014-10-08
> **lsutiger said:**
> I bought the Netgear WNDR3700 - dual band a/b/g/n. The N7260 is N not AC.
Edit - just saw there is an N and AC 7260

The 7260 should work out of the box, for most of them.  I have 2 different models and they both worked except that I can't get the bluetooth to work on the dual-band.  Your results may vary

---

### Post by lsutiger on 2014-10-08
Thanks! I don't use bluetooth on this laptop, so I guess I will be good!

---

### Post by weatherman2 on 2014-10-08
> **lsutiger said:**
> I bought the Netgear WNDR3700 - dual band a/b/g/n.

Did it help your connection speeds vs. G?  FYI, if you use wireless security (you probably should), you need to use WPA2 + AES.  WEP, WPA, WPA2+TKIP or will force you to run down at G speeds.  

As I've said before (I think on this thread) I highly recommend the Intel 6235 card if you want to stick to 802.11n dual band.  I use bluetooth with it as well as 5GHZ.

---

### Post by lsutiger on 2014-10-08
vs. G? No, but on G it did go from 11Mbps to 16Mbps, so I got that going for me. On the wired, I am getting 62Mbps vs 25 Mbps. I will report once I get the dual band N card in. I truly appreciate your input!
Edit - Yes using WPA2 for security.

---

### Post by weatherman2 on 2014-10-08
From experience, I get 2X or more better sustained throughput with 2.4GHZ, 802.11n vs. 802.11g.  5GHZ is a little better yet.

I also use a 40MHZ channel width (which uses two channels or streams) not 20MHZ, with 802.11n (with 802.11g you could use only one).  In a very congested area with a lot of routers, 20MHZ/single channel may work better, in some cases, but you can't get the bandwidth you'd get with 40MHZ under optimal conditions.

Just remember: a dual band wireless card on your laptop connects on only one band at a time, 2.4GHZ or 5GHZ not both at the same time, so you don't get 2X connection speeds with a dual band wireless card, just the ability to use 5GHZ.  The router can do both at the same time if it is simultaneous dual-band.   Many people report less-than-expected results with 5GHZ.  I have my setup working pretty well now, but not every 5GHZ router I've used has worked very well.

---

### Post by varunendra on 2014-10-08
> **jeremy31 said:**
> The 7260 should work out of the box, for most of them.

+1

The card itself is good, whatever problems are occasionally reported, are almost always due to a firmware confusion so far easily fixable. The firmware for this device is changing really fast, hopefully getting better and better.

Just keep in mind that the "**iwlwifi**" driver used with Intel cards needs a parameter "11n_disable=8" to be manually set these days (well, quite often if not always), as mentioned in this post here : [http://ubuntuforums.org/showpost.php?p=13136253](http://ubuntuforums.org/showpost.php?p=13136253) (the option related to "*iwlmvm*" may not be related, so just ignore it).

---

### Post by Vladlenin5000 on 2014-10-09
I have one of those - 7260 - in a System76 Bonobo Extreme (v8) and it works fine, most of the times. The OS (Ubuntu 14.04 64-bit) was factory installed but as usual it's just a standard Ubuntu installation + System76's PPA for a "drivers package" that I don't really know what's in it. I'm not using it right know and I'm almost sure it runs the "iwlwifi" but I can't say whether or not with tweaks by the "manufacturer".

**Never checked for "11n_disable=8" either... What does it do exactly? I understand 0 or 1 for such switches but 8?...**

Anyway, next time with the Bonobo I'll certainly take a deeper look of what's going on under the hood.

---

### Post by jeremy31 on 2014-10-09
> **varunendra said:**
> +1

The card itself is good, whatever problems are occasionally reported, are almost always due to a firmware confusion so far easily fixable. The firmware for this device is changing really fast, hopefully getting better and better.

Just keep in mind that the "**iwlwifi**" driver used with Intel cards needs a parameter "11n_disable=8" to be manually set these days (well, quite often if not always), as mentioned in this post here : [http://ubuntuforums.org/showpost.php?p=13136253](http://ubuntuforums.org/showpost.php?p=13136253) (the option related to "*iwlmvm*" may not be related, so just ignore it).

The cards with version cb? aren't supported by the iwlwifi driver yet but with the backports and some chili555 mods even it will work

Vladlenin5000

Using that parameter with 8 enables agg TX according to modinfo but this is the post from a  bug report that I saw [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630/comments/12)

---

### Post by varunendra on 2014-10-10
> **Vladlenin5000 said:**
> **Never checked for "11n_disable=8" either... What does it do exactly? I understand 0 or 1 for such switches but 8?...**

I tried to explain it **[post=13124104]here[/post]**.

---

### Post by Vladlenin5000 on 2014-10-10
Thank you. That was quite enlightening.

---

