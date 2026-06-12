---
title: "64 bit still a headache?"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Northern Mike on 2011-03-20
Is 64 as polished as 32 now? (flash etc)

I have tried 64 bit in the past but got tired of the issues.  Since then I've always stuck with 32.   My friend wants to try Ubuntu now and has bought a dell desktop with 8 gigs of ram (the upgrade was part of the sale).   He is completely new to Ubuntu and I'd like to make sure Ubuntu has the same hardware advantage as his windows side.  I have not tried the 64 bit version of 10.04 yet.   Will there be issues as in the past or is it polished now?   He lives some distance from me so tech support will not be that easy and I'd like to make the Ubuntu experience painless.

---

### Post by oldos2er on 2011-03-20
64-bit flash is not in the repos, but it's fairly painless to install (see FlashAid in my sig). What hardware does your friend have?

---

### Post by Northern Mike on 2011-03-20
That was quick, I just came back to mention he has onboard video and an i3 3.2   As for the mother board we'll see once it arrives.

---

### Post by Locke_99GS on 2011-03-20
64bit flash is a little bit flakey, but tonnes better than it was in the past. Running 32bit flash with npwrapper works pretty well though.

Other than flash, I personally haven't had any issues with 64bit in a couple years or so.

---

### Post by cottfcfan on 2011-03-20
What issues have you had in the past?

---

### Post by stmiller on 2011-03-20
No issues on 64bit, but for a newer i3 intel video you may want a more recent version of Ubuntu that has a newer kernel.

Perhaps even running the 11.04 daily ?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Northern Mike on 2011-03-20
In the past if I recall correctly I had driver issues but mainly flash.   There was always a work around but that is the headache I am trying to avoid for them.

stmiller, I run 10.04 32 bit on a 16 gig memory stick as well and when testing it in a friends Acer i3 laptop to ensure everything was supported it brought in backport updates for the newer hardware.  Hopefully that will be the case for their system.   Too many things never seem to work right on the latest and greatest.

---

### Post by cmcanulty on 2011-03-20
I installed 10 laptops new at our lib with 64 bit. Big mistake, freezes up, wouldn't write a CD, missing printer drivers etc went  back to 32 bit was a big waste of time.

---

### Post by 5149.5 on 2011-03-20
+1 on the Flashaid for fixing flash issues.

---

### Post by tordeu on 2011-03-20
I have 10.10 x64 running and I do not even have problems with flash. (Other then the fact that you can not use full screen, if and only if you start a video, then change the resolution of your screen and then press change the video to full screen)

The only thing which comes to mind are using DVD-RAMs which does not work, but I have not really tried to get that working, because using a flash drive is just much more convenient.

---

### Post by PunkLV on 2011-03-20
Had been using x64 Debian for 6 months or so. Truth be told: never had a x32/x64 related problem or erorrs. 
Usual things like compiz/gnome do happen to have minor issues in the begging, but their source is architecture irrelevant and most probably my own actions were the cause. 
As for the last several months: I can't recall 'fixing' something.

---

### Post by bsharp on 2011-03-20
I've used 64 bit since at least 7.10, and probably before that but I can't remember for sure. Flash support is good, if anything check to make sure his printer is supported (this goes for 32-bit as well) because that was the biggest problem I ran into when installing for other people. Lexmark is not your friend.

---

### Post by sandyd on 2011-03-20
No problems in x64.

Just don't resize windows that contain a flash object, or click the fullscreen button.

If you want to watch youtube in fullscreen, then just input it into vlc ;) .

The only thing I had issues with was that somewhere on the line, while I wasn't looking, the WINE ebuild suddenly gained a 64bit flag. Which completely screwed my wineprefix when I ran it for the first time....

---

### Post by sandyd on 2011-03-20
> **bsharp said:**
> I've used 64 bit since at least 7.10, and probably before that but I can't remember for sure. Flash support is good, if anything check to make sure his printer is supported (this goes for 32-bit as well) because that was the biggest problem I ran into when installing for other people. Lexmark is not your friend.
Kodak ESP is not your friend either.
spotty support for some canon printer lines.

P.S. also check wireless card.
P.P.S. You can just use 32-bit ubuntu, all the RAM will still be used because ubuntu will detect that you are using 4+ GB of RAM and select the PAE kernel instead of the normal one.

---

### Post by tordeu on 2011-03-20
> **sandyd said:**
> No problems in x64.

Just don't resize windows that contain a flash object, or click the fullscreen button.


I can use fullscreen. But it works a lot better if I reduce the resolution of the screen first, cause flash really really does not offer the fastest video playback on the planet.

---

### Post by RedRat on 2011-03-20
> **bsharp said:**
> I've used 64 bit since at least 7.10, and probably before that but I can't remember for sure. Flash support is good, if anything check to make sure his printer is supported (this goes for 32-bit as well) because that was the biggest problem I ran into when installing for other people. Lexmark is not your friend.
Yes, Lexmark can be a problem in 64bit. I run 10.04 64bit on a System76 Serval Pro. I had a major headache in getting the printer drive for my new Lexmark 905 Pro. The driver that Lexmark provided is a bunch of scripts which did not want to run on Ubuntu 10.04, though Lexmark claimed it would. However, all that being said, working with BOTH Lexmark tech support and System76 (they have a forum here) we eventually got the driver to work. I had no problem installing the Lexmark Ubuntu drivers for 8.04, installed slick as a whistle. I think that Lexmark may have caught itself up on these problems, at least I hope so. 

Printers can be a pain in-the-you-know-where, Probably, if you are new to it and want a smooth installation and working system, maybe HP is the best bet. HP has been a supporter of Linux/Ubuntu. If I had to do it over again, I would probably go with the HP printer.

---

### Post by tordeu on 2011-03-20
I don't know how it is in general, but I had no problems with Samsung printers yet, either. But it's true that printers can be a problem. No wonder that when it comes to cheap printers where toner/ink costs more then the printer and where there is a new model every few weeks, most vendors only care about hacking together a windows driver.

---

### Post by bsharp on 2011-03-20
> **RedRat said:**
> Printers can be a pain in-the-you-know-where, Probably, if you are new to it and want a smooth installation and working system, maybe HP is the best bet. HP has been a supporter of Linux/Ubuntu. If I had to do it over again, I would probably go with the HP printer.

I agree, when it was time to get a new printer I did a little research and found HP is well-supported. I have a F4440(?) printer/scanner combo I got at Wally World for around $40 about a year ago and getting it running was very easy.

---

### Post by Northern Mike on 2011-03-21
Thank you all for the responses, I think I will just give him a copy 32 bit.   What might seem like minor issues for skilled folks to rectify can be deal breaker for someone else with little experience.  Not to mention if you get their spouse hating it.   More than 4 gigs is overkill anyway if you're not running a hog like Vista and as Sandy mentioned the PAE option is there. 

Thanks again.

Mike.

---

### Post by cottfcfan on 2011-03-21
I've recently gone back to 64bit, and find it rock solid.
In fact the 32bit Flash & nspluginwrapper, that is installed via the restricted-extras package, on my system appears to work just as good as in 32 bit.
Although i have to say that flash has never been brilliant for me anyway.

---

