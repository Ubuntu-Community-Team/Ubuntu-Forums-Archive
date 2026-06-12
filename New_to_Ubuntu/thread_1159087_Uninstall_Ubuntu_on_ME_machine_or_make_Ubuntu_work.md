---
title: "Uninstall Ubuntu on ME machine or make Ubuntu work"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by merinda1 on 2009-05-14
I've seen similar threads but I can't figure out which apply to me, the main difference being that I have the Windows ME reinstall disks that came with my old computer.
 
I'll err on the side of too much information. I was one of those people who heard of Linux and that there was a human-friendly version and thought, *Cool, I'll install that on my old extra computer! *I guess I was a little naive. :) I installed Ubuntu 8.10 on my old HP xt919 Pavillion from a LiveCD I made on my main computer. The installation went great. Then Ubuntu completely froze when I tried to install updates (repeatedly) though it told me that there were scores of them I needed. It only crawled searching the web--maybe due to the updates it needed. Anyway, I decided to say goodbye to Ubuntu for now and reinstall my old Windows ME (which gives no recovery options except to wipe out the hard drive and start over).
 
Imagine my surprise when I returned to the room to find Ubuntu launched on my computer! When I restarted the computer, I saw that it had created a dual-boot configuration that gave me the choice to start with Ubuntu or Windows. Again, I thought, *Cool.* Eventually I saw that Windows was relegated to a tiny 2 GB on my 40 GB hard drive while Ubuntu saw 30 GB of free space. 
 
I tried installing the Live CD for the Ubuntu 9.4 hoping I'd be able to use that. The CD drive made small noises and would not boot the Live CD. Ubuntu 8.10 launched instead. I checked the drive by going into ME and viewing a .jpeg image from a CD. It worked. I reloaded ME just for the heck of it. It reloaded. So, clearly, I could still boot from CD. I thought there might be something I could do with the Ultimate Boot CD or the Ultimate Boot CD for Windows. Neither would load. My machine still displayed the dual-boot options for Ubuntu and ME.
 
I tried downloading Mbrfix while in Windows. I think it downloaded--what I got was a program that expressed concerns about my registry. When I typed the suggested commands like cd \ [ENTER] mbrfix /drive 0 fixmbr /yes. I just got "Bad command or file name."
 
So what now? I can neither go forward nor backward. I'd love Ubuntu if it would surf the web with the speed of ME (can't believe I'm saying that) or be happy if Ubuntu were gone and ME could see the rest of my hard drive.
 
Can you help me make Ubuntu go away?

---

### Post by BZF on 2009-05-14
[SIZE=1][COLOR=Blue]well first of all i dont know why you'd like millenium edition. if yu do want it back, just send it it and you'll get ur files back, or if u want ubuntu to work, then put the cd in and choose install ubuntu. also if ur cd drive is making wierd noises that means there may be soemthing wrong with it[/COLOR][/SIZE]

---

### Post by s.fox on 2009-05-14
Hi and welcome to the Forum,  

Have you checked your boot order in the BIOS?  Make sure CD is first option.

Also,  what are the specifications of your old computer?

-Ash R

---

### Post by mapes12 on 2009-05-14
You may find the answer to your situation here:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

On the basis that your PC does not contain any critical data and you are just looking to experiment then I would load GParted from a LiveCD, reformat the HDD, resetup my partitions (see the abve link) and do a fresh UBU install and go from there.

I can't see why your surfing speed is slow? Wifi or ethernet? If wifi then that's probably the problem. Try an ethernet cable and see how that goes.

---

### Post by Sef on 2009-05-14
How much ram does that computer have?

---

### Post by Niniel on 2009-05-14
So what do you want? Get rid of Ubunutu or make it work?
And how did you install Ubuntu the first time?
Your Computer not starting from the Ubuntu CD may mean that the CD is damaged - the fact that you can view an image on the CD doesn't really mean anything since it sounds like the part of the disk that facilitates booting is damaged. Burning disks can be a chore, e.g. it took me 4 attempts to get a working 9.04 CD. So don't give up and try to burn another CD. 
Oh, and before you even burn the disk, check the ISO-image for errors. You can do that by doing an MD5 checksum comparison (get [a program that does that in Windows]("http://www.pc-tools.net/win32/md5sums/") and then compare the number it spits out with what's on the download page).

---

### Post by NHArticleTen on 2009-05-14
try one of the distros that I have referenced in previous posts

if your machine ran ME then you'll be ok with DSL or Pup

I use them both and am still surfing the interwebs with a 1997 Gateway laptop (150mhz MMX / 224mb ram / 3gb platter / PCMCIA nic) running DSL

---

### Post by merinda1 on 2009-05-14
[SIZE=1]I wanted to change to Ubuntu from ME, I just couldn't make it work.  I tried to install 9.4, and it didn't work.  8.10 is still in the state it was when I loaded from the Live CD because I never could install the updates.  I have reloaded ME since I loaded Ubuntu, yesterday in fact, so the drive is working and booting first in sequence[/SIZE]

---

### Post by merinda1 on 2009-05-14
Thanks for replying, Ash.  My computer boots CD before the hard drive or I wouldn't have been able to load Ubuntu from the CD in the first place or reload ME, right?  I have a 40 GB hard drive, 384 MB RAM, and a 800 MHz processor.  I know these specs are low, but I thought I would enjoy the challenge of making Ubuntu run on it.

---

### Post by chrisod on 2009-05-14
With those specs, you might have more success with Xubuntu. I had it running great on a 1 GHZ / 18 MB / 512 laptop until the laptop died last week.

---

### Post by merinda1 on 2009-05-14
**[COLOR=black]mapes12,[/COLOR]**
 
Guess what, I've got an HP xt919 Pavillion and the first thing I found when I went to find the program you referred to was the following messages, so now I'm scared :)
 
[COLOR=#ff0000]///WARNING/// Due to a hardware/firmware bug, it's _NOT_ recommended to run GParted live on some types of HP Pavilion machines. Otherwise your VGA card fan might be dead. [/COLOR]
[COLOR=black][/COLOR] 
 As for networking, I have ethernet.  The other machines on my network surf fine and even ME surfed acceptably on my dual-boot Ubuntu computer.  Of course, I couldn't see anything that required Flashplayer (because ME is too old to have a modern Flashplayer written for it) which was a big reason that I wanted Ubuntu.  As far as I could tell from the Flashplayer website there is a version for Ubuntu.

---

### Post by merinda1 on 2009-05-14
384 mb

---

### Post by merinda1 on 2009-05-14
Niniel,
 
I'd like to make Ubuntu work, but maybe I'm in over my head.  I installed version 8.10 by burning a CD on my main computer and then booting my to-be Ubuntu computer.  I used WinMD5Sum to do my checksums on both the 8.10 and the 9.4 downloads.  The sums were correct on my hard drive.  When I loaded the 8.10 CD in my old machine, the first thing I did was to use the option that checks the disk for errors.  It said that there weren't any.  I couldn't do that with my 9.4 CD, because I never could get it to boot.  The checksums also added up on my Ultimate Boot CD and my Ultimate Boot CD for Windows, but neither will boot on my machine.  The only thing that still seems to boot from the drive is the re-install of ME. :(

---

### Post by Niniel on 2009-05-15
Do you really want to dual-boot with ME? Just asking, it's fine if you do. But it sounded like this was an extra computer, so why not put only Ubuntu on it? Of course, with ME on there you can practice dual booting. :)

By the way, the easiest (only?) way to upgrade Ubuntu would be from within 8.10, not by putting in a 9.04 installation CD. 

Regarding the CDs not booting, I really think that's just the CDs having problems. Unfortunately, that's not uncommon. But since the ISOs you downloaded are ok, you can burn them again (a slow burning speed, e.g. 4 x, may help). As I said, it took me 4 tries before I had a working Live CD in my hands (my first attempts also wouldn't boot, or only booted to a certain point and then died) and that I could use for installation (e.g. my 8.10 live CD worked as a live CD, but there was a disk error that prevented it from installing anything but the base system).
You can test the live CD on your main computer; it won't mess up anything, just don't click on "install". :)

---

### Post by merinda1 on 2009-05-16
Thanks to everyone on this forum who was helping me.  I think that perhaps my hard drive was going.  It got to a point that when I put in the ME installation CD, I was warned that the only way to proceed was to run fdisk, which I did-only choosing the most standard options (1,1).  After I ran fdisk (to enable it to see the whole drive and partition as one big partition), the hard drive only saw 1.7 GB to format (though I had 40 GB) when I put in the ME installaton disk this time instead of 2 GB (which it saw before).  The first time it wouldn't install and said that the contents of drive C: were unrecognized.  I tried it again, and it went through its installation but could not restart.
 
When it tried to restart, I briefly saw the Ubuntu startup screen.  Imagine, Ubuntu was still trying to live after fdisk!
 
Now it won't boot to anything.  That's okay.  I chalk it all up to experience. . .and have my eye on a new computer. ;)

---

### Post by NHArticleTen on 2009-05-16
> **merinda1 said:**
> Thanks to everyone on this forum who was helping me.  I think that perhaps my hard drive was going.  It got to a point that when I put in the ME installation CD, I was warned that the only way to proceed was to run fdisk, which I did-only choosing the most standard options (1,1).  After I ran fdisk (to enable it to see the whole drive and partition as one big partition), the hard drive only saw 1.7 GB to format (though I had 40 GB) when I put in the ME installaton disk this time instead of 2 GB (which it saw before).  The first time it wouldn't install and said that the contents of drive C: were unrecognized.  I tried it again, and it went through its installation but could not restart.
 
When it tried to restart, I briefly saw the Ubuntu startup screen.  Imagine, Ubuntu was still trying to live after fdisk!
 
Now it won't boot to anything.  That's okay.  I chalk it all up to experience. . .and have my eye on a new computer. ;)

sounds like a good time to run DBAN on your machine to zero out the hard drive.

get a copy of Puppy Linux and play around with it, you won't regret it!

---

### Post by egalvan on 2009-05-16
> **NHArticleTen said:**
> sounds like a good time to **[COLOR="Red"]run DBAN on your machine to zero out the hard drive[/COLOR]**.

**[COLOR="Red"]get a copy of Puppy Linux[/COLOR]** and play around with it, you won't regret it!

Absolutely agree with both of these recommendations...

A big [SIZE="7"]+1[/SIZE] for them!


[www.dban.org](www.dban.org)

[www.puppylinux.org](www.puppylinux.org)


Seriously, the memory on that machine is too low for 9.04,
 and marginal for 8.10 or 8.04.
Ubuntu is a MODERN, heavy GUI-oriented operating system.
It needs more memory to be happy.

On the other hand, Puppy is designed to run in 256Meg, so 384Meg will give you some breathing room.

I've run it on 128Meg.


Puppy is about 100Meg download.

[COLOR="Red"]TinyCore Linux[/COLOR], though, is only a [COLOR="Red"]**10Meg**[/COLOR] download.

[www.tinycorelinux.com](www.tinycorelinux.com)

quote from web-site...

[I]Tiny Core Linux is a very small (10 MB) minimal Linux Desktop.
 It is based on Linux 2.6 kernel, Busybox, Tiny X, Fltk, and Jwm.
 The core runs entirely in ram and boots very quickly.

It is not a complete desktop nor is all hardware completely supported.
 It represents only the core needed to boot into a very minimal X desktop typically with wired internet access.[/I]

Give both Puppy and TinyCore a try, 
you WILL be amazed at how they can transform old hardware.

---

### Post by egalvan on 2009-05-16
And if the hard drive is dead on your machine,

no worries!

Puppy and TinyCore will both run well as LiveCD,
although Puppy is probably a better choice in this case.

There a lots of different Puppy versions...

---

### Post by ugm6hr on 2009-05-16
My first true introduction to Linux was a LiveCD of PuppyLinux when my laptop HD was failing.

I'd recommend it.

Other options to consider:
Austrumi (very slick, but a bit annoying due to its non-English background)
Slitaz (not tried v2 though)
DamnSmallLinux

---

### Post by Niniel on 2009-05-19
I am not convinced yet that the disk is really broken, I rather suspect you weren't [using Fdisk correctly]("http://support.microsoft.com/kb/255867").
You see, pressing "1" just creates a new partition on empty space. It does nothing to existing partitions. 
What you need to do is start with "3" and delete all partitions that are on the disk. Only after that return to the main menu and create a new partition with "1". That should give you back the full capacity of the disk.
Using a graphical partitioning tool like [GParted ]("http://gparted.sourceforge.net/download.php")would probably be easier for you because the disk layout is visualized in a much more intuitive way. You can also use the Ubuntu Live CD, the partitioner is included on that.

So essentially, we are back on square one - I recommend you burn a new live CD. And I will say it one more time - it may take a couple of tries to get one that is without error. That has nothing to do with your second computer!
Unlike some people who posted here I do think your machine will be able to run Ubuntu, although it will probably be slow. It might just be fun to try and see how slow exactly. :)
And while I also like Puppy, an XFCE-based distribution may offer a bit more comfort to you - if you want to stay with the Ubuntu family, there's [Xubuntu]("http://xubuntu.com/"), but if you don't mind trying out something different, I prefer [Zenwalk]("http://zenwalk.org/"). 

> **merinda1 said:**
> Thanks to everyone on this forum who was helping me.  I think that perhaps my hard drive was going.  It got to a point that when I put in the ME installation CD, I was warned that the only way to proceed was to run fdisk, which I did-only choosing the most standard options (1,1).  After I ran fdisk (to enable it to see the whole drive and partition as one big partition), the hard drive only saw 1.7 GB to format (though I had 40 GB) when I put in the ME installaton disk this time instead of 2 GB (which it saw before).  The first time it wouldn't install and said that the contents of drive C: were unrecognized.  I tried it again, and it went through its installation but could not restart.
 
When it tried to restart, I briefly saw the Ubuntu startup screen.  Imagine, Ubuntu was still trying to live after fdisk

---

### Post by porchrat on 2009-05-19
Windows ME? WHY?!?

---

### Post by Mornedhel on 2009-05-19
Because the user has a valid license for it ?

---

### Post by mapes12 on 2009-05-19
> Thanks for replying, Ash. My computer boots CD before the hard drive or I wouldn't have been able to load Ubuntu from the CD in the first place or reload ME, right? I have a 40 GB hard drive, 384 MB RAM, and a 800 MHz processor. I know these specs are low, but I thought I would enjoy the challenge of making Ubuntu run on it.

I have Ubuntu running on an old Dell desktop machine with the same spec.It runs fine but struggles with streaming video. But if you have a reasonable video card then that should take the load off the machine. Mine shares main memory with the video device, hence the reason why it struggles with video.

If GParted doesn't work then go with DBAN as others have posted then start again. You may have better success with an ["alternate"]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") CD and run a text based installation. My old Dell wouldn't run an Ubu LiveCD but the alternate CD installation went without a hitch. I'm running 8.04 for the Long Term Support.

---

