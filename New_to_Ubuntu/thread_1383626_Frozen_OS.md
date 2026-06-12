---
title: "Frozen OS"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by jnmjr on 2010-01-17
Hey Guys, recently I switched from Firefox to G.Chrome to  "speedup my internet experience", but, I've been experiencing complete freezes after watching youtube videos or news clips, sometimes 3 videos other times 10, its really random, I need to shut power to reboot, usually some corruption visible after 1st reboot must reboot second time to correct, also I updated to 9.10 2.6.31-17 from 31-14 at roughly the same time, mind you this had never ever happened when I used Firefox.... anyone experiencing these hangups? Suggestions? THX.

PS: I would really want to keep Chrome, it's so much faster than FF.

---

### Post by VastOne on 2010-01-17
> **jnmjr said:**
> Hey Guys, recently I switched from Firefox to G.Chrome to  "speedup my internet experience", but, I've been experiencing complete freezes after watching youtube videos or news clips, sometimes 3 videos other times 10, its really random, I need to shut power to reboot, usually some corruption visible after 1st reboot must reboot second time to correct, also I updated to 9.10 2.6.31-17 from 31-14 at roughly the same time, mind you this had never ever happened when I used Firefox.... anyone experiencing these hangups? Suggestions? THX.

PS: I would really want to keep Chrome, it's so much faster than FF.

Remove G Chrome and try Chrome from Synaptic to see if there is a difference.  It is the same thing with more frequent updates

---

### Post by jnmjr on 2010-01-17
> **VastOne said:**
> Remove G Chrome and try Chrome from Synaptic to see if there is a difference.  It is the same thing with more frequent updates

What would be the best way to remove Chrome completely so I could re-install from Synaptic? THX.

---

### Post by VastOne on 2010-01-17
> **jnmjr said:**
> What would be the best way to remove Chrome completely so I could re-install from Synaptic? THX.

sudo apt-get remove google-chrome-unstable

---

### Post by jnmjr on 2010-01-17
> **VastOne said:**
> sudo apt-get remove google-chrome-unstable

I don't have the Unstable version installed, I did find in Synaptic the Beta version which I did a complete uninstall, then Re-installed. Beta is the only one aviallable rtight now. THX for your replies and hopefully it will work. I will see if it freezes again, but like I said before, it's random. I will post again if it happens. THX again.

---

### Post by mk1w86 on 2010-01-17
If you still have problems with Chrome you could try Chromium which is the open source build of it and is updated daily. ;)

You can install it from the Ubuntu PPA:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by jnmjr on 2010-01-17
> **mk1w86 said:**
> If you still have problems with Chrome you could try Chromium which is the open source build of it and is updated daily. ;)

You can install it from the Ubuntu PPA:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

So far so good, I appreciate your suggestion but I would rather stay away from this one for now. THX:P

---

### Post by baddog144 on 2010-01-17
> **jnmjr said:**
> So far so good, I appreciate your suggestion but I would rather stay away from this one for now. THX:P

Why? Chromium works perfectly for me on 9.10

---

### Post by ssulaco on 2010-01-17
> **mk1w86 said:**
> 
You can install it from the Ubuntu PPA:

I installed Chromium via the PPA and it worked flawless....and yes it was faster at rendering pages and flash compared to Firefox,Chromium outscored Swiftfox  2 to 1 when I ran both of them at **Peacekeeper**....just my 2 cents worth.

---

### Post by jnmjr on 2010-01-17
> **baddog144 said:**
> Why? Chromium works perfectly for me on 9.10

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

"The package is still a work-in-progress, so is Chromium, please be patient".

This is a quote from their site. Doesn't inspire great confidence yet. I don't want to end up in a possible worst position, for now lets see if the re-installation of Chrome works. As we all know Karmic has proven to be fairly buggy so I'm being careful not to rock the boat. I've run 15 straight clips so far OK. I'll try it again tomorrow. THX:D

---

### Post by jnmjr on 2010-01-18
Well Fellers, seems problem is cured, ran extensive tests on video clips from Youtube and no problems to report, looks like uninstall-reinstall did the trick. Thanks all for your suggestions they are very much appreciated.

---

### Post by VastOne on 2010-01-18
> **jnmjr said:**
> Well Fellers, seems problem is cured, ran extensive tests on video clips from Youtube and no problems to report, looks like uninstall-reinstall did the trick. Thanks all for your suggestions they are very much appreciated.

I would still highly recommend that you use Chromium and not G Chrome

Why?

No google influence (not saying this is necessarily good or bad) and more frequent updates/fixes/improvements....

I have run both and decided that the Chromium from the suggested ppa was hands down superior

---

### Post by jnmjr on 2010-01-18
> **VastOne said:**
> I would still highly recommend that you use Chromium and not G Chrome

Why?

No google influence (not saying this is necessarily good or bad) and more frequent updates/fixes/improvements....

I have run both and decided that the Chromium from the suggested ppa was hands down superior

 Ok you convinced me, I installed Chromium, now a couple of Q's:

1) Need to import all my bookmarks from G.Chrome.....Cant find file if you know how please advice. So far only available imports are from FF.

2) will the updates come automatically now, or is there something else I've got to install? Such as a repository!!

---

### Post by jnmjr on 2010-01-18
> **jnmjr said:**
> Ok you convinced me, I installed Chromium, now a couple of Q's:

1) Need to import all my bookmarks from G.Chrome.....Cant find file if you know how please advice. So far only available imports are from FF.

2) will the updates come automatically now, or is there something else I've got to install? Such as a repository!!

RESOLVED Q1, Q2 still open, 

Chromium seems to running good!;)

---

### Post by jnmjr on 2010-01-18
> **jnmjr said:**
> RESOLVED Q1, Q2 still open, 
 
Chromium seems to running good!;)
 
I just experienced catastrophic failure, had a hard time getting back to Ubuntu, so far non of the browsers work, got to figure out how to get back atleast FF.
 
Chromium is Elephant Do Do!!!!!!! Stay Away.......All was working well until I installed Chromium. It even caused changes in Grub. !WHAT A MESS!!!!!!!!!!!!!!
 
Now working from WinXP to browse!!:evil:

---

### Post by jnmjr on 2010-01-18
This thing is working like a windows VIRUS!!!!!!!!!!!

---

### Post by arubislander on 2010-01-18
Goes to show you that you should stick with what works for YOU while it is working for you. Don't commit yourself to what works for another simply because it works for them... If it aint broke don't fix it.

---

### Post by mk1w86 on 2010-01-18
> I just experienced catastrophic failure, had a hard time getting back to Ubuntu, so far non of the browsers work, got to figure out how to get back atleast FF.


What exactly happened during this failure and what errors are you getting now when you try to use Firefox etc.? :shock:

> 2) will the updates come automatically now, or is there something else I've got to install? Such as a repository!!


Chromium is updated daily from the PPA.

---

### Post by jnmjr on 2010-01-18
> **arubislander said:**
> Goes to show you that you should stick with what works for YOU while it is working for you. Don't commit yourself to what works for another simply because it works for them... If it aint broke don't fix it.

Your words are Bible!!!

To sum it up:

1) Had to reconfigure Grub
2) Removed all browsers completely
3) Removed AdobeFlash 
4) Re-installed one at a time, Epiphany, FF, G.Chrome, making sure
   each worked before installing next.
5) Installed AFlash, they all now play Clips.

I'm now back to where I was before this whole mess!!!:redface:

---

### Post by jnmjr on 2010-01-18
> **mk1w86 said:**
> What exactly happened during this failure and what errors are you getting now when you try to use Firefox etc.? :shock:



Chromium is updated daily from the PPA.

Read above Post!:frown:

---

### Post by arubislander on 2010-01-18
> **jnmjr said:**
> 4) Re-installed one at a time, Epiphany, FF, G.Chrome

You use Epiphany a lot? I had it installed once for a very brief period. Couldn't find much use for it though...

---

### Post by jnmjr on 2010-01-18
> **arubislander said:**
> You use Epiphany a lot? I had it installed once for a very brief period. Couldn't find much use for it though...

No, not at all until today, it was the only browser that worked some, so I used it, after I was able to boot back to Ubuntu from WinXP, to Google for some solutions. It had been there since I installed Karmic, unused.

The idea behind Chromium Browser is commendable, but if it causes "major malfunctions" it means it's not ready. Today is a holiday here in the US, so I had the luxury to fiddle around for over 2 hrs. "to fix what it broke". Normally, if you can imagine, I would have found it difficult to play around on a regular work day.

I use this computer for all my needs, business, play, etc., thank God I've never deleted Windows, it came in handy.... anyways I'm not mad at anybody, all of you out there have always helped me. THX.:)

---

### Post by jnmjr on 2010-01-18
[QUOTE=mk1w86;8686282]What exactly happened during this failure and what errors are you getting now when you try to use Firefox etc.? :shock:



I have had some time to reflect on the breakdown:

After the screen froze I couldn't reboot to Ubuntu so I went to XP.
For whatever reason and strangely enough, Xp automatically found my video card and re-installed it (GForce 8400 GS) don't ask I don't know. There I started looking up solutions without much success, other than uninstall everything and reinstall I had no other clue.

I closed XP and rebooted, this time Grub went to Ubuntu, I'm convinced that whatever XP did with the video card helped, again don't ask I haven't the slightest clue, during this bootup I saw a fast screen with some messages, and next some  messed up graphics then login, I did, and it took a long, long time while ubuntu went through a mess of checkups I had never seen before, finally the desktop. 

Non of the browsers worked, they would try to load and the screen would revert back to the desktop except for Epiphany which worked in some pages but not others, for example Google worked but I could not load the Ubuntu Forums it would revert to the desktop.

At this point I looked into Grub and there had been some minor configuration corruptions, such as the quiet splash line and the number on the stall time had changed from -1 (my setting) to a 10, well I reset all and saved it. Why this happened, go figure!.

Next I removed everything and reinstalled it as described in the other post, and viola! All is good again.

My personal conclusion is....Chromium caused a major corruption between the video drivers, Adobe Flash and it somehow spilled into the Bios and MBR, that was my comment about it "working like a Windows Virus". That's the Storyyyyy!!!:confused:

---

