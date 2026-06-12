---
title: "Video card purchase advice needed."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-09-20
Good evening,

Is the Nvidia Geforce 6600GT 6600 GT GF 512MB PCI-E Video Card overkill for me and my system? I'm not a gamer and just want the best from my HD monitor and for Google Earth to work properly, I also watch divx's pretty often.

Thanks a lot for any advice

PS I have done a lot of searching which brought me to the conclusion that Nvidia is the only way to go.

---

### Post by talsemgeest on 2009-09-20
Since to me it isn't a very good card (I am a gamer, so I may be a bit biased), so I would say it isn't overkill.

---

### Post by Liolikas on 2009-09-20
Newer may be much better and not much more expensive.. I mean something like 9600GT (something like 100$).

---

### Post by YoungTechie on 2009-09-20
I am a Gamer but even my Video Card is better then those and I bought it 4-5 years ago....Granted it was the best available when I got it... it should be far outdated by now.

---

### Post by 3rdalbum on 2009-09-20
> **tahitiwibble said:**
> Good evening,

Is the Nvidia Geforce 6600GT 6600 GT GF 512MB PCI-E Video Card overkill for me and my system? I'm not a gamer and just want the best from my HD monitor and for Google Earth to work properly, I also watch divx's pretty often.

The 6600 cards are OLD. And I think they only plug into AGP slots, too.

If your computer has a PCI-E slot (it's a long slot with what looks like a plastic lever on the side furtherest into the computer) then you realistically want a 9000 series Nvidia card. A passive-cooled 9500 would be fine if you don't play games. The 9000 series supports VDPAU, which gives you GPU-accelerated video decoding if you use Mplayer from SVN.

For the following video formats only: H.264, WMV9, mpeg2 and ( I think ) VC1. But that's still pretty good.

---

### Post by mapes12 on 2009-09-20
Hi

You could try searching the hardware compatability site for a card:

[http://www.ubuntuhcl.org/browse/search+video-cards?category=6](http://www.ubuntuhcl.org/browse/search+video-cards?category=6)

I have one of these with 256MB onboard RAM but it still can't play full screen video which it could when it was in an XP box. I guess it's a driver thing.

 > *-display               
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia


---

### Post by norm7446 on 2009-09-20
Before you buy have a look at the new AMD/ATI 4770. It's cheap it's almost top of the range in the budget department and I would say Light Years ahead of Nvidia card's at a similar price at the moment.

---

### Post by Liolikas on 2009-09-20
> **norm7446 said:**
> Before you buy have a look at the new AMD/ATI 4770. It's cheap it's almost top of the range in the budget department and I would say Light Years ahead of Nvidia card's at a similar price at the moment.
ATI Linux drivers development for Linux was not as good as nvidia. Not very good place to save here for Linux user. 
Maybe windos user may win few $ because his supacard works only on winxp.

---

### Post by 3rdalbum on 2009-09-20
> **norm7446 said:**
> Before you buy have a look at the new AMD/ATI 4770. It's cheap it's almost top of the range in the budget department and I would say Light Years ahead of Nvidia card's at a similar price at the moment.

The 4770 will not perform better than a similarly-priced Nvidia card if you use it on Linux.

Also, the 4770 won't work with Ubuntu 5.10, which you are apparently using :-)

---

### Post by Liolikas on 2009-09-20
Impossible he just forgot to update account info.
5 was first Ubuntu ever if I remember well. Released in 2005. With simple user killing problems like oh ma no luck with mp3. Automatic script maybe you still can find (do not try to run) man it was good times.

---

### Post by norm7446 on 2009-09-20
Ok, correct me if i'm wrong hear. To run UBUNTU you must use out of date hardware.

---

### Post by Liolikas on 2009-09-20
> **norm7446 said:**
> Ok, correct me if i'm wrong hear. To run UBUNTU you must use out of date hardware.
You are wrong.

At all I noticed most ppl fail to learn simple things like driver install and then think that hardware is unsupported.

---

### Post by sideaway on 2009-09-20
The newer ATi drivers aren't too bad. But yeah I'd still recommend an nVidia card atm. a second hand 9600gt or 9500gt should be a perfect fit to your needs provided you have a pci-e slot?

---

### Post by norm7446 on 2009-09-20
Thank God for that. If not then my PC is well over spec'ed UBUNTU and I would need to start looking for a copy of Windows7.

---

### Post by 3rdalbum on 2009-09-20
> **norm7446 said:**
> Thank God for that. If not then my PC is well over spec'ed UBUNTU and I would need to start looking for a copy of Windows7.

Windows 7 is for the victims of the Mojave Experiment. Trust me, I've tried it.

The only reason the Nvidia 6600 was brought up was because the OP doesn't have a lot of knowledge about hardware, and just thought "Nvidia works well on Linux" and "This is a cheap card".

I'm using an Nvidia GTX260 on this machine (not boasting, it's not worth boasting about). It's part of Nvidia's current line-up. Phoronix recently tested the as-yet-unreleased Intel Core i5 and an associated motherboard on Linux too, so Linux has no troubles with up-to-the-minute hardware as long as drivers are available.

---

### Post by tahitiwibble on 2009-09-21
OP says thanks to one and all for the info. It looks like I can get a 9500GT locally for about the same price a 6600 would cost to have shipped to me so it looks like .............. :)

---

### Post by norm7446 on 2009-09-21
Sorry for going of on a tangent with your thread, but glad that you have got some good advice.

---

### Post by tahitiwibble on 2009-09-21
> **norm7446 said:**
> Sorry for going of on a tangent with your thread, but glad that you have got some good advice.

Hey no sweat! 

But WOW!!!! what a difference, I ended up with the 9500GT at a price that couldn't be beaten (less than $100) and hooooooo weeeeeee ................. my programs in wine don't freeze any more, Google Earth is incredible, advanced desktop effects are sooooo cool, and I only installed the card 15 minutes ago (can't wait to install some real bells and whistles). The whole computer just runs way better! :P

PS Can someone tell me the name of the fancy 3D desktop effects programs. Thanks.

---

### Post by talsemgeest on 2009-09-22
> **tahitiwibble said:**
> PS Can someone tell me the name of the fancy 3D desktop effects programs. Thanks.
It is called Compiz Fusion, and is installed on the default Ubuntu installation. To enable it go to System>Preferences>Appearance then to the Desktop effects tab, and set it to what you want. If you want more control over your effects, install compizconfig settings manager, it is in the repositories.

---

### Post by tahitiwibble on 2009-09-22
> **talsemgeest said:**
> It is called Compiz Fusion, and is installed on the default Ubuntu installation. To enable it go to System>Preferences>Appearance then to the Desktop effects tab, and set it to what you want. If you want more control over your effects, install compizconfig settings manager, it is in the repositories.

Oh boy oh boy oh boy!

Did I imagine it or did my productivity just take quite a leap in the right direction. It's not just "eye-candy" is it! I actually feel like multi-tasking has come to roost :)

---

### Post by rmb938 on 2009-09-22
at least get a 8xxx series cards. all the others are to old and a waste. They are cheep I got my 8400 GS for $60

---

### Post by Sylslay on 2009-09-22
I read some time ago, that Nvidia 6200 is aktualy Nvidia 6600. 
There are some softwere,to chane BIOS, frimwere in thoese card.
I read that Nvidia 6600 has twice more "pipe" than 6200,
And both use the same chip.
I have Nvidia 6200 at my desktop and some games like fifa 2008 working smooth,
So if Yours budget is only for Nvifia 6600 go for it,
or try find what price is for Nvidia 9650 GT, 
chips with 105M, 130M, and 160M or 260M are to expensive at the momonet.

PS. Probaly card above geforce 8400 suport HD.

[http://www.videocardbenchmark.net/](http://www.videocardbenchmark.net/)

---

### Post by talsemgeest on 2009-09-22
> **rmb938 said:**
> at least get a 8xxx series cards. all the others are to old and a waste. They are cheep I got my 8400 GS for $60

> **Sylslay said:**
> I read some time ago, that Nvidia 6200 is aktualy Nvidia 6600. 
There are some softwere,to chane BIOS, frimwere in thoese card.
I read that Nvidia 6600 has twice more "pipe" than 6200,
And both use the same chip.
I have Nvidia 6200 at my desktop and some games like fifa 2008 working smooth,
So if Yours budget is only for Nvifia 6600 go for it,
or try find what price is for Nvidia 9650 GT, 
chips with 105M, 130M, and 160M or 260M are to expensive at the momonet.

PS. Probaly card above geforce 8400 suport HD.

[http://www.videocardbenchmark.net/](http://www.videocardbenchmark.net/)
Haha, it is usually best th read  th entire thread before posting, since the OP has already bought his card.

To the OP: Glad you are enjoying the effects. :)

---

