---
title: "How do I uninstall ubuntu 8.04 and install xubuntu 9.04?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by mikodo on 2009-06-29
Hello everyone,

I have an old computer with Hardy LTS installed that is not online, but works, just slow, that I would like to install xubuntu 9.04 on, to give to my brother-in law, who has never had a computer. Here are the specs.

Dell Dimension XPS T450
Pentium 111  433mhz
Memory 250.1 mb
Hard drive memory ? 12-20 gigabytes
NVIDIA Accelerated Graphics Driver (Legacy Cards)

I've downloaded xubuntu 9.04-desktop-i386.iso and burned it to disk. Do I just do a regular install over top of the Hardy LTS? I tried this before, a few months ago (with earlier version of Xubuntu 8.04, I think), and for whatever reason the xubuntu CD would not install over Hardy on the computer.

Any ideas as to what I might have missed? 

Any Ubuntu links you suggest that I should read up on, before attempting again?

Thanks in advance,

mikodo

---

### Post by albinootje on 2009-06-29
> **mikodo said:**
> 
Pentium 111  433mhz
Memory 250.1 mb
Which such an old machine you might want to try CrunchBang Linux (Ubuntu based but with openbox as windowmanager), or an lxde desktop based linux.

But of course you can try Xubuntu first. 
If you don't need to make backups of the Ubuntu Hardy installation, then make sure you choose to format the partitions during the partitioning stage.

---

### Post by yang925 on 2009-06-29
why uninstall why not :

sudo apt-get dist-upgrade
and sudo apt-get install xubuntu-desktop
then use the XDM and log in with xfce sessions?

but i agree with  the guy above me . not enought memory or speed for even xubuntu i bet. go with like Puppy Linux. Its decent and speedy.
EDIT: yeah it will install fine over anything. I will just reparition and reformat. Reinstallation actually sounds like the way to go for a e give a way. The *buntus are very easy to use but kinda resource heavey for that machine. Puppy Linux is hard to get new software for after the base install and I have no experiance with Crunchbang.

---

### Post by powel212 on 2009-06-29
run update manager under administration settings

after updates are current you will see a button to upgrade to Jaunty.

if that doesn't work you can boot from the live cd open partition editor, delete the existing ubuntu install and install Jaunty.

I would definitely try the first option before deleting the old partition.

Powel

---

### Post by mikodo on 2009-06-29
Well, the new iso of Xubuntu 9.04, that I burned to disk, wouldn't install over Ubuntu 8.04, just like my previous efforts. I wonder if it is because the disks are DVD? that I am using rather than CD. Don't know if that makes a difference or not! The Dell Pentium 111 has just CD player.

The Puppy Linux looks like a good alternative for this old computer, if I can get the Ubuntu 8.04 to uninstall first.

Thanks for your responses!

Good nite,

mikodo

---

### Post by caravel on 2009-06-29
Debian stable is by far the best distro for that spec of machine.

---

### Post by brayden13 on 2009-06-29
Puppy Linux would do great on that machine, ubuntu and it's variations only work great on mid range PCs. If you burned a DVD and your machine doesnt' have a DVD drive then that is the problem. Burn to a regular CD and try. But I'd highly suggest Puppy. The disk is only about 100mb in size.

---

### Post by mikodo on 2009-06-29
> **caravel said:**
> Debian stable is by far the best distro for that spec of machine.


What does this mean?...Debian 5.0 would run well on this machine?

Thanks,

mikodo

---

### Post by mikodo on 2009-06-29
> **brayden13 said:**
> Puppy Linux would do great on that machine, ubuntu and it's variations only work great on mid range PCs. If you burned a DVD and your machine doesnt' have a DVD drive then that is the problem. Burn to a regular CD and try. But I'd highly suggest Puppy. The disk is only about 100mb in size.

Thanks for the reply. I'll try with CD's in the future

mikodo

---

### Post by halitech on 2009-06-29
> **mikodo said:**
> What does this mean?...Debian 5.0 would run well on this machine?

Thanks,

mikodo

Debian testing would even run nicely on those specs as long as you go with XFCE or LXDE. Instructions are here:

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

I have used those instructions for machines with half the specs of yours and they run decently.

---

### Post by tarps87 on 2009-06-29
If you only have a cd drive you need to use a cd. You do not uninstall an OS you simply reformat the drive, this is usally done for you when installing the new OS.
I would try installing Xubuntu first, it will not be lightning quick but I have ran 8.10 on the same specs (except it was a celery stick on a p3)
IMO Xubuntu will be easier for your brother-in-law to use that Puppy Linux and you can always change the distro later

---

### Post by caravel on 2009-06-29
> **halitech said:**
> Debian testing would even run nicely on those specs as long as you go with XFCE or LXDE. Instructions are here:

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

I have used those instructions for machines with half the specs of yours and they run decently.

Yes, Squeeze is getting more stable but still has some minor issues, which is why I would still recommend stable over it for the beginner.  XFCE, IceWM, LXDE or Fluxbox will be lightweight enough with the first three probably being the most useable.

Avoid Xubuntu, yes it uses XFCE but with all of the usual Ubuntu bloat running.  I tried Xubuntu 8.04 on a 333MHz PII laptop with 256MB of memory and it was so slow as to be virtually unusable.  It won't get much better on that machine.  Go with Debian 5.01 Lenny or have a go at testing (Squeeze) if you're feeling a little braver (In all honesty testing should be fine).

---

### Post by halitech on 2009-06-29
> **caravel said:**
> Yes, Squeeze is getting more stable but still has some minor issues, which is why I would still recommend stable over it for the beginner.  XFCE, IceWM, LXDE or Fluxbox will be lightweight enough with the first three probably being the most useable.

Avoid Xubuntu, yes it uses XFCE but with all of the usual Ubuntu bloat running.  I tried Xubuntu 8.04 on a 333MHz PII laptop with 256MB of memory and it was so slow as to be virtually unusable.  It won't get much better on that machine.  Go with Debian 5.01 Lenny or have a go at testing (Squeeze) if you're feeling a little braver (In all honesty testing should be fine).

Debian Lenny (Stable) would be a good choice with LXDE. I just set up a system with LXDE on a P300 with 96meg of ram and gave it away and it booted in 2 minutes to the desktop and logged in in 15 seconds. Not a speed demon but usable.

Xubuntu used to be great for low end but they've tried to make it as easy as ubuntu so lots running in the background making it almost as heavy as Gnome. If a custom build isn't something you want to do, there is an XFCE+LXDE cd

[http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-xfce+lxde-CD-1.iso)

---

### Post by angelsguitar on 2009-06-29
I agree with the previous post.  Go with Lenny LXDE.  Very lightweight but complete.  And very stable. Then it's just a matter of choosing wisely the packages you'll install later for the daily tasks.

You can install it by using the Debian netinstall cd or by using the Debian LXDE+XFCE cd (this cd won't install both, but let you choose which of the two to install)

---

### Post by chunnel on 2009-07-01
I installed Xubuntu while running Vista.  Now I have a bootup for Xubuntu.  I was just trying it out.  How do I uninstall it?  I thought I could uninstall it while running Vista since I thought the way it described it, that it would be running with Vista in the background.  That is not the case.  So now I have a triple boot, Windows 7, Vista and Xubuntu.  So how do I uninstall this operating system?

---

### Post by halitech on 2009-07-01
If you used WUBI to install it, check Add/Remove programs and you should have an uninstaller listed for it.

---

