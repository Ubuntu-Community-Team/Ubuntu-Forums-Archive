---
title: "Lockups continue in 8.10"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by carusoswi on 2008-12-12
There is no pattern for these random lockups.  I thought it had to do with Firefox, so I tried Sea Monkey, Kahezekazi (spelling?).  Neither fixed the problem.  Then, I get similar lockups running open office or word in wine.

The computer might run a whole day without a problem, then, out of nowhere, it will lockup twice in an hour.

I dual boot to XP, and that OS can cruise the net or run any of my aps without crashing, ever.

I only mention this as I believe it rules out, for the most part, failed or failing hardware as a potential problem.

The machine is a Shuttle XPC, 2gb ram, plenty of HD Space (320+500 GB internally).

I have had similar experiences with 8.04.  The problem was not present for me in earlier versions.

What has happened to Ubuntu?  Have all the enhancements and new features come at the expense of tried and true, rock solid stability.

The greatest attraction of Ubuntu for me has always been the expectation that, no matter what combatibility problems on had to overcome, the OS would be free from crashes.

For me, that is, sadly, no longer true.

Am I alone?

Caruso

---

### Post by Peter09 on 2008-12-12
Could this be a particular application, such as firefox, which may be doing this?

---

### Post by robenroute on 2008-12-12
> **Peter09 said:**
> Could this be a particular application, such as firefox, which may be doing this?

I think the OP explained that he's tried alternatives for firefox...

Anyway, why don't you try a different distribution? Something like PCLinuxOS or Mepis? I'm not trying to steer you away from Ubuntu, it's just to get a better idea of what works with your particular hardware and what doesn't. Since you have plenty of HD space, you might want to consider SUSE as well. I used to have SUSE as my main desktop environment and was pretty chuffed with it. Friends of mine still use it and SUSE's latest seems very usable with excellent hardware support.

Good luck.

P.S. Have you tried looking at system log files (such as /var/log/syslog) just after the crash/lock-up? Don't just restart the machine when it happens; boot from a different partition/kernel or use a live CD to inspect the system log files.

---

### Post by gabkdlly on 2008-12-12
Please post the output of lspci

---

### Post by Kobalt on 2008-12-12
Lock-ups can be caused by faulty drivers as well, from hard drive to GPU drivers. I personnally experienced random lockups due to a faulty firmware in my optical drive... 
As a start, with the more obvious, which video card do you have, and which driver do you use (if you installed a particular one)?

---

### Post by carusoswi on 2008-12-13
> **Kobalt said:**
> Lock-ups can be caused by faulty drivers as well, from hard drive to GPU drivers. I personnally experienced random lockups due to a faulty firmware in my optical drive... 
As a start, with the more obvious, which video card do you have, and which driver do you use (if you installed a particular one)?

Thanks for the objective replies.  My video card is an ATI Radeon 9500.  I use the 'restricted' driver that automatically notifies me of its availability from the Ubuntu repository (I guess it's from the repository).  When I do a clean install of 8.10, although my graphics is pleasantly adjusted acceptably, this other driver presents itself as being available, and, if I follow the prompts, installs itself as a restricted driver.

I'll get back with my the output from the lspci (or whatever it was. . . can't look back from here) later this morning.  I'm in XP at the moment.

I wouldn't mind looking at other distro's, either, but find them hard to try out without messing up my system.  I tried to install Puppy a couple of weeks ago.  It 'redid' my grub, then stuck it where I couldn't even find it to edit it, and totally messed up the linux side of my dual boot.  Had to reinstall repartition and reinstall Ubuntu from scratch.

None of that is fatal, of course, but it is time consuming.  As we approach the holidays, I want to keep things simple on my machine so that I don't wind up doing what I often do around the holidays when everyone else expects me to be jovial/social.  Typically, I'm experimenting with my system, break it, and have to spend inordinate portions of the holiday rebuilding when most of the family would prefer to just be able to have me turn the thing on so that they can play games, surf, and laugh over silly utubes, etc.

There is, of course, nothing wrong with either activity (jovial/social vs geeky rebuilds), but the former tends to have a more endearing effect upon the family, LOL, especially the Mrs. who doesn't quite get my fascination with computers.

Thanks again for the advice.  I'll post back later.

Caruso

---

