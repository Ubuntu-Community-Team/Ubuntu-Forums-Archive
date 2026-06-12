---
title: "Is Ubuntu's video playing performance better than WinXP's?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by MikeFishcake on 2010-08-26
Hi everyone,

Recent convert to Ubuntu. 10.04 has really impressed me. Got it set up as main OS on my old Dell Inspiron 510m laptop, and as a VM on my main PC.

However - I've got also a Dell Optiplex GX280 (3GHz P4 CPU, 1GB RAM, integrated graphics) sat under my TV that I watch movie files and run retro console emulators on. It handles your average "tv quality" standard def Xvid files fine, and it's made a "good effort" at playing some 720p MKV files (using VLC player)

Apologies if this is a stupid question, but before I start farting around installing Ubuntu on this PC, is it likely that there's going to be any difference in video playing performance between WinXP and 10.04 on the same hardware? If it's going to be about the same (or slower :D), I probably won't go to the effort of but if there's a chance of getting smooth 720p playback on a system that can *nearly* manage it with WinXP, I'm more than happy to install Lucid Lynx on it (and then investigate the various console emulators that Linux/Ubuntu has to offer ;))

Cheers

Mike

---

### Post by QIII on 2010-08-26
Depends somewhat on the hardware.  Some OEMs produce good Linux drivers, some don't.  Even within cards from the same OEM, there are differences in performance using the same drivers.

My primary machine has an AMD/ATI card with the proprietary driver.  With Compiz off (using Metacity, which I do for video) using VLC, I get 1080p video quality that is every bit as good as my wife gets on her machine with Vista.

Your mileage may vary.  Remember that as much as many OEMs are trying to make good Linux drivers, a change in XServer or something like that can have them scrambling.

Don't listen to the ATI versus NVIDIA shouting and pissing matches.  AMD/ATI has their head in the game now and their drivers are quite good on their modern cards.  Older cards, produced before AMD bought ATI, can be extremely problematic.  Either OEM's recent cards will do.

That said, it may be worth your while to dual boot for a time and do some experimentation.  If you are not getting the performance you want for your multimedia in Linux, by all means use Windows.  There is absolutely nothing wrong with that.

---

### Post by khelben1979 on 2010-08-26
My guess is that your graphics performance are going to decrease by using Ubuntu instead of Windows XP. Other than that, if you enjoy using Ubuntu I'm sure that you're not gonna be dissapointed using it on that as well.

---

### Post by LowSky on 2010-08-26
Playing video files I would say Ubuntu is no better. 
Most of the playback is handled directly by the hardware, so maybe invest in more RAM and a cheap Nvidia graphics card. Any of the last three or model years for graphics cards will pay 1080P perfectly.


I'm not going to tell you Ubuntu is going to make things 120% better, it probably will not. I'm not going to tell you to upgrading to a newer OS is going to be better either. While I'm a fan boy for Linux I'm not zealous on trying to oversell anything that someone might not need.

Use Ubuntu if you need it. But it will not be any better for simple video playback.

---

### Post by MikeFishcake on 2010-08-26
Cheers for the feedback everybody - it's refreshing to read friendly an impartial advice relating to Linux. Had bad online experiences with Linux fans before now so it's nice to be spoken to like a human :D

Still enjoying digging around with Ubuntu anyway, been pleasantly surprised by some of the things it can do over Windows and Mac OS. Hopefully soon I'll be able to give advice to other people ;)

See you around!

Mike

---

### Post by Vaphell on 2010-08-26
Some people understand that it's better to describe the situation as is, if you overpromise and linux underdelivers for whatever reason it's ultimately harmful for linux reputation and we don't want that. It's better to have informed users who make the conscious choice and not clueless people who don't know what they are getting into and are destined to be disappointed.

to the point - video acceleration is pretty much a mess. Windows gets hardware acceleration (because of the HD mania there is a war who can squeeze more HD goodness out of the cheapass windows netbooks, thus drivers support it) and linux doesn't, companies point fingers at each other instead and we can't get reliable out-of-the-box acceleration in drivers, flash and whatnot. Video players like VLC or mplayer are excellent but they can't do much if the drivers suck and don't help, they have to eat CPU instead. Nvidia has its vdpau and reportedly it works, ati has some experimental stuff and it reportedly sometimes sorta works with some cards, other vendors - no idea.

---

### Post by no2498 on 2010-08-26
just my $.02 they both do not do mpeg video's well
i cant get any mpeg's to play
but we do have all the players there is
i think i just dont have some thing set right for me
the video's i look at play just fine
you may need to play with some settings a bit to get things set the way you like
a pet peeve of mine is you need to set/reset the

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.



and btw linux/ubuntu is a play ground for the programmers of windows and out the door

we spend no money to get the next upgrade

you can fix up your computer with the money you save

ok off my soap box now

enjoy the ride

---

### Post by jtarin on 2010-08-26
While I don't have an XP machine at home, rather I dualboot Win7 and Ubuntu and use VLC player in both. I find no diiference in playback. As you know VLC will play just about anything you throw at it. As mentioned its all about hardware. Have you tried booting the Live CD on the machine in question and playing video? While not an accurate benchmark it might be useful. 
My specs: 2ghz Dual, 1gb ram, Intel 945 graphics.

---

