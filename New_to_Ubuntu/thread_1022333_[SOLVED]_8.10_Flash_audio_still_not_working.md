---
title: "[SOLVED] 8.10 Flash audio still not working"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by djsjbh on 2008-12-26
Hey folks,

Has anyone solved the flash audio problem in 8.10? The pulse audio solution never worked for me.

Thanks

---

### Post by ercferret18 on 2008-12-26
hmm... flash works fine for me in 8.10. try playing a youtube video or something.

---

### Post by markharding557 on 2008-12-26
try changing to alsa

---

### Post by Stalker72 on 2008-12-26
I have the same problem. My speakers, Bose Companion 5, don't support ALSA though, only OSS. :(

Stalker72

---

### Post by EnGorDiaz on 2008-12-26
> **Stalker72 said:**
> I have the same problem. My speakers, Bose Companion 5, don't support ALSA though, only OSS. :(

Stalker72

my logitech ones support it just fine :P

---

### Post by kansasnoob on 2008-12-26
> **djsjbh said:**
> Hey folks,

Has anyone solved the flash audio problem in 8.10? The pulse audio solution never worked for me.

Thanks

So, for sure, you've been down this road:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I've had excellent luck with that, but ............ recently after an update Flash (and Flashblock) stopped working worth a poop!

I was once again unable to view flash videos, so I made the jump to Ubuntuzilla!

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

They have a page here:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

I don't know if that will help you or not but since installing the Ubuntuzilla version of Firefox I've had a much better experience with Flash and everything regarding Firefox!

Just a thought!

---

### Post by Warpnow on 2008-12-26
Same problem, can't find a fix...

Very annoying...

---

### Post by Warpnow on 2008-12-26
I fixed this by typing

sudo apt-get install flashplugin-nonfree-extrasound

and by typing

sudo apt-get remove pulseaudio

No idea which fixed it, but with those commands, it works.

---

### Post by djsjbh on 2008-12-26
Thanks for the input folks...

I tried everything other than installing ubuntuzilla...I guess I'll do that next. Nothing is working (ie flash audio still isn't working). I really love Ubuntu (everything else is great) but I have to stop short of recommending it because of this issue. Flash video on the web in now yester-tech and an OS not being able to play it out-of-the-box is an unforgivable sin...a deal breaker. The flamers who say Linux isn't worth the price (free) have a point.

Come on Con, fix it!

---

### Post by kansasnoob on 2008-12-26
> **djsjbh said:**
> Thanks for the input folks...

I tried everything other than installing ubuntuzilla...I guess I'll do that next. Nothing is working (ie flash audio still isn't working). I really love Ubuntu (everything else is great) but I have to stop short of recommending it because of this issue. Flash video on the web in now yester-tech and an OS not being able to play it out-of-the-box is an unforgivable sin...a deal breaker. The flamers who say Linux isn't worth the price (free) have a point.

Come on Con, fix it!

Just remember my problem was NOT sound related!

---

### Post by Warpnow on 2008-12-26
I had to reboot after doing what I said above before audio started working.

---

### Post by djsjbh on 2008-12-31
Problem solved folks. I did a clean install on Jan 1, 2009 and youtube worked fine. I think the problem may have been Skype. I downloaded it and changed some setting to accommodate the program. I must have cut off the flash audio sound when I did that. I'm marking this one solved.

---

