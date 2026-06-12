---
title: "Need help w/ installing Xubuntu"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Keizou on 2009-06-29
Alrighty, here's my situation:
- total linux newbie, I know pretty much nothing about linux so far
- found an old pent III comp with 256 RAM and 20 GB HD
- the comp has no OS on it so I thought I'd install Xubuntu since I heard some good things about it
- so I pop in the live CD and i test it out...everything works fine

The Problem:
- when I try to install xubuntu, the installation stops like 1/3 the way thru and says that it can't copy the files from the CD
- it then says that the CD might be damaged, CD drive is old etc.

Now, I'm not sure what to do. Is there any (uncomplicated) way I could install xubuntu via USB drive or anything else that doesn't require a CD drive

thanks in advance!

---

### Post by halitech on 2009-06-29
pendrivelinux.com has info on installing from a pendrive. My question is, does the machien support booting from USB?

---

### Post by stuart.reinke on 2009-06-29
I've encountered this problem also. First thing to do is test your install cd. It sounds like the ISO might be corrupt. The test option is on the main menu when you first boot the cd.

---

### Post by Keizou on 2009-06-29
> **halitech said:**
> pendrivelinux.com has info on installing from a pendrive. My question is, does the machien support booting from USB?

I kno this is a dumb ques: How to I find out if I can boot via USB

thanks for the help!

---

### Post by halitech on 2009-06-29
you'll need to go into the BIOS and check the boot sequence and see if USB is there. P3 I'm thinking probably not an option but can hope

---

### Post by AsusEEEPC on 2009-06-29
Well, go in your BIOS. Then go to Boot properties, boot device priority, then see if there is anything like USB drive or Removable Media in there.

---

### Post by philcamlin on 2009-06-29
i doubt there is an option in a P3 
wubi would work but you dont want windows too...

---

### Post by Keizou on 2009-06-29
another dumb ques: How exactly do I go "into" the BIOS?


also, as a side note: I've ran a check of the disc, it says that everything's OK

---

### Post by halitech on 2009-06-29
wubi and unetbootin would require windows to run and there is no OS on the system currently. If you have linux on another sytem on your network (assuming you have one) you could set up a PXE server and try to boot the system with a floppy (if it has one) to load from the other machine. Or take the drive out, install linux then pop it back into the original system.

---

### Post by halitech on 2009-06-29
> **Keizou said:**
> another dumb ques: How exactly do I go "into" the BIOS?


also, as a side note: I've ran a check of the disc, it says that everything's OK

depends on the system, some its DEL, some F1, F2 or F12 but you should see something when you power on about press key XX to enter setup

---

### Post by philcamlin on 2009-06-29
when your pc starts its a screen liek this 

[http://www.peacefire.org/bypass/booting-from-cd-tutorial/dell-setup.jpg](http://www.peacefire.org/bypass/booting-from-cd-tutorial/dell-setup.jpg)

try that  there is where youd get into the bios :popcorn:

---

### Post by Keizou on 2009-06-29
I found this tutorial: [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

only problem is that I have no OS, is it possible to use my xubuntu liveCD and follow the tutorial in the link above?

---

### Post by Keizou on 2009-06-29
> **philcamlin said:**
> when your pc starts its a screen liek this 

[http://www.peacefire.org/bypass/booting-from-cd-tutorial/dell-setup.jpg](http://www.peacefire.org/bypass/booting-from-cd-tutorial/dell-setup.jpg)

try that  there is where youd get into the bios :popcorn:

oh thanks, I guess i would need to use that tutorial....i'm gonna check rite now...

---

### Post by Keizou on 2009-06-29
looks like i can't do the F12...when my comp starts up, it doesn't says "F12" and when i press it, it just brings me to a screen where it says no OS found

---

### Post by halitech on 2009-06-29
F12 is for the boot menu, try F2

---

### Post by Keizou on 2009-06-29
> **halitech said:**
> F12 is for the boot menu, try F2

i tried F2, still get the same problem that I mentioned before

---

### Post by stuart.reinke on 2009-06-29
Is your computer a Dell?  Different brands use different methods to enter Bios.  For example I have an old IBM that requires me to hold the F1 key while it boots. Then it goes to bios.

---

### Post by -kg- on 2009-06-29
There are several keys that various computers (and BIOSes) use to get into the BIOS  setup menu.

When you come to the screen shown in the guide, look around the screen.  I usually see the indicated "F2, F12" information at the bottom of the screen.  Sometimes "Del" is used; sometimes "Esc".  You need to read that screen and find what key you need to press to enter your particular BIOS setup utility.

---

### Post by raymondh on 2009-06-29
> **Keizou said:**
> another dumb ques: How exactly do I go "into" the BIOS?


also, as a side note: I've ran a check of the disc, it says that everything's OK

See this link and browse for your system

[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

---

### Post by LewRockwell on 2009-06-29
> **Keizou said:**
> Alrighty, here's my situation:
- total linux newbie, I know pretty much nothing about linux so far
- found an old pent III comp with 256 RAM and 20 GB HD
- the comp has no OS on it so I thought I'd install Xubuntu since I heard some good things about it
- so I pop in the live CD and i test it out...everything works fine

The Problem:
- when I try to install xubuntu, the installation stops like 1/3 the way thru and says that it can't copy the files from the CD
- it then says that the CD might be damaged, CD drive is old etc.

Now, I'm not sure what to do. Is there any (uncomplicated) way I could install xubuntu via USB drive or anything else that doesn't require a CD drive

thanks in advance!

to figure out how to get into your machine's BIOS just google your machine's model number and "BIOS"...surely someone has posted it somewhere on the interwebs

it is entirely possible that your equipment is old enough that xubuntu will not perform satisfactorily(here again, googling your machine's model number and ubuntu will show...in short order...what other people's experiences have been)

with respect to your situation with the CD:

sometimes the disk checker says it's good when it isn't and we usually recommend rechecking the MD5 of the iso and reburning another CD at the slowest burn speed possible(we've even experienced "bad" blank CDs before which caused problems...good thing they are cheap now!)

the other thing you might do is to blow out your optical drive as sometimes dust gathers on the eye and causes problems

keep us posted

.

---

### Post by Keizou on 2009-06-29
when the comp boots up it just says "F2 configuration/setup", there's no indication of what to press to get into the bios

it's an IBM NetVista...i searched on the web and people are saying to press and hold F1...tried that but no luck

i'm gonna try cleaning the optical drive, maybe using one of those CD drive cleaners and see if that works...

as for checking the MD5...how exactly do you do that? (don't even kno what md5 is)

thanks for the help so far!

---

### Post by halitech on 2009-06-29
> **Keizou said:**
> when the comp boots up it just says "F2 configuration/setup", 

there is your answer right there

---

### Post by Keizou on 2009-06-29
I just found a solution but another problem popped up...

I went to my local dollar store and bought one of those CD drive cleaners. I used it to clean the CD drive and Xubuntu ends up installing completely. 

Shortly after I install xubuntu, i decide to install flash. during the installation of flash, my comp freezes and that some how srews up everything.

i restart the comp and then it says configuration changed...no OS installed 

so i try to re-install xubuntu but when i get to step 4 "Prepare partitions" (or something like that) and it's something I didn't see in my previous installation setup and I have NO idea what is going on! When I try to go to the next step, it says "No root file system defined. Please correct this from the partitioning menu."

i hoped my transition to linux would go smoothly but i guess i'm just out of luck:(

any help is much appreciated!

---

### Post by Keizou on 2009-06-29
help...anyone? :cry:

---

### Post by ecmatter on 2009-06-29
I've been fighting the same battle today (installing Xubuntu on a PIII with 256 Mb RAM).  It's not the easiest thing in the world to do.

I'll do my best to walk you through what I did to get mine up and running.

A couple of quick questions:

1. You're wanting to install Xubuntu alone (no dual boot) to the hard drive?
2. Are you willing to start over and install from scratch?

---

### Post by Keizou on 2009-06-29
> **ecmatter said:**
> I've been fighting the same battle today (installing Xubuntu on a PIII with 256 Mb RAM).  It's not the easiest thing in the world to do.

I'll do my best to walk you through what I did to get mine up and running.

A couple of quick questions:

1. You're wanting to install Xubuntu alone (no dual boot) to the hard drive?
2. Are you willing to start over and install from scratch?

1. Yes. I just want Xubuntu on it. I don't got any OS on it anyways.
2. Yes. Anything to get this up and running again.

thanks for the help!

---

### Post by -kg- on 2009-07-01
Hmmm...two days ago.  Well, if you're still with us, I'll pick up the football.

> so i try to re-install xubuntu but when i get to step 4 "Prepare partitions" (or something like that) and it's something I didn't see in my previous installation setup and I have NO idea what is going on! When I try to go to the next step, it says "No root file system defined. Please correct this from the partitioning menu."

What it sounds like to me is somehow "Specify Partitions Manually" was selected.  I am booted to an Xubuntu Live CD so I can give you exact guidance.

You have said you want to start over from scratch with a fresh installation.  That is probably the best and easiest course of action in your case.  Boot to the Live CD and you can either select to try Ubuntu and start the installation from the desktop (the default selection) or select install Ubuntu and start the installation directly.

Go through the first few screens (you know what to put in there) and just after Keyboard Selection you will come to the "Prepare Disk Space" screen.  I checked the next screen after selecting "Specify Partitions Manually" and indeed, it goes to the "Prepare Partitions" just as you said yours did and when I tried to go forward (without specifying the root partition, of course) I got the same error as you.  That is likely what happened.

When you get to the "Prepare Disk Space" screen you will be presented with four radio button selections:

o Install them side by side

o Use the entire disk

o Use the largest contiguous free space

o Specify partitions manually (Advanced)

Since you want to just do a fresh install (and since you have no other OS on the computer) you will want to select the second selection, "Use the entire disk."  Notice that under the "Entire disk" selection there is a drop-down menu (at least, there is on mine).  If you have more than one hard drive installed, you want to select "sda" (or hda, if it is so on your computer), which should be the default selection.

This selection will delete all existing partitions on that hard drive, create new ones for Xubuntu, and install Xubuntu into those partitions, so if you have more than one hard drive installed make *absolutely sure* that you have the right drive selected.

If you had Windows or another operating system installed that you wanted to keep and dual boot with, you would select the first selection, and if you already had sufficient free (unallocated) space on your drive, you might select the third.  You can select the 4th in either scenario, but you're expected to know what you're doing, as you will be shrinking, deleting, and/or creating partitions manually, as well as marking their mount points.

Enough extraneous information for now.  You'll learn all that.  Let's get you up and running.

Make sure you have "Use Entire Disk" selected and click forward.  I'm not sure what other screens you might go through (shouldn't be any more, but I don't know as I personally have always used "Manual partitioning"), but if there are any they should be self-explanatory.  The installer should then start installing Xubuntu using the entire disk.

OK, you said that this problem cropped up when installing Flash.  How did you install Flash?  From the repositories or did you get it from the Adobe website?  If you got it from the website, what distribution file did you get?  .deb?  tar.gz?

My advice is to use the repositories unless what you want is just not there at all.  Normally, apt and aptitude makes the installations safely and seamlessly, and takes care of any dependencies or conflicts.  .deb files will do this also, but .tar.gz (AKA tarballs) won't do this...you have to take care of all that yourself.

If you want the Flash plugin, I recommend you launch Synaptics and search for Xubuntu-restricted-extras.  Among other things that has the Flash plugin and works great.

There's the best way to go about what you want to do.  Hopefully you haven't given up on us yet!  Good luck!

Oh, and BTW, if you want to learn a little more about hard drives and partitioning, read at the link in my signature block.

---

### Post by Keizou on 2009-07-02
Hey there, thanks for the help. I was waiting for someone to reply. Since my last post, my situation has change a bit. Previously, I couldn't even access the step with the "use entire disk" option but I found out that if I just turn off my comp and restart the install, it shows up. But I've encountered another problem.....

So, I went to step 4 and selected "use entire disk" and I clicked forward.

However, I get yet another error while the installer is copying files to my HD: "Input/output error during write on /dev/sda"

I'm guessing that the failed flash install made my HD undetectable. I also tried to install windows XP and Puppy Linux, but I couldn't since both said it could not detect my HD.

Also, I installed flash using the repositories, not from the flash website. 

Anyways, your help is much appreciated. Hopefully you can help me further. I'm just getting pretty frustrated with this comp rite now (and linux, didn't kno linux was this frustrating), but I really want to bring it back to life. 

Thanks!

---

### Post by halitech on 2009-07-02
I'm wondering if the hard drive is toast. Try going back into the BIOS and see if it will auto detect the drive again. If it does you should be able to install. If it doesn't, you need a new drive (most likely)

---

### Post by Keizou on 2009-07-02
> **halitech said:**
> I'm wondering if the hard drive is toast. Try going back into the BIOS and see if it will auto detect the drive again. If it does you should be able to install. If it doesn't, you need a new drive (most likely)

I'm not sure if I'm doing the right thing.....I pressed F1 and went to config/setup > system summary. It says that I have a 20 GB HD installed (which is correct). So, I does my BIOS does detect it.

I should also mention that it says my HD has a configuration error (this happened after my failed instal of flash that crashed my comp).

---

### Post by halitech on 2009-07-02
is the drive setting on auto? I know on some systems you can set the drive info and even on a failed drive the BIOS will still say it has the drive (in fact I've removed drives and the BIOS has said it was still there)

The HD configuration error sounds like a clue to a dead/dying drive. Does it allow you to detect the drive from the error screen or the BIOS setup screen?

---

### Post by Keizou on 2009-07-02
> **halitech said:**
> is the drive setting on auto? I know on some systems you can set the drive info and even on a failed drive the BIOS will still say it has the drive (in fact I've removed drives and the BIOS has said it was still there)

The HD configuration error sounds like a clue to a dead/dying drive. Does it allow you to detect the drive from the error screen or the BIOS setup screen?


I have no clue if it's set to auto. 

I also have no clue how to enter the error or BIOS setup screen. (Sorry for being such a newbie)

Also, my situation has change (yet again). I formatted my hard drive (I thought it would help) by using my windows XP CD.  When I try to install xubuntu I'm back at the previous error I had before (see post #23).

I've posted screenshots so you get to see what I'm seeing when I get to step 4 of the install or when I open up gparted.

---

