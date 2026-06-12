---
title: "random system hang - at wit's end"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by echofaction on 2009-08-10
I had finally had it with windows, the love affair was long over.  I followed the advice of my wiser friends and installed the 9.04 version of Ubuntu.  Very excitedly I carefully followed the instructions on how to check my download, burn, install..  gasped with anticipation as the installation performed quickly and flawlessly...  grinned like an idiot when the login screen popped up...  and dutifully set myself to the task of opening my heart and mind to the beauty of Linux.

But then... 

Nothing happened.

Long story short I've been going through the forums endlessly on Live CD and trying desperately between crashes to resolve the problem, all while not really knowing what I'm doing, but eagerly trying to learn (I'm not giving up this easy!)

Specs: as it stands NOW
AMD 2400 chip (don't ask me for anything too fancy, I'm an artist not a nerd but I'm working on that)
AOPEN motherboard - ak77-400 max
Radeon 7000 AGP video card
512mb DDR ram

This is after ditching my previous ATI video card (the text looked all wonky and I had read a few threads about 3D graphics acceleration issues causing system hangs and crashes), removing half of my RAM because the other stick was much slower and didn't test well, getting a new HD for sh!ts and giggles,

I also gave Kubuntu a shot, the video was a bit better but after multiple installations of both Ubuntu and Kubuntu and upgrades and installs and putting in code the result is always the same.

Boot, login, hang.
Boot, login, run for five minutes, hang.
Hang during boot.
Boot login, hang.
Boot login, run for FIFTEEN MINUTES!...  hang.
no boot
Boot, login, hang.
And so on...

I have to admit after changing the video card out to an AGP card and pulling out the second, slower, iffy RAM, it has gotten a bit better, but I still have to reboot my computer about ten times to make it through the login screen, and then it's anyone's guess as to how long it'll run before it just stops in it's tracks again.  And it's really frustrating trying to troubleshoot when you don't know if you've got thirty seconds or thirty minutes to work with before it goes tits up.

I think it was for Kubuntu but I know ENVYNG does not support either video card - too old.  
I was pretty much chasing the video card issue this whole time until the RAM thing came up and it was running good for hours and I actually got to shut it down for once, thought I had it nailed until I came home from work today and it was back to square one.

Any suggestions out there?  I must be overlooking something obvious - my blonde roots are showing.

---

### Post by Threbus5 on 2009-08-11
That sounds very frustrating.

Perhaps something became corrupted during the install.

Anyway - does the system function well if it boots and runs from the Ubuntu install CD? If it does, then you might consider a system repair or a re-install from the Ubuntu CD. If the system fails and hangs while running from the install CD then disregard the instructions below and wait for help from a more knowledgable person. (Sorry)

If you want to try to repair possible scrambled files without a re-install try this -
1. be patient enough to login (hard to do I know)
2. bring up a terminal screen (that would be the textual command line screen)
3. enter on the command line:  sudo fsck   and press Return
4. enter your password and select yes to the prompts (they will attempt to correct corrupted files)
5. it may be necessary to execute steps 3 - 4 a couple of times.

then turn off the machine via the shut down option and restart - see if it works better
If it still hangs then perform a re-install

Good luck.

---

### Post by kerry_s on 2009-08-11
try a different distro. i recommend debian testing.
net installer:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by broncosis on 2009-08-13
I did the current install and much of the testing provided the agp video card 
and found the ram issue for her 

and when she left here we though she was good to go and she went home 
now as far as I can tell it maybe a bad power supply or crumy power 
at her location (lots of surges and brown outs)

she has been banned from these forums by over zelus mod's 
so she can't reply or update her situation 
but I will vouch for her my account was made a while ago 
while I don't post often as I don't have many issuses 
I do read lots and am very thankful for both these forums and ubuntu

---

### Post by nanotube on 2009-08-13
try running a memtest from the grub screen, to make sure the ram is good.

if the ram is good, another thing to try is turn off the desktop effects and run with plain metacity. under system-> preferences -> appearance, choose "no effects"

---

### Post by broncosis on 2009-08-13
she says thank you that seems to have helped some

---

