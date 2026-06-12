---
title: "CD-ROM couldn't be mounted using Alternate install CD"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Wayne Twine on 2009-05-26
Hi 
 
I tried installing Ubuntu 9.04 onto my PC with the Live CD. Got Busybox/imitramfs errors. Posted a thread on this forum and it was suggested that it may be something to do with video or graphics cards, so I downloaded the Alternate CD and and tried again. Now I get an error message saying "CD-ROM couldn't be mounted" and something about there not being a CD in the drive, which there was.
 
Any suggestions? I seem to be getting thwarted at every turn in my efforts to join the wonderful world of Ubuntu!
 
Cheers

---

### Post by Malta paul on 2009-05-26
Hi, Sorry to hear you are having problems.
Lets just start at basic.
 1)Can you boot you computer with the live CD?
 2)It is probably best if put Ubuntu on a separate partition, say
   an old Windows one you don't need and having first backed up
   MS files!  
 3)What graphic card have you got, you can uses the generic 
   driver first then install the driver for your card.

Let us know how you get on :)

---

### Post by Wayne Twine on 2009-05-26
HI there
 
Thanks for quick response.
 
Before I respond to your questions: I seem to have solved one problem, and caused another!
 
I have two Cd-ROM drives, (56X R and 52 x 24 x 52 RW).  I was trying to boot from the RW drive, as the other one gives trouble from time to time (e.g. doesn't always open).  However, I discovered in the BIOS that the 56X CD-ROM is set as the master and the RW as the slave.  So, I managed to get the master drive open, inserted the Alternate CD, and tried to boot again.  This time it worked.....got through resizing partition etc, BUT then I got an error message that it failed to select and install some software, and then the same problem for the GRUB.  I assume that's because the *&%$ CD ROM was giving trouble.  I eventually had to abort installation.  Now I can't boot into Ubuntu from the CD on EITHER of the CD ROM drives - it just boots into Windows!
 
Aaaargh!
 
Now to your questions:
 
1) I can't boot from Live CVD as I get imitramfs error (i've tried the various F6 options recommended).
 
2) I created a new partition during this last semi-successful installation from Alternate CD (I did back up my docs and settings).   I have 2 SATA  hard drives, C: as main drive and D: to backup my docs and settings.  It seems that the Ubuntu partition editor selected the D: drive instead of the C: drive as the default for repartitioning and installing, because when I went back into Windows XP, the capacity of C: was unchanged but D: had shrunk!  Not a train smash but I assume it would be best to run both Windows and Ubuntu on the C: drive and keep D: for backing up and sharing files? 
 
3) I have a NDVIDIA GeForce Ti 4200 with AGP8X graphics card - does that sound right (I am not a computer techie)?
 
Thanks for your help.

---

### Post by Malta paul on 2009-05-26
Well as you now have a working CD drive with your BIOS set up, I would first put in your CD and do a disk check to see if your disk itself has as defects?
good luck:)

p.s. Grub can get mixed up in identifying the partition you wish to boot from. At the grub menu press 'e' and try some more disk settings. Then 'b' to boot, this will not not change anything permanent  only for that boot so you can try as many times as you like!

---

### Post by Wayne Twine on 2009-05-26
I solved the initial booting from CD issue: the booting order in the BIOS had changed such that HDD was above CD ROM drive, so I have  moved the working CD ROM to first place and it now boots from the CD into Ubuntu.
 
BUT, Ubuntu still can't mount this CD ROM when I try to install.  It seems to only be able to mount the CD drive which is set as master, and not the slave (and I don't know how to change the slave to the master).  Is this corerct, and if so, is there a way around this, since my master CD ROM drive seems to be dodgy?

---

### Post by Malta paul on 2009-05-26
Sounds like a BIOS setting is required.
You can check if Ubuntu is recognizing your drives. I am at work at the moment using MS and can't correctly remember the command line codes. In the mean time download 'SysInfo' It's in Add/Remove repository. If you haven't got an answer by this evening I'll post you again. :)

---

### Post by NHArticleTen on 2009-05-26
> **Wayne Twine said:**
> I solved the initial booting from CD issue: the booting order in the BIOS had changed such that HDD was above CD ROM drive, so I have  moved the working CD ROM to first place and it now boots from the CD into Ubuntu.
 
BUT, Ubuntu still can't mount this CD ROM when I try to install.  It seems to only be able to mount the CD drive which is set as master, and not the slave (and I don't know how to change the slave to the master).  Is this corerct, and if so, is there a way around this, since my master CD ROM drive seems to be dodgy?

I think you're going to need to get your hands dirty if your bad optical device is the master.  I've had some CD-ROM drives go bad and they do get "dodgy" in more ways than one.

Let's operate:

-turn off and unplug from electricity(and take normal precautions when working with electronics regarding static and grounding)

-remove access cover(s) necessary to unplug, unscrew, and remove the optical drives(make notes as to how things were connected and/or take photos, etc)

-there are jumpers on the back of the drives, sometimes they are both set to "cable select" and other times one is set to "master" and the other to "slave".  Take the bad drive out and leave it out.  Make sure the remaining drive is set to "master" or "single"(note that sometimes a drive's "master" setting will be different from it's "single" setting...more common with hard drives than optical drives)

-ok, so you should have a single optical drive with the proper jumper setting reinstalled in the machine and plugged in to the last connector on the cable(obviously you'll reconnect the power plug to the back of the optical drive also)

...

your bios should auto-update but if it doesn't then you'll need to adjust it appropriately.

does it work properly for you now?


(also, and it can't be pointed out enough, MANY people have experienced frustrating problems simply because they did not burn their disk at the LOWEST burn speed selectable on their machine.  Never assume a disk is without error/damage until after you've successfully used it in multiple systems and optical devices.)

---

### Post by Malta paul on 2009-05-26
Hi Wayne,
To view the partitions that Ubuntu detects, Use 'sudo fdisk -l' in the terminal and see if both your CDROM's are listed.
:D

---

### Post by Wayne Twine on 2009-05-27
Thanks for responses
 
I burned the installation CD at 4x for the very reason NHARticle10 gave - was that slow enough? I did check the disk too.
 
Paul, I can't run sudo fdisk as I have not yet managed a full installation of Ubuntu - unless I can enter the command during install process.
 
Before I get the screwdriver out, could my NVIDIA GeForce 4200 card be the cause of the initramfs error when trying to install from the live CD? I tell you why I ask: Last night, out of frustration, I did a Wubi installation of Ubuntu in Windows just to get the feel of Ubuntu. My NVIDIA card caused untold trouble with graphics. The correct monitor could not be detected and resolution was wrong. I could not select medium graphics effects under Display. I downloaded and installed the recommended NVIDIA driver via Envy. The resoltion then improved but when I clicked on Display, it gave an error message about the driver not supoprting all extensions of the application and gave me the option of going to NVIDIA menu. However, there were not many settings I could change in the NVIDAI panel. 
 
After a few hours of reading forum threads and doing what they suggested, I uninstalled the Wubu installation, utterly dejected...I wish I had done the sudo fdisk -l when I had the chance though...
 
I'll wait for a response before fiddling with CD-ROM drives.
 
Thanks

---

### Post by Wayne Twine on 2009-05-27
SORTED,  Yeeah!

Guys, it was the slave/master CD-ROM issue that was causing havoc with my installation!  I changed the slave CD-ROM drive to master and vice versa by changing the pins at the back of the drives as suggested.  This resulted in the "good" CD that I was booting from now being the master, and the "dodgy" one the slave.  After doing this, I installed from the Live CD first time with no problems - didn't even need to try the Alternate CD.

Thanks for your help guys!

So, anybody getting "initramfs" errors when installing from Live CD, or "CD-ROM couldn't be mounted" when installing from Alternate CD, CHECK THAT THE CD-ROM DRIVE YOU ARE INSTALLING FROM IS THE MASTER, NOT THE SLAVE.

Now I just need to sort out that NVIDIA driver issue, but that's for another thread......

Later
:)

---

### Post by NHArticleTen on 2009-05-27
Glad you succeeded in solving your installation issue Wayne!

Now you might add "[Solved!]-" to the beginning of your title.

I also wanted to ask if, when you have time, you might browse the beginner forum and "pay it forward" as we all learn and grow.

A related story:

Gal gives me a "dead" computer. Won't even POST. She thinks it might be a bad hard drive. I don't think so but I keep my mouth shut(kinda like the driver, whose car won't start, saying "maybe the air in the tires needs changed"...in other words...THEY HAVEN'T A CLUE)

machine=up on test bench, side cover off
hook-up=keyboard, monitor, and mouse
plug-in=push power button

nothing except fans=scratch head briefly

unplug hard drive and cycle power=still nothing
unplug cd drive and cycle power=nothing
unplug dvd burner and cycle power=nada
unplug floppy drive and cycle=zip
remove modem card and cycle power=SUCCESSFUL POST
plug everything back in=working unit!

note to self: next time remember that if there is absolutely no POST then try board level add-on cards first.

(especially dial-up modems since they are MOST susceptible to damage from external sources via the "almost always electrically dirty" phone lines)

---

### Post by Malta paul on 2009-05-27
Hi Wayne,
Great news, well done mate
Paul

---

