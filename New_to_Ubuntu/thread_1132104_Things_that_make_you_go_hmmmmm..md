---
title: "Things that make you go hmmmmm."
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-21
Hey guys. I'm not sure if I'm posting this in the right place but I'm new to Ubuntu so I figured you guys would hopefully find it in your hearts to put up with my newb-ness. Well I just found out that my video card is no longer supported by Ati and the drivers for it in linux aren't all that great, I'm not overly happy about this, but what can ya do. So my question is, should I upgrade to another Ati card or should I go for a Nvidia which seems to have a bit better following with linux. Please help!

---

### Post by amingv on 2009-04-21
[personal experience]
So far I've had trouble with ATI and Intel cards but Nvidia cards always work fine with the proprietary drivers, so I'd say yeah, go with that.
[/personal experience]

---

### Post by Duskao on 2009-04-21
Yeah, thats kinda what I was thinking as well. Do you think that a 9800gt would be a good bet? I'm upgrading from a Radeon x1950 pro.

---

### Post by LowSky on 2009-04-21
9800 would be fine

---

### Post by Xero Xenith on 2009-04-21
nVidia cards have always served me well; I'm using a 9500 GT now. From what I've heard, if you can splash the extra cash, an upgrade to the new 2XX series would go a long way, but assuming a 9800 GT is more powerful than a 9500 GT (makes sense!), a 9800 should do you fine.

That is, assuming you're not seriously involved in gaming (and your interest in Linux seems to support my hypothesis that you're not :P).

---

### Post by Elfy on 2009-04-21
Personally I've not had any major issues with any nvidia cards - a small hiccup with an old card when intrepid was in development is all.

> Things that make you go hmmmmm.well to be honest - thread titles :D

---

### Post by Eisenwinter on 2009-04-21
I have an ATI Radeon 9200, I use the open source drivers, they work great.

Of course, I don't do any gaming, or use video editors, or anything of that sort.

---

### Post by Martje_001 on 2009-04-21
Read [phoronix]("http://www.phoronix.com/scan.php?page=home") and you'll know AMD/ATi is the only answer ;).

1. [http://www.phoronix.com/vr.php?view=13724](http://www.phoronix.com/vr.php?view=13724)
2. [http://www.botchco.com/agd5f/?p=43](http://www.botchco.com/agd5f/?p=43)
3. [http://www.phoronix.com/scan.php?page=news_item&px=NzIxNQ](http://www.phoronix.com/scan.php?page=news_item&px=NzIxNQ)

AMD/ATi have published all the information needed to build a driver and hires developers to develop them!

But of course, this won't be ready until Ubuntu 9.10. So;

Short-term: Go with NVidia
Long-term: Go with AMD/ATi

---

### Post by Duskao on 2009-04-21
Thanks so much for everyones opinions. I have been a bit of an ati fanboy for a long time now mainly because they are/were a canadian based company. But since my switch to Linux it has been a bit aggrovating to say the least. I mean to set up the drivers and all that is a snap, but then when trying to watch videos on my desktop there was a really nasty cutting and fluttering of the video, so then I found that I had to switch to X11 and I assume that is using the processor which kinda defeats the purpose of the graphics card in one aspect, and of course the quality reflected that. Then to gaming, I an not a hard core gamer or enthusiast but I do enjoy games once in a while. This was even a bit of an issue especially on certain games that are said to work fine through wine. I have tried and tried to get them to run, let alone run properly (half life 2, DOD source) and at one point had HL2 running in Ubuntu before I accidently pooched my system (still learning hehe) and had to reboot, but even then there was so much distortion I could barely tell what I was looking at. I think I may have hit the point where Nvidia is likely my choice for now. I just hope I have better luck with them then ati in the last couple weeks.

---

### Post by ajgreeny on 2009-04-21
> **Eisenwinter said:**
> I have an ATI Radeon 9200, I use the open source drivers, they work great.

Of course, I don't do any gaming, or use video editors, or anything of that sort.
+1, but then we are both using a very old card.  I'm not a gamer so it does more than enough for me; compiz -great, DVDs -great, Flash in Firefox -great, what more could I want?

---

### Post by LiamWilson on 2009-04-21
The 9200 card is an EXCELLENT card. I use it in my older PC, and it sure has served me well.

---

### Post by steve101101 on 2009-04-21
Intel is leaps and bounds beyond AMD and I have always used NVidia. Love them both.

---

### Post by xfearxnxloathing on 2009-04-21
9200 se pro is what i'm using now and have been for years, so odd such an old card can still run compiz fusion.  

Duskao, you could use restricted drivers and keep that card unless you just wanted to buy a new graphics card.  i also have an nvidia 8500gt in my other machine.

---

### Post by Duskao on 2009-04-22
well xfearxnxloathing, thats part of the problem. If I want to use restricted drivers all I can use are 9.3 and earlier because amd/ati has stopped supporting this card and the drivers that are avail with linux from ati need more work. Like I said, I don't game lots, but I do game some, so this is an issue for me.

---

### Post by Duskao on 2009-04-22
or maybe I have misunderstood. I'm used to windows where there is only the "one" real driver that gets updated monthly. But now with linux there is more then one... am I right??? Ok, so if I click on the "hardware drivers" it finds no drivers for me to use. So is there an open source driver that can enable OpenGL and allow me to play more graphically intensive games? If so then how do I do this? Please give me a bit of a walkthough. I'm assuming that this is not the driver that comes with Ubuntu when you first start it up because I can't run any graphically intensive games.

---

### Post by nandemonai on 2009-04-22
Nvidia 9800gt here and it runs great.

As pointed out earlier in this thread, unless Nvidia follow ATI with opening up their hardware then in the future ATI may be the way to go.

For now though I'd suggest sticking with Nvidia.

---

### Post by Duskao on 2009-04-22
With Ati opening up the hardware how does that help us out? Does that mean that people will be able to try to improve upon the existing drivers released by ati? Sorry guys. I'm such a newb.
So what is the best driver to use generally?

---

### Post by skymera on 2009-04-22
> **Duskao said:**
> With Ati opening up the hardware how does that help us out? Does that mean that people will be able to try to improve upon the existing drivers released by ati? Sorry guys. I'm such a newb.
So what is the best driver to use generally?

Yes, open drivers mean people can develop it.

For the moment go with Nvidia for more stability, my 8800GT used to run with no problems on 180 drivers.
Now i run Debian Squeeze 64bit with my HD4870, Compiz works fine but it's not quite as stable as my Nvidia was, some minor graphical glitches. But it's never failed on me :). Think my ATi driver is 8.6.

---

### Post by Godly on 2009-04-22
Nvidia no doubt. The 9500gt is pretty decent, big difference from Ati.

---

### Post by h4mx0r on 2009-04-22
A comparison of graphics cards based on the motorvehicle you drive.

ati- drag racer with crappy turning and many missing neccessary features but nice breakneck speed in the benchmarks
intel- what you might use when you go on vaction, very accomodating. Serves its purpose, hopefully good gas mileage for long trips.
nvidia- the fancy sports car with all the bling and extra features (since video cards are considered the flashiness aspect of the system this one usually prevails)
anything else- like driving a motorcyle naked and without a helmet

A comparison of graphics cards prices.

ati- best bang for your buck when buying performance
intel- lowest price
nvidia- long term support so less chance of future purchases
other- fun to tinker with, very expendible

---

### Post by markbuntu on 2009-04-22
The x1950 is fully supported by the open source ati driver. 2D acceleration and 3D are fully working for that card in the latest releases. Some people say the open source drivers are better for that card and other x1xxx cards than the driver from ati ever was.

ATI going open source was the best thing they could possibly do. It lets the community maintain the drivers which means more people working on them and more people being able to learn how advanced gpus work and how to write for them and faster response to problems. It also removes dependence on the manufacturer for driver updates and fixes.

In the next few months the open source drivers will have working 3D for the RV600 and RV700 cards. Accelerated 2D already works and preliminary 3D for the RV600 is already out.

Maybe someday nvidia will get 2D acceleration working for their cards or maybe HDMI audio.

---

### Post by Duskao on 2009-04-27
Hey markbuntu. Now here is my little problem, since I am a newb and all. How exactly do I get the open source drivers? I tried the X.org drivers from the add/remove and it buggered up my system and I had to reinstall ubuntu. So please give me a bit of an in depth lesson on where to find and how to install the open source drivers for my card. Please :D

---

### Post by Martje_001 on 2009-04-27
It's not recommended as a 'newbie' to install brand-new videocard drivers. You better wait for Ubuntu 9.10.

---

### Post by Duskao on 2009-04-27
Thanks for the reply. Even if it wasn't what I wanted to hear. On the other hand I don't want to trash my OS again.

---

