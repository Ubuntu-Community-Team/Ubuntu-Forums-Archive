---
title: "First time building AMD / Ubuntu computer."
date: 2011-03-01
forum: New to Ubuntu
---

### Post by casbahdk on 2011-03-01
I am interested in building an AMD based system that only runs Ubuntu and need some help finding hardware that works together and is Linux friendly. This is the first time I have ever tried building a computer, so all advice is appreciated.

The computer is for all around use. I don't do much gaming, but the box should be able to cope with Compiz, GNOME, KDE, Unity, etc. on the graphics side. Some video and sound editing will be done on the box, but otherwise it will be used for text processing, Internet surfing, etc.

Here is a basic list of components that look good to me, but nothing is set in stone, except that I want an AMD processor:

Cabinet:	Antec Three Hundred
CPU:		AMD Athlon 64 II X4-640/ 3.0GHz -2MB-BOX AM3
CPU fan:	AMD standard ???
Motherboard:	(???) Asus M4A87TD/U3B3 AMD 870-AM3-DDR3-PCIEX
Graphic card:	Radeon EAH 5770-1GB-DDR5-DX11-HDMI-ASUS CuCore
Sound:		On board (???)
Hard disk:	2 x 1 TB-Western WD1002FAEX Black-7200RPM-SATA-III-64M
CD/DVD:		???
Ram:		???

I am based in Denmark, so I am trying to get components that are available locally, or in the UK.

Cheers

---

### Post by taseedorf on 2011-03-01
I would get a phenom x6....they are cheap on newegg.com

---

### Post by matt_symes on 2011-03-01
Hi

[https://help.ubuntu.com/10.10/installation-guide/amd64/hardware-supported.html](https://help.ubuntu.com/10.10/installation-guide/amd64/hardware-supported.html)

Make sure you get a supported wireless card. Unsupported cards can cause not end of headaches.

The rest of the specs look alright as far as i can tell.

Kind regards

---

### Post by Matt__ on 2011-03-01
the wifi/lan on that board only throws up one post from 2008 that i can find on these forums
[http://ubuntuforums.org/showthread.php?t=582453](http://ubuntuforums.org/showthread.php?t=582453)

It includes a fix, which I doubt is needed anymore.

I would suggest you dont use the stock cooler either, for 15-20 euros you can get a half decent cooler/sink that will keep your cpu much happier [ebuyer.com]("http://www.ebuyer.com/product/176157")

here is a list of ATI cards that run well on the open source drivers [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by mastablasta on 2011-03-01
the card that OP wants should run on proprietary drivers as well.
 
anyway a very small list can be found here: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)
 
edit lisf of HW components is here: [http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)
 
 
some AMD/ATI cards work very well even with opensource drivers.

---

### Post by cascade9 on 2011-03-01
The Asus M4A87TD has another nasty VIA sound chip (VT 1818 ). I'd probably take a GA-870 board over the asus 870s in any case, from what I've seen the gigabyte AM2+/AM3 boards are better in general. I dont think they have hit the UK/europe yet, but GA-870-UDP3 would be my choice if possible.  GA-870A-UD3 if the other model isnt avaible.  

You could always get a sound card, asus makes some which are widely avaible and work well with linux. I wouldnt be suprised if thats part of why they are putting nasty VIA chips onboard these days. 

You wont need a aftermarket CPU heatsink if you are gettign a retail box. The cheap ones wont be much better (if any better at all) than the boxed heatsink anyway. 

5770s are far more than you would need if you arent gaming. Compiz etc will run just fine on much lower level video cards, and you would get more from a better CPU for video editing on linux than you would from a video card. I'd get a lower spec card, and spend any money saved on the CPU. ATI 5450-5670 or nVidia GT210, GT220, GT430. 

RAM- Nice 2 x 2GB DDR3 1600 is probably the 'sweet spot' now. BTW, even though the 870s normally have support for much faster RAM, running faster than DDR3 1333 can be a pain with AM3. 

CD/DVD- whatever SATA model you want. I use pioneer if I can, and avoid the LG/samsung models. Lots of people use LG/samsung with no problems though, they should work. 

HDD- WD blacks are nice, but why 2? I'd get 1 for the /root and /home, and a 2nd (WD GP, or other 'green' drive) for data/media storage

---

### Post by mastablasta on 2011-03-01
some via chips seem to work on 10.10, but only analog sound. no digital it would seem. oh well...

---

### Post by casbahdk on 2011-03-01
Wow, thanks for all of the feedback so far.

---

### Post by casbahdk on 2011-03-02
As far as I can determine, only Asus M4 series motherboards are available. I can't find any GA series motherboards at all. I understand that getting an AMD Phenom X6 processor would be a better choice.

I am considering purchasing the bits through a Swedish company that will build and ship the box. Anyone have any experience with [Compless]("http://shop.compless.com/")? Is it a reliable company? I am looking at the "Compless Allround" computer (Allround 139 version 2). There is the possibility of ordering it with an AMD Phenom X6 processor and a number of various Asus M series motherboards.

---

### Post by mick8985 on 2011-03-02
What's the situation with getting peices from the UK, is it just easy to get shipping to Denmark, are do you visit the UK frequently?

Edit: In my experience for a price of a cheap cooler it's much better than going with stock.
The stock AMD coolers tend to run at high rpm are noisy and run significantly warmer than just sticking a big mamajama like this [http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR](http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR) in there.

---

### Post by casbahdk on 2011-03-02
> **mick8985 said:**
> What's the situation with getting peices from the UK, is it just easy to get shipping to Denmark, are do you visit the UK frequently?

Edit: In my experience for a price of a cheap cooler it's much better than going with stock.
The stock AMD coolers tend to run at high rpm are noisy and run significantly warmer than just sticking a big mamajama like this [http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR](http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR) in there.

I assume that it is possible to get PC equipment shipped from the UK. I haven't tried it, but I use Amazon a lot and don't have any problems with books. I have been looking at the pre-built barebones systems at the URL you provided. They seem quite interesting, but there must be an issue with the power supply - or?

At this time, the Arctic Cooling Freezer 7 Pro Rev 2 CPU cooler is available at some PC parts suppliers in Denmark.

An interesting side note is that I yesterday visited some PC retailers and they are dumping the rest of their desktop boxes. They claim that the market is dead and that people are only in the market for laptops, netbooks, smartbooks and tablets, these days.

---

### Post by 3177 on 2011-03-02
From the looks of it, everything should work fine. Nice build by the way.

---

### Post by mick8985 on 2011-03-02
> **casbahdk said:**
> I assume that it is possible to get PC equipment shipped from the UK. I haven't tried it, but I use Amazon a lot and don't have any problems with books. I have been looking at the pre-built barebones systems at the URL you provided. They seem quite interesting, but there must be an issue with the power supply - or?

At this time, the Arctic Cooling Freezer 7 Pro Rev 2 CPU cooler is available at some PC parts suppliers in Denmark.

An interesting side note is that I yesterday visited some PC retailers and they are dumping the rest of their desktop boxes. They claim that the market is dead and that people are only in the market for laptops, netbooks, smartbooks and tablets, these days.

No issue with the power supply, they'll ship you a UK kettle lead, but just replace it with a europlug kettle lead and everything will be fine. [http://ecx.images-amazon.com/images/I/31B%2BupPfZwL._SL500_AA300_.jpg](http://ecx.images-amazon.com/images/I/31B%2BupPfZwL._SL500_AA300_.jpg)

Overclockers seems to ship overseas aswell so denmark shouldn't be an issue if you do go with them.

---

### Post by tempmike on 2011-03-02
I'll be playing the role of modesty and conservatism in this post. (usually I try to get only what I need and not more in computers)

Is there a reason you want to avoid integrated video and get a discrete card?
I fully understand there are processing applications where having a discrete GPU is an advantage(and that your selected mobo does not have integrated video so you need something) but you may be able to spend 20USD extra on the motherboard and get by with all the video power you need.

As for the CPU, more cores does not always mean better computer. Its all based on what you're doing and if you're only using 2 or 3 or 4 cores you're "not" gaining from having the extra overhead of 6 cores (yeah, there is the turbocore technology but you pay a premium for it).

Also, you should consider your PSU needs.
That's very important for a computer. I would suggest buying a "brand name" PSU. I've only ever bought corsair and never had any problems, but I've seen a few posts of people who switched from cheap psu to quality and were very satisfied. I'd say any brand name is fine, just dont get more power than you need (edit: in the foreseeable future).


As for CPU coolers, if youre running hardware at spec you should be fine with the stock coolers. (and I don't know if AMD will honor any warrenty problems if youre using a thrid party cooler. not that they would necessarily know if you were or were not)


Of course, if you're looking to build the Hummer/Cadillac hybrid of computers ignore everything I've said. (except about needing a PSU, you need a PSU).

---

### Post by khelben1979 on 2011-03-02
Some of my thoughts:

1. nVidia cards works better with heavy Linux gaming.
2. Make sure to get a high quality powersupply, Corsair makes really good powersupplies!
3. Be aware how the computer is gonna be used, less power gets more cheap and might be enough.

I think the things in the list you provided should be okay, but get an nVidia card or get dissapointed for heavy gaming..

---

### Post by casbahdk on 2011-03-03
> **khelben1979 said:**
> Some of my thoughts:

1. nVidia cards works better with heavy Linux gaming.
2. Make sure to get a high quality powersupply, Corsair makes really good powersupplies!
3. Be aware how the computer is gonna be used, less power gets more cheap and might be enough.

I think the things in the list you provided should be okay, but get an nVidia card or get dissapointed for heavy gaming..

Thanks for the advice :)

---

### Post by casbahdk on 2011-03-03
> **cascade9 said:**
> The Asus M4A87TD has another nasty VIA sound chip (VT 1818 ). I'd probably take a GA-870 board over the asus 870s in any case, from what I've seen the gigabyte AM2+/AM3 boards are better in general. I dont think they have hit the UK/europe yet, but GA-870-UDP3 would be my choice if possible.  GA-870A-UD3 if the other model isnt avaible.

I see that OcUK has a [GA-870A-UD3]("http://www.overclockers.co.uk/showproduct.php?prodid=MB-283-GI&groupid=701&catid=1903&subcat=1782"). Will this motherboard work with an Antec Three Hundred case, or do I need something bigger?

---

### Post by mick8985 on 2011-03-03
> **casbahdk said:**
> I see that OcUK has a [GA-870A-UD3]("http://www.overclockers.co.uk/showproduct.php?prodid=MB-283-GI&groupid=701&catid=1903&subcat=1782"). Will this motherboard work with an Antec Three Hundred case, or do I need something bigger?

Your case should be fine with virtually any motherboard you fancy.
If you decide to go for an nvidia card, get one which supports vdpau [http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)
It enables the video card to decode video, works with youtube videos with the new flashplayer aswell.

---

### Post by casbahdk on 2011-03-03
> **mick8985 said:**
> Your case should be fine with virtually any motherboard you fancy.
If you decide to go for an nvidia card, get one which supports vdpau [http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)
It enables the video card to decode video, works with youtube videos with the new flashplayer aswell.

Thanks for the useful information :)

---

### Post by casbahdk on 2011-03-04
> **mick8985 said:**
> Your case should be fine with virtually any motherboard you fancy.
If you decide to go for an nvidia card, get one which supports vdpau [http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)
It enables the video card to decode video, works with youtube videos with the new flashplayer aswell.

I just ordered the first bits for my AMD box:

Antec Three Hundred Kabinet - U/Psu- Gamer Case
AMD Phenom II 64 X6-1100T/ 3.3GHz -9MB Black BOX AM3
Gigabyte GA-870A-UD3 AMD 870 (Socket AM3) DDR3 Motherboard

I decided to go with the Phenom II 64 X6-1100T as it got the best review of all of the AMD CPUs in the newest PC Format magazine.

It looks like the Gigabyte GA-870A-UD3 has Sata III, I believe I have seen some Sata III hard disks being sold online, but what about CD/DVD drives? What interface am I looking for?


Cheers

---

### Post by cascade9 on 2011-03-05
The antec 300 is a pretty nice case. Not quite my style, but hey its not my build....  

You should be able to fit the vast majority of standard ATX style motherboards into that case. There are a few that wont fit, EATX/ATXXL motherboard wont, but they arent common for desktop motherboards. As far as I know, there are only a few 890FX AM3 and X58 LGA1366 motherboards that are EATX/ATXXL. Its far more common in server/workstation dual CPU boards. 

SATAIII HDDs are fine, but dont expect any major differences between a STAII and SATAIII HDD. The main place where you will notice a difference between SATAII and III is with SSDs, some of them are faster than SATAII bandwidth. 

A SATA CD/DVD should work just fine with a SATAIII controller. 

> **mick8985 said:**
> What's the situation with getting peices from the UK, is it just easy to get shipping to Denmark, are do you visit the UK frequently?

Edit: In my experience for a price of a cheap cooler it's much better than going with stock.
The stock AMD coolers tend to run at high rpm are noisy and run significantly warmer than just sticking a big mamajama like this [http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR](http://www.overclockers.co.uk/showproduct.php?prodid=HS-035-AR) in there.

Thats actually not that great from every test I've seen. This is fairly typical- 

[http://www.tomshardware.com/reviews/lga-1156-heatsink,2535.html](http://www.tomshardware.com/reviews/lga-1156-heatsink,2535.html)

Probably the best of the cheaper aftermarket coolers is the coolermaster hyper 212+ which is only an extra quid or so- 

[http://www.overclockers.co.uk/showproduct.php?prodid=HS-029-CM&groupid=701&catid=57&subcat=1395](http://www.overclockers.co.uk/showproduct.php?prodid=HS-029-CM&groupid=701&catid=57&subcat=1395)

I stil dont think that its really needed, newer AMD heatsink/fans are better than the older ones. I've got a Socket 939 4000+, its a lot louder than the stock heatsink on either the AM2+ 4800+ (dual core) or Phenom II X2 550 also running around here. Its also a lot louder than the X4 945/955/965 heatsinks I've heard as well (so far I havent heard a stock X6 heatsink, all teh X6s I've seen have been using aftermarket coolers) 

> **tempmike said:**
> I fully understand there are processing applications where having a discrete GPU is an advantage(and that your selected mobo does not have integrated video so you need something) but you may be able to spend 20USD extra on the motherboard and get by with all the video power you need.

A cheap video card doesnt cost much (if anything) more than how much extra the manufacturers want for a board with onboard video. The cheap onboard uses main system RAM as well, which does give a minor performance hit compared to a discreet video card as well, and the better ones with onboard video RAM cost more than a low end video card.

---

### Post by casbahdk on 2011-03-05
> **cascade9 said:**
> The antec 300 is a pretty nice case. Not quite my style, but hey its not my build.... 

Thanks for the reply. First build. Maybe I will develop my own style as time goes on :)

> **cascade9 said:**
> You should be able to fit the vast majority of standard ATX style motherboards into that case.
This was confirmed by OverclockersUK.

One thing I am confused about is RAM for the motherboard. The specs say "4x DDR3 DIMM 1866(OC) / 1333 / 1066 MHz (Max. 16GB) / Dual Channel", but when I look at local sites, they refer to "DDR2-RAM 240 pins, DDR3-RAM 240 pins or DDR3-RAM -i7" Is "i7" RAM specific for Intel i7 processors? I assume that "1866, 1333 and 1066" refers to MHz? What do I want and does the brand of the RAM make a difference?

> **cascade9 said:**
> SATAIII HDDs are fine, but dont expect any major differences between a STAII and SATAIII HDD. The main place where you will notice a difference between SATAII and III is with SSDs, some of them are faster than SATAII bandwidth.

Do you still have to fiddle with pins for setting "master" and "slave" drives as with the ATA interface or is this sorted automagically now with SATAII and SATAIII? 

> **cascade9 said:**
> A SATA CD/DVD should work just fine with a SATAIII controller. 

Cheers.

> **cascade9 said:**
> Probably the best of the cheaper aftermarket coolers is the coolermaster hyper 212+ which is only an extra quid or so- 

[http://www.overclockers.co.uk/showproduct.php?prodid=HS-029-CM&groupid=701&catid=57&subcat=1395](http://www.overclockers.co.uk/showproduct.php?prodid=HS-029-CM&groupid=701&catid=57&subcat=1395)

I stil dont think that its really needed, newer AMD heatsink/fans are better than the older ones. I've got a Socket 939 4000+, its a lot louder than the stock heatsink on either the AM2+ 4800+ (dual core) or Phenom II X2 550 also running around here. Its also a lot louder than the X4 945/955/965 heatsinks I've heard as well (so far I havent heard a stock X6 heatsink, all teh X6s I've seen have been using aftermarket coolers) 

OK, so the jury is still out on this. What do other posters think? Do I need an aftermarket cooler when I am not overclocking? The motherboard isn't going to burn is it? That happened to me many moons ago when I had an AMD system built for me. The Soyo Dragon Plus motherboard fried after a year.

> **cascade9 said:**
> A cheap video card doesnt cost much (if anything) more than how much extra the manufacturers want for a board with onboard video. The cheap onboard uses main system RAM as well, which does give a minor performance hit compared to a discreet video card as well, and the better ones with onboard video RAM cost more than a low end video card.

I was thinking about a GeForce 9800 GT 1 GB PCIe. It seems to be well supported in Linux.

Do I need a sound card?

BTW, does the power supply come with the Antec 300 or do I purchase a power supply separately?

Thanks for all the feedback.

---

### Post by mick8985 on 2011-03-05
I'd definitely go with an aftermarket cooler, I used the stock cooler from AMD for a long while and the noise annoyed me so much I changed for that reason purely, nothing to do with overclocking.

Cascade seems to be up on the different coolers so I'd take his recommendation over mine on choice of cooler. I have the cooler I suggested and it's fine, but if Cascade thinks the other one is better and it's only a pound more, I'd spend the pound.

I'd definitely go with an Nvidia card. To me on linux all I care about is A) the proprietary drivers for nvidia are better than those for AMD, and B) the Nvidia card I pick supports vdpau, they are my only 2 considerations and the card you suggested ticks both boxes.

As for sound card, on board sound will probably serve you well enough.

If I were going to focus on improving my audio experience I'd spend my money on one of these [http://www.superfi.co.uk/index.cfm/page/moreinfo.cfm/Product_ID/7116](http://www.superfi.co.uk/index.cfm/page/moreinfo.cfm/Product_ID/7116) Before I start spending money on a decent sound card and plugging it into crappy pc speakers.

If you have a decent amp and speakers, get the sound card, if not don't bother.

[http://www.overclockers.co.uk/showproduct.php?prodid=CA-101-AN](http://www.overclockers.co.uk/showproduct.php?prodid=CA-101-AN)

This Antec 300 has no PSU, if you are getting it from another shop, a danish one perhaps they package it with a PSU I dunno.

The ocUK branded white goods PSU's claiming to be silent look temptingly cheap (especially the modular one for £38.99), dunno whether I'd put on in my box though.

---

### Post by casbahdk on 2011-03-05
> **mick8985 said:**
> I'd definitely go with an aftermarket cooler, I used the stock cooler from AMD for a long while and the noise annoyed me so much I changed for that reason purely, nothing to do with overclocking.

Cascade seems to be up on the different coolers so I'd take his recommendation over mine on choice of cooler. I have the cooler I suggested and it's fine, but if Cascade thinks the other one is better and it's only a pound more, I'd spend the pound.

OK, one cooler to be ordered, check.
--
Edit - I could also go with a Arctic Freezer 7 Pro v.2 cooler. I can get it locally. The review here [http://www.testseek.com/labs/reviews/review-of-arctic-cooling-freezer-7-pro-rev-2-cpu-cooler/?p=2694]("http://www.testseek.com/labs/reviews/review-of-arctic-cooling-freezer-7-pro-rev-2-cpu-cooler/?p=2694")seems to be pretty good. cascade9, what do you think?
--
> **mick8985 said:**
> I'd definitely go with an Nvidia card. To me on linux all I care about is A) the proprietary drivers for nvidia are better than those for AMD, and B) the Nvidia card I pick supports vdpau, they are my only 2 considerations and the card you suggested ticks both boxes.

I can't find the link now, but I am sure the GeForce 9800 GT 1 GB PCIe was in the "A" category for vdpau support.

> **mick8985 said:**
> [http://www.overclockers.co.uk/showproduct.php?prodid=CA-101-AN](http://www.overclockers.co.uk/showproduct.php?prodid=CA-101-AN)

This Antec 300 has no PSU, if you are getting it from another shop, a danish one perhaps they package it with a PSU I dunno.

Doh! No, it doesn't. I see that now. Since I am ordering the cooler through ocUK, do you have a suggestion for a good power supply as an alternative to the ocUK branded PSU's? There doesn't seem to be much to choose from locally.

---

### Post by mick8985 on 2011-03-05
I really like modular PSU's but they are really expensive, I got a cheap one from Hiper in a local shop, which does the job fine.
If you aren't bothered about a modular psu (all it does is make you case tidier really) 
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-044-AK&groupid=701&catid=123&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=CA-044-AK&groupid=701&catid=123&subcat=)
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-033-CS&groupid=701&catid=123&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=CA-033-CS&groupid=701&catid=123&subcat=)
These 2 have enough power for the job and are nicely priced.
If you plan on a ton of extra hard drives or anything like that you might want a more powerful one.

---

### Post by casbahdk on 2011-03-05
> **mick8985 said:**
> I really like modular PSU's but they are really expensive, I got a cheap one from Hiper in a local shop, which does the job fine.
If you aren't bothered about a modular psu (all it does is make you case tidier really) 
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-044-AK&groupid=701&catid=123&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=CA-044-AK&groupid=701&catid=123&subcat=)
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-033-CS&groupid=701&catid=123&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=CA-033-CS&groupid=701&catid=123&subcat=)
These 2 have enough power for the job and are nicely priced.
If you plan on a ton of extra hard drives or anything like that you might want a more powerful one.

Thanks for the quick reply. If there is any doubt about my power needs, I could get something like either the Corsair Builder Series CX 500W or 600W PSU:
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-034-CS&groupid=701&catid=123&subcat=1084]("http://www.overclockers.co.uk/showproduct.php?prodid=CA-034-CS&groupid=701&catid=123&subcat=1084")
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-035-CS&groupid=701&catid=123&subcat=1084]("http://www.overclockers.co.uk/showproduct.php?prodid=CA-035-CS&groupid=701&catid=123&subcat=1084")

---

### Post by willhurley82 on 2011-03-05
I build my own computers and am a Windows power user, switching to Linux.  I had an ATI video card, the first time I installed Ubuntu.  It did good, but gave me nothing but trouble when I did anything 3D.  I ended up getting rid of it (it was a 4650) because I found that ATI did not actively support Linux.  You may want to research this before you go with that card.

---

### Post by casbahdk on 2011-03-05
> **willhurley82 said:**
> I build my own computers and am a Windows power user, switching to Linux.  I had an ATI video card, the first time I installed Ubuntu.  It did good, but gave me nothing but trouble when I did anything 3D.  I ended up getting rid of it (it was a 4650) because I found that ATI did not actively support Linux.  You may want to research this before you go with that card.

Thanks for your reply. I found the link again, and it lists the GeForce 9800 GT 1 GB PCIe under "A" features.
[http://www.mythtv.org/wiki/VDPAU#Supported_Cards]("http://www.mythtv.org/wiki/VDPAU#Supported_Cards")

---

### Post by casbahdk on 2011-03-06
The outstanding ingredients for my new computer are RAM and cables:
1) The specs for my motherboard state "4x DDR3 DIMM 1866(OC) / 1333 / 1066 MHz (Max. 16GB) / Dual Channel" What kind of RAM do I want and does the brand of the RAM make a difference?
2) What cables do I need for my computer and do they need to be purchased separately or are they included with the motherboard?

---

### Post by cascade9 on 2011-03-06
Sorry for a huge post. Make yourself a cup of coffee, tea, or go get a beer before you start LOL. 

> **casbahdk said:**
> Thanks for the reply. First build. Maybe I will develop my own style as time goes on :)

I'll fully admit to being an opinionated sot. I know what I like,I've seen so many cases and there is such a huge range of cases around that I've got to the point of just saying 'thats what I like'. 

Its not really a problem if you dont have the same attitude. In the end, a case is just a box to hold the parts. ;) 

> **casbahdk said:**
> One thing I am confused about is RAM for the motherboard. The specs say "4x DDR3 DIMM 1866(OC) / 1333 / 1066 MHz (Max. 16GB) / Dual Channel", but when I look at local sites, they refer to "DDR2-RAM 240 pins, DDR3-RAM 240 pins or DDR3-RAM -i7" Is "i7" RAM specific for Intel i7 processors? I assume that "1866, 1333 and 1066" refers to MHz? What do I want and does the brand of the RAM make a difference?

'i7' would be for socket 1366, which unlike 'dual channel' RAM fond on LGA11556/1155 or AM2+/AM3 (and tons of earlier socckets) LGA1366 uses 'triple channel' RAM. So you need 3 sticks, not 2. Well, you dont actually need 2 sticks to run a dual channel board, or 3 sticks to run triple channel, either will run with less sticks. 

Running at DDR3-1333 is the standard for AM3. It can be possible to run faster RAM speeds, but its hit and miss. 

Brand? If you want to be totally sure that everything should run properly, getting RAM from the manufacturers supported RAM list is the way to go. Its more likely have issues with RAM thats not on the supported list, but that is still farily unlikely. 

Currently, DDR3-1600 is probably the best bet (even though you wont be able to run at 1600 with that board. The faster RAM is still going to enough more than DDR3-1333/1600 that its not worth it IMO. 

BTW, CAS ratings will have a minor impact. Lower CAS = better. Also, some RA runs at higher than normal voltage, ranging from 1.5v (what DDR3 should be) to 1.7-1.9volts. I'd try to get DDR3-1600 with the lowest CAS rating you can get, running at 1.5v. Again, depending on whats available and costing that might not be possible, or viable. No point spending a huge amount more for lower CAS or lower voltage, its a balancing act (given the option I'd go for DDR3-1600 CAS9 1.5v over DDR3-1600 CAS7 1.7v, as an example)

> **casbahdk said:**
> Do you still have to fiddle with pins for setting "master" and "slave" drives as with the ATA interface or is this sorted automagically now with SATAII and SATAIII? 

Nope, all that master/slave (whips/chains LOL) stuff is gone from SATA drives. 

There are still jumpers on the back of the drives in most cases, but thats for limiting to slower SATA speeds, and other technical trickery. You should have to play with jumpers at all in the vast majority of cases. 
 
> **casbahdk said:**
> OK, so the jury is still out on this. What do other posters think? Do I need an aftermarket cooler when I am not overclocking? The motherboard isn't going to burn is it? That happened to me many moons ago when I had an AMD system built for me. The Soyo Dragon Plus motherboard fried after a year.

Soyo Dragon Plus? Socket 'A', the stock AMD socket a coolers were generally pretty awful to be honest. Things have got a lot better these days. 

Still, when you are spending that much on a CPU, getting a decent cooler is never bad idea. 

> **casbahdk said:**
> I was thinking about a GeForce 9800 GT 1 GB PCIe. It seems to be well supported in Linux.

Do you game much? If not, then the GT9800 is just a power drain, and if you do game then there are better choices. 

For gaming- 
GTS250- same basic chip as the 8800GT, 9800 GT, but slightly upgraded. VDPAU 'A'.
GTX2XX- faster than GTS250/9800/8800, hard to find now. VDPAU 'A'.
GTX460- The current price/performance king for gaming with good linux support. VDPAU 'C'. 

If you dont game-
GT220- Low power, runs cool, tons of performance for desktop use. Also has VDPAU 'C'.
GT430- better for a HTPC (GT220 wont out DTS over HDMI, GT430 will). VDPAU 'C' Not really worth the extra cost over a GT220 for any over use IMO. That would depend on the local prices though....  

BTW, 'A' is ther lowest level of VDPAU support, 'C' is highest. Currently anyway.

Also, I'm running a 8600Gt. About the same amount of performance as the GT220, and it does VDPAU, desktop effects (kwin, I dont use compiz) really well. A lot cheaper than a 9800GT as well.  

> **willhurley82 said:**
> I build my own computers and am a Windows power user, switching to Linux.  I had an ATI video card, the first time I installed Ubuntu.  It did good, but gave me nothing but trouble when I did anything 3D.  I ended up getting rid of it (it was a 4650) because I found that ATI did not actively support Linux.  You may want to research this before you go with that card.

ATI/AMD is really picking up these days, and in some ways they support linux better than nvidia. ATI/AMD engineers actually do some work on the open source drivers, and ATI/AMD has shown at least some of the technical specs for the older cards. nVidia hasnt opened the specs at all, have dropped the 'nv' driver and are letting the open source community muddle though trying to get the open source 'nouveau' drivers working. 

I'd still go for nVidia at this point. VDPAU is great, the drivers work. XvBA (ATI/AMD hardware video decoding) is still buggy, but at least the drivers work well now.  

> **mick8985 said:**
> Cascade seems to be up on the different coolers so I'd take his recommendation over mine on choice of cooler. I have the cooler I suggested and it's fine, but if Cascade thinks the other one is better and it's only a pound more, I'd spend the pound.

Thanks fot the vote of confidence ;) 

> **mick8985 said:**
> As for sound card, on board sound will probably serve you well enough.

If I were going to focus on improving my audio experience I'd spend my money on one of these [http://www.superfi.co.uk/index.cfm/page/moreinfo.cfm/Product_ID/7116](http://www.superfi.co.uk/index.cfm/page/moreinfo.cfm/Product_ID/7116) Before I start spending money on a decent sound card and plugging it into crappy pc speakers.

If you have a decent amp and speakers, get the sound card, if not don't bother.

I'd agree. Though I dont think you would need 200 quids worth of amp to be able to tell the difference between the onboard sound and a decent sound card. As with almost everything to do with sensible system building, its a balancing act. 

> **casbahdk said:**
> OK, one cooler to be ordered, check.
--
Edit - I could also go with a Arctic Freezer 7 Pro v.2 cooler. I can get it locally. The review here [http://www.testseek.com/labs/reviews/review-of-arctic-cooling-freezer-7-pro-rev-2-cpu-cooler/?p=2694]("http://www.testseek.com/labs/reviews/review-of-arctic-cooling-freezer-7-pro-rev-2-cpu-cooler/?p=2694")seems to be pretty good. cascade9, what do you think?


I tend to not really trust heatsink reviews that are just a single cooler..they didnt even compare to the stock intel heatsink. The spanish (I think) in the graphs is pretty strange as well. 

One other thing with the Freezer 7 Pro 2 is that it using fan/clip assembly, so fitting a different fan could be a pain. The coolermaster uses just clips, its easy to swap the fan out for something more quiet if you decide the stock fan is too noisy. You can pay as much for a good fan as you do for the coolermaster heatsink/fan..... 

> **casbahdk said:**
> 2) What cables do I need for my computer and do they need to be purchased separately or are they included with the motherboard?

You should get 2 SATA cables, and 1 PATA cable with the motherboard, provided that the retailer hasnt opened he box and taken them out (I know of stores that do that so they can sell you a a couple a $5-10 cables you should have got for free). 

> **casbahdk said:**
> Thanks for the quick reply. If there is any doubt about my power needs, I could get something like either the Corsair Builder Series CX 500W or 600W PSU:
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-034-CS&groupid=701&catid=123&subcat=1084]("http://www.overclockers.co.uk/showproduct.php?prodid=CA-034-CS&groupid=701&catid=123&subcat=1084")
[http://www.overclockers.co.uk/showproduct.php?prodid=CA-035-CS&groupid=701&catid=123&subcat=1084]("http://www.overclockers.co.uk/showproduct.php?prodid=CA-035-CS&groupid=701&catid=123&subcat=1084")

Personally, I'd probably go for the CX500 (opinionated sot). I havent used one myself, but all the corsair power supplies I've seen are very good quality, and IMO the power supply is vital. Bad voltages can cause damage, and better quality power supplies tend to have better voltages, quieter fans, and are just tougher in general. 

Example? I'm running a corsair HX-520. My housemate has a thermaltake 430watt (I forget the exact model). One day we were both using our computers, and a power substation blew (within sight of my window, I actually saw it blow!). Housemates computer- just turned off. My computer, filckered with the lights then kept on running.....

---

### Post by Vaphell on 2011-03-06
> and IMO the power supply is vital. Bad voltages can cause damage, and better quality power supplies tend to have better voltages, quieter fans, and are just tougher in general.

agreed, voltage spike can kill every part inside the computer, i've had dead mobos, a dead hdd, dead gfx card and even a keyboard and a mouse. Good power brick can shield the system from such destructive voltages and the probability of total system failure is greatly reduced. Being cheap simply doesn't pay off in such case.

---

### Post by casbahdk on 2011-03-06
> **cascade9 said:**
> Its not really a problem if you dont have the same attitude. In the end, a case is just a box to hold the parts. ;) 

No worries :)

> **cascade9 said:**
> 'i7' would be for socket 1366, which unlike 'dual channel' RAM fond on LGA11556/1155 or AM2+/AM3 (and tons of earlier socckets) LGA1366 uses 'triple channel' RAM. So you need 3 sticks, not 2. Well, you dont actually need 2 sticks to run a dual channel board, or 3 sticks to run triple channel, either will run with less sticks.

Noted. 

> **cascade9 said:**
> Running at DDR3-1333 is the standard for AM3. It can be possible to run faster RAM speeds, but its hit and miss. 

Brand? If you want to be totally sure that everything should run properly, getting RAM from the manufacturers supported RAM list is the way to go. Its more likely have issues with RAM thats not on the supported list, but that is still farily unlikely.

I downloaded the "[qualified vendors list]("http://download.gigabyte.eu/FileList/Memory/mb_memory_ga-870a-ud3.pdf")" but I don't really understand it, beyond that Gigabyte recommends Kingston and Corsair, plus a few others. What is SS/DS? 

> **cascade9 said:**
> BTW, CAS ratings will have a minor impact. Lower CAS = better. Also, some RA runs at higher than normal voltage, ranging from 1.5v (what DDR3 should be) to 1.7-1.9volts. I'd try to get DDR3-1600 with the lowest CAS rating you can get, running at 1.5v. Again, depending on whats available and costing that might not be possible, or viable. No point spending a huge amount more for lower CAS or lower voltage, its a balancing act (given the option I'd go for DDR3-1600 CAS9 1.5v over DDR3-1600 CAS7 1.7v, as an example)

So I am looking for something like this?
[http://www.overclockers.co.uk/showproduct.php?prodid=MY-026-KS]("http://www.overclockers.co.uk/showproduct.php?prodid=MY-026-KS")

> **cascade9 said:**
> Nope, all that master/slave (whips/chains LOL) stuff is gone from SATA drives. :lolflag: 

> **cascade9 said:**
> Do you game much? Not at all, but I wouldn't mind trying, now that I am building a PC that will be able to.

> **cascade9 said:**
> BTW, 'A' is ther lowest level of VDPAU support, 'C' is highest.

What? That is just downright counter intuitive. Hmm.

> **cascade9 said:**
> One other thing with the Freezer 7 Pro 2 is that it using fan/clip assembly, so fitting a different fan could be a pain. The coolermaster uses just clips, its easy to swap the fan out for something more quiet if you decide the stock fan is too noisy. You can pay as much for a good fan as you do for the coolermaster heatsink/fan..... 

OK, Coolermaster it is.

> **cascade9 said:**
> You should get 2 SATA cables, and 1 PATA cable with the motherboard, provided that the retailer hasnt opened he box and taken them out (I know of stores that do that so they can sell you a a couple a $5-10 cables you should have got for free).

I have ordered the motherboard through OverclockersUK. I don't know what their usual practice is.

> **cascade9 said:**
> Personally, I'd probably go for the CX500 (opinionated sot). I havent used one myself, but all the corsair power supplies I've seen are very good quality, and IMO the power supply is vital. Bad voltages can cause damage, and better quality power supplies tend to have better voltages, quieter fans, and are just tougher in general.

Is the CX600 overkill for my needs? I am just concerned that I have enough power to run the usual bits and bobs.

---

### Post by casbahdk on 2011-03-06
> **Vaphell said:**
> agreed, voltage spike can kill every part inside the computer, i've had dead mobos, a dead hdd, dead gfx card and even a keyboard and a mouse. Good power brick can shield the system from such destructive voltages and the probability of total system failure is greatly reduced. Being cheap simply doesn't pay off in such case.

Cheers.

---

### Post by casbahdk on 2011-03-06
I think I will get the GeForce GT220 and the Corsair CX 600W. I will have the necessary power should I choose to upgrade the graphics card.

---

### Post by cascade9 on 2011-03-06
> **casbahdk said:**
> I downloaded the "[qualified vendors list]("http://download.gigabyte.eu/FileList/Memory/mb_memory_ga-870a-ud3.pdf")" but I don't really understand it, beyond that Gigabyte recommends Kingston and Corsair, plus a few others. What is SS/DS? 

SS/DS = Single Sided/Double Sided. Some RAM sitcks only have chips on one side (single) and some have chips on both sides (double). It used to be more useful in IDing RAM sticks, in these days of RAMsinks SS/DS is more of technicality. 

The support list is really just a guide in a lot of ways. The RAM manufacturers tend to release newer versions of the sticks they make, and the support list normally (not always) doesnt change over time. The sticks listed are what the manufacturer tested, thats why they have the part numbers (Module P/N). 

I've seen people go crazy trying to get the exact part number listed. I can sort of see why, but in most cases a newer or older module will work just as well. A lot of shops dont even list the module part number, just the basic title (like 'corsair dominator DRR3-

BTW, sorry about all times I've used 'most' and 'normally'....  

> **casbahdk said:**
> So I am looking for something like this?
[http://www.overclockers.co.uk/showproduct.php?prodid=MY-026-KS]("http://www.overclockers.co.uk/showproduct.php?prodid=MY-026-KS")

Close, but thats DDR2. 

After having a look at the RAM overclockers UK is selling, Id go for either the corsair, geil or OCZ DDR3-1600 2 x 2GB kits....damnit, I cant be bothered to type out the whole name, linking instead- 

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517)

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-104-GL&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-104-GL&groupid=701&catid=8&subcat=1517)

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-192-OC&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-192-OC&groupid=701&catid=8&subcat=1517)



 
> **casbahdk said:**
> Not at all, but I wouldn't mind trying, now that I am building a PC that will be able to.

Even the GT220 is more than capable of gaming. The 'gaming' cards will give you a better framerate. 

> **casbahdk said:**
> What? That is just downright counter intuitive. Hmm.

It sort of is. The way I remember how the VDPAU features work is 'A' is 1st (lowest support), 'C' is last (highest support). 

> **casbahdk said:**
> Is the CX600 overkill for my needs? I am just concerned that I have enough power to run the usual bits and bobs.

With a GT220, X6 1100T, a DVD-RW a few HDDs yeah, it is. But you never know, you might want to slide a huge video card into the system at some point, and they can eat huge amounts of power. 

Even then 600watts is probably more than you would need, but its probably better safe than sorry. Its only 10 quid more anyway, and its not like you could get a modular 500 watter for the same amount of money as the corsair 600. 

Modular wont really help, but it sure makes things neater inside the case. ;) 

BTW, if you've got time, and have much interest in the actual power consumption then this article is well worth reading- 

[http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html)

Its shocking how low the 'real world' power consumption of even top end systems are, when you compare them to some of the monster 1 kilowatt+ power supplies you see some people use.

---

### Post by casbahdk on 2011-03-06
> **cascade9 said:**
> After having a look at the RAM overclockers UK is selling, Id go for either the corsair, geil or OCZ DDR3-1600 2 x 2GB kits....damnit, I cant be bothered to type out the whole name, linking instead- 

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517)

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-104-GL&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-104-GL&groupid=701&catid=8&subcat=1517)

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-192-OC&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-192-OC&groupid=701&catid=8&subcat=1517)


The Corsair XMS3 4GB and the OCZ Intel Extreme XMP 4GB specs state that they are especially designed for the Intel "i" series of processors.

> **cascade9 said:**
> Even the GT220 is more than capable of gaming. The 'gaming' cards will give you a better framerate. 

Sounds good.

> **cascade9 said:**
> With a GT220, X6 1100T, a DVD-RW a few HDDs yeah, it is. But you never know, you might want to slide a huge video card into the system at some point, and they can eat huge amounts of power. 

Even then 600watts is probably more than you would need, but its probably better safe than sorry. Its only 10 quid more anyway, and its not like you could get a modular 500 watter for the same amount of money as the corsair 600. 

Thanks again for all of the feedback.

---

### Post by cascade9 on 2011-03-06
> **casbahdk said:**
> The Corsair XMS3 4GB and the OCZ Intel Extreme XMP 4GB specs state that they are especially designed for the Intel "i" series of processors.

*channels public enemy* Don't, don't, don't believe the hype.  

Or a sales page for that matter. Its marketing, as in 'look out, dont step in the marketing!' 

> Guaranteed to work on all dual channel Intel and AMD platforms

[http://www.corsair.com/cmx4gx3m2a1600c9.html](http://www.corsair.com/cmx4gx3m2a1600c9.html)

Being more serious, and cutting a long story short, you can see the hint in the overclockers UK page-

> - Sandybridge compatible (use sub 1.60v) 

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517)

There are lots of DDR3 modules that use a voltage higher than intel allows for iX chipsets. 

I haven't checked the offical page for the OCZ RAM, but I'll bet its the same situation. 
 
> **casbahdk said:**
> Thanks again for all of the feedback.

No problem. ;)

---

### Post by casbahdk on 2011-03-06
> **cascade9 said:**
> *channels public enemy* Don't, don't, don't believe the hype.  

Or a sales page for that matter. Its marketing, as in 'look out, dont step in the marketing!' 



[http://www.corsair.com/cmx4gx3m2a1600c9.html](http://www.corsair.com/cmx4gx3m2a1600c9.html)

Being more serious, and cutting a long story short, you can see the hint in the overclockers UK page-

 

[http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517](http://www.overclockers.co.uk/showproduct.php?prodid=MY-203-CS&groupid=701&catid=8&subcat=1517)

There are lots of DDR3 modules that use a voltage higher than intel allows for iX chipsets. 

I haven't checked the offical page for the OCZ RAM, but I'll bet its the same situation. 
 


No problem. ;)

Thanks to everyone that contributed to this thread. Special thanks to cascade9 for all of the research and opinions. :) Here is what my final configuration looks like:

Antec Three Hundred Case					
AMD Phenom II 64 X6-1100T/ 3.3GHz -9MB Black BOX AM3		
Gigabyte GA-870A-UD3 AMD 870 (Socket AM3) DDR3 Motherboard	
Plextor PX-L890SA internal SATA DVD/CD Super Multi Writer	
GeForce GT220-1024MB-DDR2-VGA/DVI+HDMI-ASUS V2			
Harddisk: 1 TB-Western WD1002FAEX Black-7200RPM-SATA-III-64M	
GeIL 4GB (2x2GB) DDR3 PC3-12800C9 1600MHz			
Cooler Master Hyper 212 Plus CPU Cooler
Corsair Builder Series CX 600W ATX Power Supply

---

### Post by cascade9 on 2011-03-06
Being thanked for being an opinionate so-and-so, LOL

Argh! I thought I had seen plextor in a post you made, then I couldnt find it later. 

Dont. Just dont. Plextor used to make amazing CD drives, but these days they are just rebanded drives from other manufacturers. I dont know for sure what the PX-L890SA  is rebranded from (probably a liteON) 

*edit- 

> I'd then go for an Optiarc (in case CD application matters) or a Liteon. Plextors are Liteon drives with custom firmware.

[http://club.myce.com/f105/advice-samsung-s233l-plextor-px-890sa-319830/](http://club.myce.com/f105/advice-samsung-s233l-plextor-px-890sa-319830/)

I wouldnt call a forum post 'proof' but it makes me think that I was right with the liteON guess. 

> I recently bought a new Plextor DVD drive (PX-L890SA) because my old one (Philips DVDR 1640) broke down. Unfortunately, I have some problems writing DVD-RAM media on Linux. 
snip!
As I found several other postings with people complaining about their Plextor not working properly when writing DVD-RAM on Linux, I suppose it is a Plextor issue

[http://club.myce.com/f43/dvd-ram-px-l890sa-not-working-linux-318920/](http://club.myce.com/f43/dvd-ram-px-l890sa-not-working-linux-318920/)

You'll probably never want to burn DVD-RAM, but still....

There is also this, which isnt really current but its enough for me to lose respect for plextor- 

> Plextor has introduced 'protected commands' (Q-Check functions) in PX-755 and PX-760, which control features such as GigaREC and SilentMode quality checks. According to Alexander Noé, developer of PxScan and PxView, the commands were designed to prevent these features from being used on alternative operating systems and applications. The commands in question are implemented in the standard MultiMedia Command Set - 3 (MMC-3) command set, so they are not really secret. However, the drives require retrieving a code, then sending another one, calculated from the received one, back to the drive; otherwise, those commands are rejected by the drive.

In May 2005, Alexander Noé and Eric Fernandez (under the name zeb), the author of PxLinux, received a letter from a legal firm based in Brussels on behalf of Shinano Kenshi, the Japanese company that develops PlexTools and PlexTools Pro, for removing the software. The letter accused Noé and zeb of:
Using "unfair commercial practices" because they allegedly compared and announced that their software is an alternative for PlexTools.
Harming the company's "good name and fame" because of the alleged comparisons between PxScan and PlexTools.
Infringing various intellectual rights of the company, including "The right of reproduction, translation, adaptation, arrangement and any other alteration of a computer program and the reproduction of the results thereof as well as the right to control all and any form of distribution and dissemination. Infringement of the author rights (and where applicable, copyright) in relation with protected interfaces. The trademark of the company".

[http://en.wikipedia.org/wiki/Plextor](http://en.wikipedia.org/wiki/Plextor)

Good luck with your system, it should go like a rocket ;)

---

### Post by casbahdk on 2011-03-06
Thanks for the heads-up. I have often used both LiteOn and Plextor products without ever having had any problems. In fact, I use a Plextor external DVD drive with my netbooks that have Linux Mint 9 installed. No problem at all.

I will  give this a serious look, however. I take very seriously attempts at DRM. There have been a number of cases (Sony, Intel) where people have been prevented from using legally purchased material. That is _the_ most important reason as to why I never considered building an Intel powered box.

Fortunately, we have a guaranteed right to demand our money back for products purchased on the Internet, that we aren't satisfied with as long as the company is located in the EU :)

How do I test if the DVD-RAM works on the "Plextor"?

---

### Post by mick8985 on 2011-03-06
I've bought a few motherboards from Overclockers, they don't steal your cables, if anything you'll get more sata cables than you require, so I wouldn't bother buying extra ones, I've had sata cables packaged with my HD's too.
Incidentally I have 2 sata dvd drives in my box along with 4 sata hd's and I've never bought a sata cable.

---

### Post by casbahdk on 2011-03-07
> **mick8985 said:**
> I've bought a few motherboards from Overclockers, they don't steal your cables, if anything you'll get more sata cables than you require, so I wouldn't bother buying extra ones, I've had sata cables packaged with my HD's too.
Incidentally I have 2 sata dvd drives in my box along with 4 sata hd's and I've never bought a sata cable.

Thanks for the information :)

---

### Post by casbahdk on 2011-03-07
One thing I am wondering about is how many of the people on this thread are using an AMD64 version of Linux. Any advice for when I install a system on my new box? I understand that there are some things with the AMD64 systems that aren't yet up to snuff, like an AMD64 Flash version only being in beta. Is there other software that isn't available in AMD64 versions? What do you do? When you add PPA's to your system, do they automagically default to an AMD64 version of the software if it is available?

Cheers.

---

### Post by mastablasta on 2011-03-07
AMD64 is a 64 bit version of the system it can also run 32bit applications. sometimes slightly slower, but usually just normally as 32bit would. 
 
32 bit maybe has a bit more compatibility with older stuff but things are changing. i think going for 64 bit would be safe.
 
PPA sometimes applicaitons have two verisons but mostly they just use 64bit libraries.

---

### Post by casbahdk on 2011-03-07
> **mastablasta said:**
> AMD64 is a 64 bit version of the system it can also run 32bit applications. sometimes slightly slower, but usually just normally as 32bit would. 
 
32 bit maybe has a bit more compatibility with older stuff but things are changing. i think going for 64 bit would be safe.
 
PPA sometimes applicaitons have two verisons but mostly they just use 64bit libraries.

Thanks

---

### Post by cascade9 on 2011-03-07
AMD64/x86-64 here. 

Flash might be 'beta' but it works, as well as flash on linux ever does (and at least some distros actually give the the 64bit flash in the repos, I dont know why ubuntu doesnt....it might be connected to the whole 'we advise 32bit' thing they do) 

I havent had any issues with 64bit software since I've been using it.  

> **casbahdk said:**
> How do I test if the DVD-RAM works on the "Plextor"?

Get a DVD-RAM disc and try it, thats the only way. 

If you havent order the DVD drive yet, I'd really just get a liteON, last time I saw plextor drives they were 2.5x more expensive than the LiteONs they were rebranded from.

> **mick8985 said:**
> I've bought a few motherboards from Overclockers, they don't steal your cables, if anything you'll get more sata cables than you require, so I wouldn't bother buying extra ones, I've had sata cables packaged with my HD's too.

The better retailers don't remove the cables, I thought that overclockers UK wouldnt, but its nice to know for sure.

---

### Post by casbahdk on 2011-03-07
Thanks for the reply.
> **cascade9 said:**
> AMD64/x86-64 here. 

Flash might be 'beta' but it works, as well as flash on linux ever does (and at least some distros actually give the the 64bit flash in the repos, I dont know why ubuntu doesnt....it might be connected to the whole 'we advise 32bit' thing they do) 

I havent had any issues with 64bit software since I've been using it.  

Sounds good.

> **cascade9 said:**
> Get a DVD-RAM disc and try it, thats the only way.

Noted 

> **cascade9 said:**
> If you havent order the DVD drive yet, I'd really just get a liteON, last time I saw plextor drives they were 2.5x more expensive than the LiteONs they were rebranded from.

I received it today. It was very cheap. I can always return it. I have been looking at Overclockers, but everything seems to be BluRay or OEM :( Same problem locally. That is also why I went for the Plextor - I have no interest in BluRay.

---

### Post by cascade9 on 2011-03-07
> **casbahdk said:**
> I received it today. It was very cheap. I can always return it. I have been looking at Overclockers, but everything seems to be BluRay or OEM :( Same problem locally. That is also why I went for the Plextor - I have no interest in BluRay.

If it was cheap, less of a problem. (like I said, all the plextors I've ever seen have been very expensive). 

Same here, no intrest in blu-ray at all. Maybe in a few years when the discs are much cheaper I might, but for now commerical DVDs and DVD-R/DVD-RW does just fine.

OEM drives are what I try to get actually. The normally come as just a bare drive, the retail packs tend to have a cable, CD audio connector, and some form of burning software. Sometimes you even get odd parts like a tool for ejecting the tray if it gets stuck (a paperclip can do the same job). Since I've got cables, dont use the CD audio connector, and use linux burning software thats just fine for me.

---

### Post by gordintoronto on 2011-03-07
> **casbahdk said:**
> One thing I am wondering about is how many of the people on this thread are using an AMD64 version of Linux. Any advice for when I install a system on my new box? I understand that there are some things with the AMD64 systems that aren't yet up to snuff, like an AMD64 Flash version only being in beta. Is there other software that isn't available in AMD64 versions? What do you do? When you add PPA's to your system, do they automagically default to an AMD64 version of the software if it is available?

Cheers.

64-bit 10.10 is your best bet. If you want to run lm-sensors to see how warm your Phenom II CPU is, it works right away with 10.10 but is a hassle with 10.04. I've been using 64-bit for almost two years with no hassles. I install Ubuntu, install the restricted extras, everything "just works."

---

### Post by casbahdk on 2011-03-08
> **cascade9 said:**
> If it was cheap, less of a problem. (like I said, all the plextors I've ever seen have been very expensive). 

Same here, no intrest in blu-ray at all. Maybe in a few years when the discs are much cheaper I might, but for now commerical DVDs and DVD-R/DVD-RW does just fine.

It is nigh on impossible to find an optical drive locally that isn't BluRay. I think my drive is part of some stock the company hasn't been able to unload.

> **cascade9 said:**
> OEM drives are what I try to get actually. The normally come as just a bare drive, the retail packs tend to have a cable, CD audio connector, and some form of burning software. Sometimes you even get odd parts like a tool for ejecting the tray if it gets stuck (a paperclip can do the same job). Since I've got cables, dont use the CD audio connector, and use linux burning software thats just fine for me.

Now that is interesting. I hadn't though of it that way.

---

### Post by casbahdk on 2011-03-08
> **gordintoronto said:**
> 64-bit 10.10 is your best bet. If you want to run lm-sensors to see how warm your Phenom II CPU is, it works right away with 10.10 but is a hassle with 10.04. I've been using 64-bit for almost two years with no hassles. I install Ubuntu, install the restricted extras, everything "just works."

That is an interesting point that you brought up. Do users feel the need to monitor the temperature of their AMD processor? Does everyone use lm-sensors?

---

### Post by casbahdk on 2011-03-08
Does anyone have a suggestion for a TV card that will work with this PC configuration? I need something that supports DVB-C and PAL format broadcasts. There is no plan for this to be an HTPC, I just want the ability to see TV while I am doing other things.

I have seen some recommendations for the Hauppauge HVR-1600, but I have also seen other postings suggesting that this card doesn't work very well with Linux.

---

### Post by mick8985 on 2011-03-08
> **casbahdk said:**
> Does anyone have a suggestion for a TV card that will work with this PC configuration? I need something that supports DVB-C and PAL format broadcasts. There is no plan for this to be an HTPC, I just want the ability to see TV while I am doing other things.

I have seen some recommendations for the Hauppauge HVR-1600, but I have also seen other postings suggesting that this card doesn't work very well with Linux.

According to the [list at the mythtv wiki]("http://www.mythtv.org/wiki/Digital_Tuner_Cards") you have 2 choices 1 PCI and 1 USB.

PCI: [TechniSat CableStar 2]("http://linuxtv.org/wiki/index.php/TechniSat_CableStar_2_PCI_/_Cable4PC_PCI")

USB: [Sundtek	MediaTV]("http://www.linuxtv.org/wiki/index.php/Sundtek")

There is a list of technisat retailers in this [pdf]("http://www.technisat-daun-fs.de/downloads/sources_of_supply/list-of-specialist-retailers_COM_02-2011.pdf") None of them Danish I'm afraid.

I set my location to copenhagen and did a [google product search]("http://www.google.co.uk/products/catalog?hl=en&safe=off&q=TechniSat+CableStar+2&cid=10559827577960190073&ei=LpR2TaiNAYiaxAXY88ifBw&sa=title&ved=0CAcQ8wIwADgA#p") which shows 2 retailers online, both German.
ComEuro is the cheaper one, and has 528 ratings in google mostly positive.

Incidentally as per software I used to have a DVB-T card at university, and the only software I found usable for watching tv while doing other things was Kaffeine, this was on KDE 3.5 I have since not used KDE very much, but I have yet to see a decent gnome solution for DVB aside from the media center software. 
I have no idea what Kaffiene is like now in KDE4 but it's what I would recommend, whether your a Gnome or KDE user.

---

### Post by gordintoronto on 2011-03-08
> **casbahdk said:**
> That is an interesting point that you brought up. Do users feel the need to monitor the temperature of their AMD processor? Does everyone use lm-sensors?

I'm using a system I built myself. One of my design parameters was to have good airflow to keep the components cool. Lm-sensors lets me see whether I met my goal, and it turns out that I did. (The highest temperature during normal operation is 50 C, and that's the video card.)

Some portion of the people who post problems here, have problems caused by overheating. If they don't see the temperature, they probably don't know why they have a problem.

---

### Post by cascade9 on 2011-03-09
> **casbahdk said:**
> It is nigh on impossible to find an optical drive locally that isn't BluRay. I think my drive is part of some stock the company hasn't been able to unload.

I doubt it....

AFAIK DVD-RWs are still coming of production lines. I know I've got far more DVD/DVD-RW options than blu-ray where I go. 

Maybe you just haven't found the right retailer? I really dont know for Denmark. But here a lot of the cheaper places with a largeer range of stock are in semi-industrial areas, or tucked away in corners, not 'high street' retailers.  

> **casbahdk said:**
> That is an interesting point that you brought up. Do users feel the need to monitor the temperature of their AMD processor? Does everyone use lm-sensors?

I dont. 

I give a computer hell when I 1st get it, and check the temps fairly often. Once I'm sure that its not going to overheat, I stop bothering checking temps much, and just check every now and again (mainly if I'm getting some issue). By 'every now and again' I mean once ever week max....

---

### Post by mick8985 on 2011-03-09
Whoa, hold on I didn't read the wiki properly. 
That device is not supported, DO NOT buy it.

[http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards#Currently_Unsupported_DVB-C_PCI_Cards:](http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards#Currently_Unsupported_DVB-C_PCI_Cards:)

---

### Post by casbahdk on 2011-03-09
> **mick8985 said:**
> Whoa, hold on I didn't read the wiki properly. 
That device is not supported, DO NOT buy it.

[http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards#Currently_Unsupported_DVB-C_PCI_Cards:](http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards#Currently_Unsupported_DVB-C_PCI_Cards:)

No problem. I ordered the following card, which is recommended by local Linux groups:
Mystique CaBiX-C2, DVB-C, HDTV, CI-Connector, Windows/Linux
[http://www.dvbshop.net/product_info.php/info/p2258_Mystique-CaBiX-C2--DVB-C--HDTV--CI-Connector--Windows-Linux.html]("http://www.dvbshop.net/product_info.php/info/p2258_Mystique-CaBiX-C2--DVB-C--HDTV--CI-Connector--Windows-Linux.html")

---

### Post by casbahdk on 2011-03-20
I just put together the computer with some help from my brother in law who is an electrician. I am experiencing three major problems at this time:

1) The Cooler Master fan jerks at start-up, but never starts spinning. Should this run all of the time or is it controlled by a thermostat?

2) Nothing shows up on the monitor. I don't have another computer that can use PCI express cards, but my brother in law has tested whether electricity is reaching the graphics card, which it is.

3) The reset button doesn't seem to have any effect.

I am not sure if the above problems are interrelated or separate issues. The only thing that I am sure of is that the electrical connections have been triple checked and seem to be OK. I will however admit that I felt the mileage for the documentation for the different bits varies a lot.

Does anyone have an idea how I can sort these issues out?

---

### Post by cascade9 on 2011-03-22
The CPU fan should spin all the time AFAIK. No fans spinning = not booting. So you wont get video output, and reset wont do anything. 

You probably wont be getting any BIOS beeps either, because its not booting. (though if you are getting any beeps at all, the pattern could give you a hint as to the problem). 

I'd try unpluging everything apart from 1 stick of RAM and the video card, and see if that helps. If it doesnt.....maybe you are shorting out somewhere? You can always just remove the motherobard from the case, put it on the box the board came in and trying it there, if there is a shorting problem from the case then that should fix it. BTYW, I always use a screwdriver to start the computer when I benchtest on a box, you just touch the 2 pins that the power switch connects to with the screwdriver blade (or anything made of metal that conduces eletricky should work).

---

### Post by piquat on 2011-03-23
Fan jerks, nothing on the monitor, **reset button doesn't work.**
 
The reset button not working along with apparent booting problems makes me wonder if you have all the wires to the header on the board in the correct position.  Those pins, all in a row, usually have shoddy explanations for what each does and it's sometimes a pain to decipher what they're trying to tell you.  I know I've hooked up a few wrong in my time.

---

### Post by casbahdk on 2011-03-23
Thanks for the replies. The problem was that there is an extra power socket on the top left side of the motherboard that needs to be connected to the power source. Everything seems to be fine now. I'll install the system this weekend and take it for a test ride.

Thanks again.

---

### Post by casbahdk on 2011-03-24
Any recommendations for a keyboard to go with this system? I have been unable to find anything in the motherboard documentation about using USB keyboards at startup. Is it possible to use keyboard combinations to access the BIOS or edit GRUB settings at boot with a USB, wireless or bluetooth based keyboard, like with a PS/2 keyboard?

---

