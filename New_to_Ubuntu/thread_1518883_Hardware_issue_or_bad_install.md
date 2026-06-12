---
title: "Hardware issue or bad install?"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by wenfuli on 2010-06-27
I'm running Ubuntu 10.4 on my sister-in-law's old laptop. It was a freebie as in her opinion it wasn't good anymore; she had been told it needed a new hard drive among other things. So, when I started having problems booting up (I wiped out Windows when I installed Ubuntu, right now Ubuntu is the only OS on the machine), I assumed the problem was the presumed faulty hard drive.
The problem is getting worse though. Now when I turn on the computer, I have to manually turn it off and turn it on again many times before it will actually boot up into Ubuntu. So now I'm wondering if maybe the problem isn't the hard drive but a bad install.
During failed boot-ups, the machine sometimes hangs on a black screen with a flat cursor in the top-left corner, sometimes it hangs after displaying what I assume to be memory address locations and error messages (I wish I could remember what they were right now, but I can't. I'll write them down next time if it's important.), and every once in a while I get a message warning of kernel panic.
So, I'm asking for opinions: Does this sound like a simple hardware problem, or did something go wrong with my installation? Would anybody recommend a complete re-install of Ubuntu?

---

### Post by warfacegod on 2010-06-27
If it's an HDD issue, you'll have no choice but to do a Fresh Install but let's find out first.

A good tool for finding HDD problems is:

```
sudo apt-get install gsmartcontrol
```

And running an Extended Test. This could take some hours depending on the laptop specs so maybe having few errands to run in the mean time would be wise.

Another thing to do is run memtest86 from the GRUB menu. Also several hours so the same advise applies. In fact for this one, you might just do it before going to bed.

---

### Post by kaldor on 2010-06-27
Also, check the specs; might be too heavy on an old laptop.

---

### Post by Chame_Wizard on 2010-06-27
How old is the laptop anyway?

---

### Post by wenfuli on 2010-06-28
Age of the laptop? Probably about three or four years old.

Specs: According to the sticker on the computer itself, 1.5 GHz Celeron CPU, 40 GB HDD (yeah, I know that's small), 256MB DDR2 (not much there, either) and an Intel Graphics Media Accelerator 900. Not overly powerful, but it was good enough to run WinXP before, so it should handle Ubuntu fine, I would think.

I ran gsmartcontrol and no errors were found. After the test, however, my machine seems to run a little faster and smoother, with the exception of the first restart after the test. My machine was quite slow when I restarted it shortly after running the test, but on the subsequent restart, everything seems to be better. Boot up went smoother too.

I installed GRUB, but I can't figure out how to do the memtest86. I'll keep looking around.

---

### Post by varunendra on 2010-06-28
All the symptoms you told in your first post are of potential hard drive faliure.

Not having exact knowledge of what happens in the background, I can only assume that it happens due to the problem in reading system files every now & then.

Yes the 256MB RAM is sort-of constrained for Lucid, but if you need to restart many times before booting process can actually proceed then it is most probably due to abnormal delay time in accessing boot-sector & boot-files.

One not-very-promising but complementary method to cross check hard drive status would be to perform a thorough surface scan from BIOS or in some Live CD environment and notice if the progression-speed of the scan process is constant throughout the whole process or there is huge variation at different places. If there is significant variation at certain places on HDD, then it is failing even if passes the test at that moment.

However, this is only a symptom & actual reasons may differ. Your best bet would be to backup data & make a fresh install of Ubuntu 9.10 or even older & stable version.

By the way, how is the performance when you run a Live Session?

---

### Post by Evanescence on 2010-06-28
Hi,
In my opinion, if it was a hardware issue then XP would have also had problems. Most probable cause of the issue you are experiencing is a poor install. Which option did you choose when installing it as a stand-alone OS? I have had such a problem before and it was due to  an improper formatting of the HDD. I would suggest you use a Live CD, and using Gparted, delete any partitions to leave the entire HDD unallocated, then you can exit Gparted and run a fresh install. That is my suggestion.

---

### Post by wenfuli on 2010-06-28
I haven't had time to run more tests or do a Live CD session (but considering this computer currently doesn't have a DVD drive -- it's external and my sister-in-law forgot to give it to me -- it would have to be a Live USB session), but I'm tempted to go with the bad hard drive verdict. It'll be  a couple days before I'll have time to check things out properly though.
This machine did have problems when it was running Windows -- that's the main reason she bought a new computer and basically through this one away. I've actually got it running better using Linux than it was running under Windows. Right now the only problems are freezes on boot up and occasionally getting a little slow. When it was a Windows machine, it would all of a sudden shut itself off and then restart, with no warning at all.

---

### Post by warfacegod on 2010-06-28
> 1.5 GHz Celeron CPU, 40 GB HDD (yeah, I know that's small), 256MB DDR2

CPU is a little slow but should be ok. The real issue is the RAM. For 10.04, the Recommended is 1 GB RAM. That isn't to say that some of the hardware isn't possibly failing, just that you don't have close to enough RAM and that could be causing your problem.

---

### Post by Dave68 on 2010-06-28
You might also check into Xubuntu. The System Reqs are a little leaner.
 
Mint XFCE 8. lists 256MB RAM as one of the minimum requirements. (Also similar to Ubuntu, but with Restricted Areas already installed.)
 
I'm not exactly sure what the Xubuntu Specs are, but I'm running it on two 5 year old machines with minimal issues. They have 512 MB RAM though.
 
It is still Ubuntu, but it uses the Xfce Gui, which is lighter than KDE or Gnome.
 
Just a Thought,
Dave

---

### Post by warfacegod on 2010-06-28
> **Dave68 said:**
> You might also check into Xubuntu. The System Reqs are a little leaner.
 
Mint XFCE 8. lists 256MB RAM as one of the minimum requirements. (Also similar to Ubuntu, but with Restricted Areas already installed.)
 
I'm not exactly sure what the Xubuntu Specs are, but I'm running it on two 5 year old machines with minimal issues. They have 512 MB RAM though.
 
It is still Ubuntu, but it uses the Xfce Gui, which is lighter than KDE or Gnome.
 
Just a Thought,
Dave

The new XFCE has almost no difference in system requirements than the other 'Buntu's. The LXDE environment is the only lightweight desktop Environment available for Ubuntu. Otherwise custom building an Install is the only choice. Even then, LXDE or Custom, 256 MB RAM is still pushing it.

---

### Post by wenfuli on 2010-07-03
Updated my RAM to 2GB. So far boot-ups have been better, but not perfect. On three boot-ups (one a restart) so far, the first two booted right up, the third froze twice before starting up. I'll have to wait and see if things stay improved like this or if they go back to how they were before. (A few times over the past few days I was wondering if my computer was ever going to start up.) At the very least, it's running much faster now.

---

