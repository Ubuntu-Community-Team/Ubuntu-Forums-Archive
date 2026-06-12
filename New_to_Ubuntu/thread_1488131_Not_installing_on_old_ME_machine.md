---
title: "Not installing on old ME machine"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by freecomputer12 on 2010-05-19
Never had ubuntu before and wanted to try so went and bought an old ME clunker from second hand store. Has over 700meg ram and have ram to bring it over a gig. Actually runs fairly stable for an ME system, but wanted to get rid of ME and make a clean install with only ubuntu. Setup CD to boot and put in iso cd I made with other machine to install ubuntu. However had repeated failures to boot from cd. Tried other cds and they did play so made install of ISO read program just in case that was issue, also added several different cd/dvd drives just in case of mechanical error in cd drive.
 
Same issues with all, "failure to boot from CD". Note I did set it as first to boot in setup and it does try, but failure is result. After normal boot using ME it can read the cd . Thought about going with the usb install but looks like that uses a iso file as well...
Have read quite a bit about installs here in forum but may have missed the one thing I needed to know. Noted that some have had good installs using ME machines but wonder if there was some quirk about ME that needs considered. As I said only want this machine for ubuntu so am willing to start from scratch and go old school if needed and manually reformat drive, but don't want to end up stuck with nothing responding either. Any ideas?

---

### Post by SlidingHorn on 2010-05-19
I would check the md5 for your iso and make sure that you're burning the disk at the lowest speed you can set it to.  4x seems to work well

---

### Post by themusicalduck on 2010-05-19
The fact that it has ME installed shouldn't make any difference. It looks like you've tried most things, but you didn't mention if you had checked the md5sum of the iso file or the burned CD. I'm not sure how to check it on Windows, but you can probably find out quite easily.

Also, you should always burn Ubuntu at a low burn speed to minimise chance of corruption. Actually the Ubuntu CD almost always failed for me unless I burnt it at a low speed. If things still fail, then it might be worth downloading a new iso file.

Also, if you can install from a usb drive then it's still worth trying. It installs a lot quicker too and is less likely to corrupt as you don't need to burn to a CD.

---

### Post by ron999 on 2010-05-19
^^^^^^^^^

---

### Post by ankspo71 on 2010-05-19
what type or speed of processor do you have?
Windows ME was able to run on some very low spec processors, including my 200mhz AMD K6 processor in my old laptop. Unfortunately Ubuntu requires a recommended of 1 GHz x86 processor for the desktop (live CD) install as seen _[here]("https://help.ubuntu.com/community/Installation/SystemRequirements")_. I personally don't think the desktop cd needs that much CPU, (maybe 700Mhz?) but that is what they are now recommending.

The Aternate cd or Server cd can be installed with a 300 MHz processor.  

PS> Puppy Linux 5.0 is now using Ubuntu (lucid) packages. 
Hope this helps.

---

### Post by freecomputer12 on 2010-05-19
Fairly sure I did burn on slow speed as that is how I did most ISO files. Have Windows 7 on newest machine, and won't try any new ISO burning program on it as it crashes everytime I add anything.Tired of reinstalling 7. So will need to create an XP machine and install old Infra recorder on that to burn another. Already checked specs on Infra recorder and know it is not rated for 7, ugh. This could take a while.

---

### Post by dwalby on 2010-05-19
> **freecomputer12 said:**
>  As I said only want this machine for ubuntu so am willing to start from scratch and go old school if needed and manually reformat drive, but don't want to end up stuck with nothing responding either. Any ideas?
 
AFAIK the ISO boot disk you're using for the installation should be able to boot and run without finding anything on the HD, so reformatting isn't going to help. 
 
read this page [http://www.ultimatebootcd.com/faq.html](http://www.ultimatebootcd.com/faq.html)
 
There's a lot of useful suggestions there regarding your problem. Also I've read before that there are some older CD units that aren't capable of booting even though the BIOS allows it, but I'm not sure how to tell if that applies in your case or not.
 
Edit: Just read one of the newer posts and it got me thinking, its not necessarily the CPU speed that is the problem, but the instruction set that it supports.  Each generation of processors supports new instructions that weren't in the previous versions.  If the ISO executable uses instructions that are from a newer instruction set version than the processor you're running supports then that might also explain it.  Its able to boot from the CD, but can't figure out how to execute one of the instructions and dies.

---

### Post by halitech on 2010-05-19
you say you tried other cds and they play. Do you mean you have other bootable cds and they boot? when you browse the cd in Win ME, do you see a single file or a bunch of folders and files?

---

### Post by Jerry N on 2010-05-19
Something that is not clear - are you copying the .ISO file to a CD and trying to boot that or are you using image burning software to create a disk image from the ISO?  I normally use Nero on my Windows machines or NeroLinux on my Linux machines to do all my disk burning.  A lot of people advise burning very slowly.  I have burned many dozens of boot disks (100s?)with near 100% success and never have to resort to burning them at slow speed.  When I have had burn failures over the years, the problem has been marginal media or a failing CD burner.  The latest, just this week on my newest computer build, was a nearly unused LG burner that would not burn CDs - popped up error messages and quit before burning anything at all on the CD.  Reads CDs and burns DVDs ok though!  I replaced it with a new Plextor SATA burner and everything is just fine.   I think I will give up on LG!

Jerry

---

### Post by freecomputer12 on 2010-05-19
halitech,
    Have taken apart system as was a few hours ago to think on matter, had thought myself to try another rebootable disk, but did not try yet. When I reviewed the iso cd of ubuntu it showed many files.
 
Jerry N,
 
   Used infra recorder to burn the iso disk of ubuntu, now don't have that to use again as was on an xp machine, and won't work with ME or windows 7 in order to burn another copy.Have used infra recorder before with iso so should have worked, didn't hook up the ME system to net so didn't check md5, but also on my list of reviews for later.

---

### Post by candtalan on 2010-05-20
If you can boot the CD in any machine, the initial menu (press a key early to get menu if using 10.04) will include a CD self check, which is worth doing. If this checks out all ok then you know th edownload was ok and also the CD burn, an dthe reading in the testing drive is ok. However this does not fully answer the problem, because the best CD checks are done in the actual target drive.

---

