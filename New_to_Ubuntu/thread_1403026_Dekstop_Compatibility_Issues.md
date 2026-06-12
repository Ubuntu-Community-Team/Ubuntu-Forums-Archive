---
title: "Dekstop Compatibility Issues"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-02-09
I am planning on building the PC below:

Motherboard + Processor: Gigabyte GA P55A-UDP4P + i5 750
RAM: 4GB Corsair PC3 1600mhz CL9
Hard Drive: 80gb Intel SSD + 1TB WD Caviar Black
Graphics Card: MSI HD5850 oc edition
DVD Drive: Lite-ON 24X DVDRW
Case: NZXT Hades Mid Tower
PSU: Corsair HX850
Cooling: CoolerMaster V8
LCD Monitor: LG 24" W2442PA

I've been doing my research mainly here [http://forums.hardwarezone.com.sg/showthread.php?t=2667555](http://forums.hardwarezone.com.sg/showthread.php?t=2667555), but no-one has been able to advise me on compatibility issues with ubuntu.

What I would like your help with is gauging whether all these components have good driver support in Ubuntu 9.10. I also need to know which PCMCIA wireless adaptor I should get, which is also compatible with Ubuntu.
Summary:
1.	MSI Radeon HD5850 – compatible with Ubuntu? Can I use dual screens?
2.	As it is 4GB RAM do I need to download the 64bit version of Ubuntu? Are there any major differences I should be aware of?
3.	Anything else I should know about?
Thanks!

Updated Specs: [http://spreadsheets.google.com/ccc?key=0AqEpmdlxbFPndDVCeTI4bnlUZmJibzF4WmFBVzh4eHc&hl=en](http://spreadsheets.google.com/ccc?key=0AqEpmdlxbFPndDVCeTI4bnlUZmJibzF4WmFBVzh4eHc&hl=en)

---

### Post by warfacegod on 2010-02-09
.01 I strongly suggest getting an nVidia Graphics card instead. Although ATi driver support is getting better it's still atrocious.

.02 Only if you want to. If you want to use all 4 GB RAM 64 Bit is the best but using a 32 Bit with a pae kernel will work too.

.03 Atheros chipset wireless is pretty well supported as is Ralink. Here's a good place to start looking:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by abhiroopb on 2010-02-09
Many thanks for that! Any particular nVidia card? Are they as good now and worth getting for such a powerful system?

---

### Post by warfacegod on 2010-02-09
> **abhiroopb said:**
> Many thanks for that! Any particular nVidia card? Are they as good now and worth getting for such a powerful system?

I'd go to nVidia's site and choose 4 or 5 of approximately the same performance and research which one works best in Ubuntu. From what I understand, nVidia has a small edge in the "Raw Horsepower" department.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> I'd go to nVidia's site and choose 4 or 5 of approximately the same performance and research which one works best in Ubuntu. From what I understand, nVidia has a small edge in the "Raw Horsepower" department.

Thanks,

I've just been informed that comparable nVidia cards (compared to the ATI HD5850) are not as good and way overpriced. Would you agree?

If this were the case I would be stuck using Windows 7 until there is better support for ATI.

---

### Post by abhiroopb on 2010-02-09
Just found this thread: [http://ubuntuforums.org/showthread.php?p=8721697](http://ubuntuforums.org/showthread.php?p=8721697)

Which suggests that the latest driver (9.12) supports the HD5850. Do you have any knowledge of this?

Thanks!

---

### Post by barkej on 2010-02-09
Steer clear of ATI if you can. The drivers are usable but they still leave alot to be desired.

---

### Post by abhiroopb on 2010-02-09
> **barkej said:**
> Steer clear of ATI if you can. The drivers are usable but they still leave alot to be desired.

In my opinion I would spend a little more for an nVidia card.

Thanks for that. To be honest I won't be heavily using the graphics card in Ubuntu. 

I will be dual booting with Win 7 and playing games etc.

All I need to know is that Compiz will run and I can use dual screens. 

I'm not too worried about performance issues and the like.

Also this is a desktop (in case I was unclear!)

---

### Post by warfacegod on 2010-02-09
> **abhiroopb said:**
> Just found this thread: [http://ubuntuforums.org/showthread.php?p=8721697](http://ubuntuforums.org/showthread.php?p=8721697)

Which suggests that the latest driver (9.12) supports the HD5850. Do you have any knowledge of this?

Thanks!

Whom ever told you that nVidia isn't as good is misinformed. Go to newegg.com and pick 3 each of ATi and nVidia of the same specs and compare the prices. I only know that there orders of magnitude more threads on help with ATi and Intel graphics as compared to nVidia. I don't use ATi because they just don't work well in Linux. I have two sitting in my spare parts box that gave me fits. My nVidia cards have always worked "out of the box".

I cannot stress to how likely it is that you'll be ripping your hair out trying to run Compiz because the ATi driver refuses to behave itself.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> Whom ever told you that nVidia isn't as good is misinformed. Go to newegg.com and pick 3 each of ATi and nVidia of the same specs and compare the prices. I only know that there orders of magnitude more threads on help with ATi and Intel graphics as compared to nVidia. I don't use ATi because they just don't work well in Linux. I have two sitting in my spare parts box that gave me fits. My nVidia cards have always worked "out of the box".

I cannot stress to how likely it is that you'll be ripping your hair out trying to run Compiz because the ATi driver refuses to behave itself.

Thanks for that.

I am considering the **_GTX 285_**...what do you think?

With respect to your opinion I'd like some other thoughts as well if anyone else is reading this thread!

---

### Post by warfacegod on 2010-02-09
When we first started discussing nVidia, I went to their site and the GTX 285 is one of a few that caught my eye. I looked and it runs on the 190 driver so I don't think you'll have any trouble with it.

You are absolutely correct in not accepting my opinion alone. (Besides the fact that I'm right. I'm always right. It's part of my divine sinister plot. Beeoowwaauuhhahaaahahahaaaa!!!!!)

---

### Post by abhiroopb on 2010-02-09
DX 11 support is a slight issue for me as well as the 285 does not support it :(

---

### Post by warfacegod on 2010-02-09
> **abhiroopb said:**
> DX 11 support is a slight issue for me as well as the 285 does not support it :(

I think the 295 does but that ones a bit pricey.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> When we first started discussing nVidia, I went to their site and the GTX 285 is one of a few that caught my eye. I looked and it runs on the 190 driver so I don't think you'll have any trouble with it.

You are absolutely correct in not accepting my opinion alone. (Besides the fact that I'm right. I'm always right. It's part of my divine sinister plot. Beeoowwaauuhhahaaahahahaaaa!!!!!)

Reviews seem to suggest that the ATI HD 5850 is much cheaper, runs DX 11 and is either just as good as the GTX 285 (some reviews) or better (other reviews).

Up till now everyone has recommended the HD5850 as the best one to get RIGHT now. nVidia may release DX 11 cards later this year but it’ll probably be at least another year before they are affordable anyway.

One thing I have learnt is that unless there is something incredible about to be released there is no point in always waiting around for tech. Every 3-4 months a company is about to release something new anyway so what is the point.
With that in mind while I appreciate your comments and taking into account that linux support is important, I don’t think it’s worth getting:

a)	An inferior card (as some reviews suggest)
b)	A more expensive card
c)	Something that doesn’t support DX 11

All for the sake of better Ubuntu support. It is important to me, but not enough that I’m going to compromise in other departments.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> I think the 295 does but that ones a bit pricey.

Yes that is way out of my price bracket!

---

### Post by Psyco430404 on 2010-02-09
assuming that your buying the card for basic use with in ubntu and basic gaming in windows 7 (nothing majorly draingin like crysis) why go wiht a card like that anyway, ive got a 9600gt that works wonders in my distro and for gaming, but yes the 285 is an excelent card, and there right, ati cards are a major headache....its generaly not worth it

---

### Post by mickie.kext on 2010-02-09
> **abhiroopb said:**
> 
I've just been informed that comparable nVidia cards (compared to the ATI HD5850) are not as good and way overpriced. Would you agree?
Currently, any NVIDIA card is better than 5850.
> **abhiroopb said:**
> If this were the case I would be stuck using Windows 7 until there is better support for ATI.
Then you might be sticking with Windows a long time.

---

### Post by warfacegod on 2010-02-09
Well, there you have it. Four? of us have recommended nVidia. (You see, I told you I'm always right!:P)

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> Well, there you have it. Four? of us have recommended nVidia. (You see, I told you I'm always right!:P)

I’m really struggling here. I love using Ubuntu and have been using it for about 4 years now (basically since I got my laptop). I have everything set up and it’s great. However, there are always hiccups. I have posted on these forums many times about how I always find there is something not working. For example, this morning my girlfriend called on skype and she could not hear me as the mic was not working. I couldn’t get it to work so I had to restart the computer. I’m sure similar things happen in Windows (and Mac). Anyway it’s a very difficult decision for me as I have everything set up just the way I like it in Ubuntu.

But, here is what I will do. I will buy the ATI HD 5850 see how Ubuntu works out (and if I can get drivers for everything). If things seem broken I am afraid I will have to become a Windows man (as much as I loathe myself for turning to the dark side).

---

### Post by warfacegod on 2010-02-09
Now young Skywalker...you *will* die.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> Now young Skywalker...you *will* die.

Now I have the pleasure of finding Windows apps that are better than my ubuntu ones :(

---

### Post by warfacegod on 2010-02-09
I can't think of *any*. When I switched 3 years ago I missed Windows Media Player 11 but then I discovered Amarok 1.4

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> I can't think of *any*. When I switched 3 years ago I missed Windows Media Player 11 but then I discovered Amarok 1.4

At least I'll have Skype that will work better and I use that a LOT.

Skype on Linux is a terrible experience!

But yes finding a new media player will be a hassle!

---

### Post by warfacegod on 2010-02-09
WMP 11 does pretty much everything. It doesn't do it all that well but it does do it. VLC is good too, no matter what platform it's on.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> WMP 11 does pretty much everything. It doesn't do it all that well but it does do it. VLC is good too, no matter what platform it's on.

Twitter/Facebook: Tweetdeck in both Ubuntu and Windows
Broswer: Chrome (or Chromium)
Music: iTunes
Video: VLC
IM: Pidgin (I can keep the same one!)
Office: OpenOffice (can keep the same one!)
Torrent: uTorrent

Seems like what I will miss most is rsync and bash in general

---

### Post by mickie.kext on 2010-02-09
> **abhiroopb said:**
> 
But, here is what I will do. I will buy the ATI HD 5850 see how Ubuntu works out (and if I can get drivers for everything). If things seem broken I am afraid I will have to become a Windows man (as much as I loathe myself for turning to the dark side).

Then you are setting yourself for a failure. HD5850 will not work before Ubunutu 10.10. It is not like GTX260 can't run games:D.

Abut your other Skype problem, you can't really blame Ubuntu for that. Skype is proprietary app and if they chose to do a lame port, there is nothing Canonical can do. You would be better off switching to some open protocol like Jabber:D.

---

### Post by abhiroopb on 2010-02-09
> **mickie.kext said:**
> Then you are setting yourself for a failure. HD5850 will not work before Ubunutu 10.10. It is not like GTX260 can't run games:D.

Abut your other Skype problem, you can't really blame Ubuntu for that. Skype is proprietary app and if they chose to do a lame port, there is nothing Canonical can do. You would be better off switching to some open protocol like Jabber:D.

I completely agree with you and for the most part I have been happily using Ubuntu. However, as of now everything seems (in my opinion) to be stacked up against Ubuntu and there seems to be almost no reason for me to continue using it. Bear in mind the switch back to Windows will be as difficult for me as someone switching from Windows to Ubuntu.

---

### Post by warfacegod on 2010-02-09
> **abhiroopb said:**
> I completely agree with you and for the most part I have been happily using Ubuntu. However, as of now everything seems (in my opinion) to be stacked up against Ubuntu and there seems to be almost no reason for me to continue using it. Bear in mind the switch back to Windows will be as difficult for me as someone switching from Windows to Ubuntu.

Are you planning on keeping a Linux machine around also? You've already got it on the machine you're on now, I presume.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> Are you planning on keeping a Linux machine around also? You've already got it on the machine you're on now, I presume.

It depends.

My laptop's battery is atrocious so I almost used it like a desktop (had an external keyboard, monitor and mouse). Now that I will have a desktop it'll be pretty useless as a desktop replacement.

I may buy a new battery and use it when I'm moving around, but it is quite heavy.

Not sure, but if I keep it then yes will continue using linux on it.

---

### Post by warfacegod on 2010-02-09
My laptop weighs 10 lbs. and the battery will go 45 minutes if I'm lucky.

---

### Post by abhiroopb on 2010-02-09
> **warfacegod said:**
> My laptop weighs 10 lbs. and the battery will go 45 minutes if I'm lucky.

Is that your way of saying life sucks? haha

---

### Post by warfacegod on 2010-02-09
> **abhiroopb said:**
> Is that your way of saying life sucks? haha

Actually, it's my way of saying I don't give a flying crap about the batteries' life sucking.:P

---

### Post by cascade9 on 2010-02-10
A Corsair HX850? Are you planning on running SLI or crossfire? Even if yuo are, 750watts shopuld be enough. 

> **warfacegod said:**
> I'd go to nVidia's site and choose 4 or 5 of approximately the same performance and research which one works best in Ubuntu. From what I understand, nVidia has a small edge in the "Raw Horsepower" department.
 
Not now they dont....see here (or half a doxen other benchmarking sites)-

[http://www.tomshardware.com/reviews/radeon-hd-5850,2433.html](http://www.tomshardware.com/reviews/radeon-hd-5850,2433.html)

You will find the odd game where the HD5850 is beaten by the GTX285 (fastest single GPU nVidia card now, the GTX295 is 2x 275s at 260 speeds). But once you crank up the AA/AF and/or resolution the HD 5850 comes back. 

But wait a bit for the GTX470/480 release (slated for march) and maybe that will change again. I'd probably try to hold off untill then, the GTX2xx cards will drop in price a fair bit, and its possible...probable? that ATI pirces will drop as well.  

> **abhiroopb said:**
> DX 11 support is a slight issue for me as well as the 285 does not support it :(

None of the nVidia cards do right now. Wait for the GTX470/480...again. 

I wouldnt worry about DX11 myself, its not like there are going to be _any_ DX11 only games for a few years. Its not that much better than DX10/10.1 anyway.

> **mickie.kext said:**
> Then you are setting yourself for a failure. HD5850 will not work before Ubunutu 10.10. It is not like GTX260 can't run games:D.

Pffft! to that. The drivers are already up on the ATI site. As well they should be, really, its been a few months. As to how well the drivers work, that might be a different question....

From the way that nVidia dropped the ball on the GT230, GTS240/250 and GTX275 (that one is fixed now) I wouldnt place any bets on the GTX4xx drivers being that brilliant on release either.

---

### Post by abhiroopb on 2010-02-10
> **cascade9 said:**
> A Corsair HX850? Are you planning on running SLI or crossfire? Even if yuo are, 750watts shopuld be enough. 


 
Not now they dont....see here (or half a doxen other benchmarking sites)-

[http://www.tomshardware.com/reviews/radeon-hd-5850,2433.html](http://www.tomshardware.com/reviews/radeon-hd-5850,2433.html)

You will find the odd game where the HD5850 is beaten by the GTX285 (fastest single GPU nVidia card now, the GTX295 is 2x 275s at 260 speeds). But once you crank up the AA/AF and/or resolution the HD 5850 comes back. 

But wait a bit for the GTX470/480 release (slated for march) and maybe that will change again. I'd probably try to hold off untill then, the GTX2xx cards will drop in price a fair bit, and its possible...probable? that ATI pirces will drop as well.  



None of the nVidia cards do right now. Wait for the GTX470/480...again. 

I wouldnt worry about DX11 myself, its not like there are going to be _any_ DX11 only games for a few years. Its not that much better than DX10/10.1 anyway.



Pffft! to that. The drivers are already up on the ATI site. As well they should be, really, its been a few months. As to how well the drivers work, that might be a different question....

From the way that nVidia dropped the ball on the GT230, GTS240/250 and GTX275 (that one is fixed now) I wouldnt place any bets on the GTX4xx drivers being that brilliant on release either.

I may run XFire later (as in upgrade). So, I'd rather prepare for it now.

---

### Post by Botruckle on 2010-03-20
I'm running Ubuntu 9.10 (64bit) and using an ATI HD 5850 and the latest drivers from ATI. No problems. Video for movies seems excellent. I don't have any hi-res games I can run on it, so can't report anything there.

---

### Post by bossdak on 2010-05-30
i have a 5770 and running 64 bit lucid. i have the following problems - delay in maximizing windows. video is choppy/stuttering in maximized window.

---

### Post by AMD_FTW on 2010-06-23
> **bossdak said:**
> i have a 5770 and running 64 bit lucid. i have the following problems - delay in maximizing windows. video is choppy/stuttering in maximized window.

Hello,

I am planning on buying the 5750 very soon.  I too am running 64bit Lucid on my nvidia 7600GT.  Did you have flawless video playback in maximized window and flawless maximize effects before purchasing this card?

I currently have dual head setup perfectly with no problems playing maximized 720p and no problems with compiz effects.

Do compiz effects work for you?  Which driver do you use?

-Zero

---

