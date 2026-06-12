---
title: "Driver for Netgear WG511v2 PC card (Ubuntu 5.04)"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by Gwilym ab Ioan on 2005-10-17
Equipment: Old Time Laptop with Pentium 300Mhz (odd) PSU. 128Mb RAM a Hoary something or other Distro (Ubuntu 5.04) a Netgear WG511v2 PCI WiFi card a Netgear DG834Gv2 Router & three other PCs working perfect well with XP Pro Operating Systems on the same LAN.

I've just installed my first Ubuntu Distro (5.04). How the hell do I get the (Netgear) wireless network card to talk to my OS & connect up to my LAN? I've hunted for info, Netgear doesn't seem to have heard of Linux! Less still provide drivers for Linux based OSs.

All the info I find from other sources seems to be in Geek Goobldegooch! I simply want to get it up and running without wearing my fingertips out typing command lines etc. - is there a quick solution? Can someone convince me that it's easier than setting up a Network with Win XP? Up until now it's been like a blind man trying to play darts - I don't even know where the dart board is!!

Whatever happened to all those write ups about setting up your Linux Distro and "hey presto" everything works - including the Wireless Network connection when it first boots up? Is this a myth? 

HELP! I need to be taken gently through this process half a step at a time! 

Gwilym

---

### Post by breakthestate on 2005-10-17
Gwilym.  

If you really don't want to wade through the gobbledeegook, try installing 5.10.  I know the prism54 drivers are auto installed and should detected wg511v2.  

Also, report back if you have failure but also success!

Getting wireless to work with linux can be quite hard, especially for people new to linux, me included.  Hang in there, I promise once you get internet access with Ubunutu, you'll be glad you stuck with it.

---

### Post by Gwilym ab Ioan on 2005-10-18
Thank you very much my friend. Funnily enough I downloaded the ISO image of that version last night - straight after I posted the original message - I noticed an invitation link to go to the download page at the top of the forum window.

That's what I'll do then, and I'll report back to you. 

Isn't it amazing how many "newbies" there are about. On most of the other Linux Forums I've browsed the vast majority seem to be new to Linux, but many give what I would consider to be quite expert advice on many subjects - yourself included. Thank again!

Kind Regards,

Gwilym.

---

### Post by richbouchard on 2005-10-18
Hi there,

I have the same setup as you apart from using Breezy 5.10 on a 5-year-old VAIO.  Wireless worked out of the box without any encryption (turned off MAC filtering and WPA in the router).  There are different versions of the WG511 card as you've no doubt established.  Mine is v2 made in Taiwan.  Serial starts WG551.  Chipset reported by [some ls command that I've forgotten already - lspci was it?] is PrismGT/Duette.  Like I say, works beautifully *if I turn off my encryption*.  However, install wpasupplicant and configure it as per various instructions on this forum, turn on WPA at the router and I can't get the card to associate.  WPA works fine with all my Windows boxes, naturally.  I started another thread about WG511 and WPA, but nobody else seems to be having this problem.  Please let me know if you have any success with WPA.

Cheers,

---

### Post by Gwilym ab Ioan on 2005-10-19
Hi Breakthestate & Richbouchard,

O.K. first **Breakthestate**: I've taken your advice and downloaded the latest v 5.10 of Ubuntu (Breezy badger) and have now installed that instead of the earlier version (5.04). No joy I'm afraid, it hasn't picked up the WG511v2 card. However unlike the earlier OS version I do now have a blinking connection icon in my panel, but the Netgear wireless card is still not functioning. When I check the properties of the connection shown it tells me that it's a loopback interface (lo).

**Richbouchard**: I've discovered that the chipset for the WG511v2 card that I have is a "Marvell" so although we appear to have the same set-up equipment wise (router & card) the chipset in your WG511v2 is not the same as mine - also mine is made in China & not Taiwan.

It appears that whilst there may be a driver in Ubuntu's database for your chipset version there isn't one for mine (unless the card is defunct, but that's unlikely because it's brand new)
.
So O.K. guys where do I go from here? Incidentally Netgear tell me that they do not have a Linux drivers for any of their WG511v2 cards :( 

Regards,

Gwilym

P.S. The Laptop is actually a Time machine with an AMD K2-2 (400Mhz) CPU and not 300 as I originally wrongly quoted.

---

### Post by Gwilym ab Ioan on 2005-10-21
Hello Everyone,

After trawling through pages of forums dealing with Linux networking (all different Distros) I've come to the definate conclusion that if you want a Netgear WG511v2 wireless network adapter card to work "out of the box" DO NOT BUY a "made in China" version - stick to the "made in Taiwan" version which uses a different chipset and is covered by the prism54 driver. 

This thread from one of the forums I found sums it up:

[Date Prev][Date Next]   [Thread Prev][Thread Next]   [Thread Index] [Date Index] [Author Index] 
Re: prism54 not loading firmware...
From: Jesse Keating <jkeating j2solutions net>
To: fedora-devel-list redhat com
Subject: Re: prism54 not loading firmware...
Date: Fri, 22 Apr 2005 09:29:53 -0700
 
On Fri, 2005-04-22 at 09:11 -0400, Dan Williams wrote:
> 
> [B][COLOR="Red"]For Netgear WG511v2 cards (on bottom of the box and on back of card):
> 
> If it says "Made in Taiwan" it is OK.
> If it says "Made in China" it is softmac and not currently usable.[/COLOR][/B]
 
I just pulled it, Made in Taiwan.
 
I have more info now.
 
The firmware IS loaded if I do an 'ifconfig eth1 up'.  Previously I
misread this as 'ifup' which would hit the config files.
 
Now when I try to associate it with an AP found w/ iwlist I get this in
iwevent:
 
21:15:09.916365   eth1     Custom driver event:Authenticate request to
00:12:17:D8:AE:97  : REJECTED  (10)
21:15:09.916495   eth1     Custom driver event:Authenticate request to
00:12:17:D8:AE:97  : REJECTED  (10)
21:15:09.916515   eth1     Custom driver event:Authenticate request to
00:12:17:D8:AE:97  : REJECTED  (10)
21:15:09.916532   eth1     Custom driver event:Authenticate request to
00:12:17:D8:AE:97  : REJECTED  (10)
 
Even though this AP has no security on it at all, and works for other
Linux wireless devices.
 
Now I am trying an Ralink device, so I will hit up the website for that
device.
 
-- 
Jesse Keating RHCE      (geek.j2solutions.net)
Fedora Legacy Team      ([www.fedoralegacy.org](www.fedoralegacy.org))
GPG Public Key          (geek.j2solutions.net/jkeating.j2solutions.pub)
 
Was I helpful?  Let others know:
 [http://svcs.affero.net/rm.php?r=jkeating](http://svcs.affero.net/rm.php?r=jkeating)
 
References: 
prism54 not loading firmware... 
From: Jesse Keating
Re: prism54 not loading firmware... 
From: Per Bjornsson
Re: prism54 not loading firmware... 
From: Jesse Keating
Re: prism54 not loading firmware... 
From: Per Bjornsson
Re: prism54 not loading firmware... 
From: Dan Williams
[Date Prev][Date Next]   [Thread Prev][Thread Next]   [Thread Index] [Date Index] [Author Index]

Live 'n Learn I suppose,

Regards,

Gwilym

---

### Post by spd106 on 2005-10-21
I saw this card in PC World yesterday and thought it might be a good one. Good job I saw this thread before buying.

Have you tried ndiswrapper yet? It seems to work with most cards, although not natively, at least you can use the drivers on the supplied cd. 

Please can you update the [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") list when you near some kind of resolution. So that others know of any success/ failure.

Cheers

---

### Post by breakthestate on 2005-10-22
I'm a little confused.  I think the v3 version is the made in China version.  There aren't two different v2's are there?  Anyways, I got my "made in china" v3 working using this.

[http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804)

---

### Post by Gwilym ab Ioan on 2005-10-23
It seems there are two sources for the WG511**v2**. One in Taiwan (o.k. works "from the box apparently) and the dreaded one made in China (it uses the "Marvell" chip). The only way to get the "Marvell" chipped one to work is by using it's MS XP driver - that doesn't sound like the recipe for perfection to me!

Apparently there is also a "made in China" variation that shows "WG511v2" on the box, but shows !WG511v3" on the actual card. The only really definitive way of finding out what's actually on board is to make a note of the serial No. and ask Netgear which chipset lurks inside - that's what I did.

The answer is to stick to the "made in Taiwan version" - if you have to use a Netgear wireless adaptor. I did, simply to keep everything on an even keel because I already had a Netgear Wireless Router installed (you know the problem - you have a hickup with the router & Netgear - after a long wait in a q - will tell you it's a problem with the Belkin (or other) adapters you're using & vice versa when you contact Belkin).

Regarding the v3 I guess they may all be made in China - but I don't actually know.

Cofion Gorau,

Gwilym

---

### Post by Gwilym ab Ioan on 2005-10-24
Regarding the 511v2 and their source here's another snippet from:
 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

[COLOR="Navy"]Card: Netgear WG511 V2 (Made in Taiwan) 
Chipset: Marvell Technology Group Ltd.: Unknown device lfaa (rev 03) 
Driver: Windows XP driver available on the Netgear CD: WG511v2.INF 
Other: I'm using Ubuntu Breezy with Kernel 2.6.12-8-386. Ndiswrapper is provided by Ubuntu Breezy Colony 3 CD and version is 1.1-4. I also tried with Ubuntu Horay and its ndiswrapper seems to be broken. Once I upgrade to Breezy and it all works fine. 

Card: Netgear WG511 v2 (Made in China) 
Chipset: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03) 
Driver: Any marvell chipset driver, either from the CD, from Netgear website or from Marvell website 
Other: You cannot have preemtive kernel. It hangs either on modprobe, or randomly later. Tried with 2.6.8, 2.6.12, 2.6.13.4 and ndiswrapper1.1 and 1.4.[/COLOR]

Info Source: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) 

*Footnote*

Although the above suggests that the chip in the card from both countries is the "Marvell" - Netgear told me that it was only the made in China cards that had that chip - however, what you hear from a Call Centre operative is not always accurate! So I don't know.

To save anymore farting around :mad: I've decided to get either a new "Made in Taiwan" WG511v2 or a totally different card which is guaranteed to work out of the box. I'll hang on to the "Made in China" card and stick it in something else where it will work - without messing about. Being messed about is not good for you - it causes disappointment and that leads to stress, stress stops your heart :shock: - so rather than run the risk of heart disease  (regardless of how much you learn on the way), "ditch the hassle & use something that works" is my motto, so that I can get on with my real life !!!! 8-) 

Cofion Gorau,

Gwilym.

---

### Post by excyberlabber on 2006-05-01
I just wanted to say at this much later date, that I have a netgear WG511v2 made in China, and I got it working with Linuxant.  They have a trial license - a month for free, and a full license for $19.95.  It worked beautifully and installed my wireless card drivers from the cd .inf and .sys files without a hitch.  My Ubuntu 5.10 now sees the card and I was able to activate it through the network interface.

I am posting this for all the people who go out and buy one of these cards, as I did, thinking they were getting something that would work 'out of the box' and then getting a nasty surprise from many postings that it 'would not work'.  Well, it will work - with linuxant.

I failed with ndiswrapper...that's why I tried linuxant, and I am glad they are out there.

Now I just have to figure out how to get my WPA-PSK to work...

---

### Post by Keith_Beef on 2006-05-01
Maybe my thread [here]("http://www.ubuntuforums.org/showthread.php?t=165964") about getting my wg311v3 card to word might help you.

I wonder if there is some confusion as to the card being made in Taiwan or in the PRC, due to the fact that the Marvell chip itself is made in Taiwan, but the board as a whole is assembled on the mainland.


Beef.

---

