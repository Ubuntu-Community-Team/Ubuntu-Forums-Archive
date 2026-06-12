---
title: "Install with no network"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by anewguy on 2010-05-11
I'd like to put Ubuntu on my elderly parents' PC, as they currently have Windows and no matter what I do it seems they always get a virus or worm and it gets all screwed up.  This was the "nth" time around and I couldn't solve it over the phone - would need to be sitting in front of the PC (can't remote desktop - Dad got so ticked this time he has his internet terminated!).

So, what I'd like to do is some time go to visit them (I'm in Minnesota, they're in Arizona) and install Ubuntu, but I need wine and some other things as well, and I won't have access to the internet.  I need Wine because of some Windows programs they run that I know will run in Wine (I tried them) as I'm want to make the transition as painless as possible for them (they are just about 80 and not real patient on learning new things anymore).  So keeping their existing programs and running the via Wine is the easiest.

So.......is there some sort of "super DVD" or something I can download and burn (doesn't matter if it's more than 1 disk) that would have all kinds of packages and their dependencies on it so that I can just install via synaptic or apt-get?  Obviously I have the LiveCD's for 10.04 and going back quite a way, but it's okay if Ubuntu itself is included on the download as well.  I just want something simple to run from which I can install many things without a network connection or access to another PC (that is after I've downloaded what ever and burned it to media).

Any help/thoughts would be appreciated!

thanks in advance!
Dave ;)

---

### Post by ubunterooster on 2010-05-11
Install it to a new hard drive then take that drive and give them a new hard drive and OS at once :D

---

### Post by super kim on 2010-05-11
> **ubunterooster said:**
> Install it to a new hard drive then take that drive and give them a new hard drive and OS at once :D
this is an excellent suggestion, you can just send them a hard drive with everything set up ready. that's the best way to be sure everything you think they need is installed.

this is only possible with ubuntu, never try anything like this with windows. i took my friends pc home, re-installed windows, all worked fine and when i took it back...
the first problem was the different monitor...:guitar:

---

### Post by anewguy on 2010-05-11
I'm assuming that with the new X that it will find the different video card okay, how about sound - I shouldn't have much trouble configuring that should I?

I'm not sure exactly what the PC is, but I know it's about 6 years old or so, HP desktop, AMD 64 FX(?).  I know it has plenty of memory and disk space.  Only other thing I can think of is they have a now 6 year old or so Epson printer, and the last I checked (I've been using HP peripheals for quite a while now) Epson wasn't the easiest thing to get going in Linux.  Has any of that changed?  If worse comes to worse I'll bring an HP inkjet I have that I know works with Ubuntu (I was using it until my brother in-law gave me his old laser printer a couple of weeks ago).

Thanks again!
Dave ;)

---

### Post by ubunterooster on 2010-05-11
Epson still stinks. As for sound...it's likely to work but if it doesn't it's a pain even if you are able to get online

---

### Post by bredman on 2010-05-11
Have a look at APTonCD. It allows you to build your own CD of any extra packages which are not part of the standard install. The CD can be used by any program in the apt family, for example Synaptic.

APTonCD is normally used by sysadmins to bring software updates around to PCs which do not have network connections. I regularly use it to download large updates at work and bring them home, because my home internet access is pathetic.

---

### Post by anewguy on 2010-05-11
> **super kim said:**
> this is an excellent suggestion, you can just send them a hard drive with everything set up ready. that's the best way to be sure everything you think they need is installed.

this is only possible with ubuntu, never try anything like this with windows. i took my friends pc home, re-installed windows, all worked fine and when i took it back...
the first problem was the different monitor...:guitar:

Yeah, seems like Windows doesn't run if you even replace things like the motherboard with one not exactly like the one it was installed with.

As for sending the drive - well, that's out of the question.  We're talking 80-year old with no interest in getting inside the computer.

Sound - I really do assume it's probably someone's cheapy "Soundblaster compatible" and will probably work fine.

I would still rather just have a set of disks to take with me and install there.  It used to be years ago (very early 1990's) that you could get a series of disks with practically everything you might ever want to install.  I'd like to find something like that, but with packages that would work through synaptic so I don't have to go through dependency heck.

Dave ;)

---

