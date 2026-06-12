---
title: "2nd distro for duel boot"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by nml on 2009-03-26
Hey All,

I'm currently using Ubuntu 8.10 on a 5yo IBM laptop (pent M 1.7 with 1.5 ram) with an 80gig HD.  I am thoroughly enjoying it, but have been playing with the live CDs of a couple other distros (knoppix and mandriva).

Since this is a 'spare' computer, I have the latitude to be able to 'play/experiment' some.....so, I want to duel boot with another linux distro (not windows as I've already done that and am through with it).....What is an easy OS to now set up with my current 8.10 install (the live CDs are just to slow).

Since I'm such a beginner, I will need to slowly work through the process of setting up new partitions, configuring whatever new version I/we decide on. I would love to keep the system so that I can remove the new addition and add another new one if I wanted to down the road....I would like to keep Ubuntu as the primary OS for quite a while...

Debian seems to be a possibility, but I'm certainly open to any other suggestion.....

TIA,

Mick

---

### Post by bruno9779 on 2009-03-26
I personally like a lot to try new distros with Qemu (in the repositories)

I dunno if it will work with your hardware, though

---

### Post by Simian Man on 2009-03-26
Is a duel boot where two OSs spar for control of the hard drive??

Seriously using a VM like VirtualBox is great for testing out distros.  Play around with a few and see what you like.  I think Debian is so similar to Ubuntu that dual-booting them wouldn't net you much.  Why not something really different like Zenwalk, Fedora or Arch.

---

### Post by .Maleficus. on 2009-03-26
I tend to recommend Arch and Gentoo a lot to new users, simply because using another "easy" distro is a waste of space on your hard drive.  Why not actually take the time to learn something new?  Slackware would be another good option (and one I've been meaning to try myself).

---

### Post by mhgsys on 2009-03-26
Talking about Slackware, 

Maybe this can be interesting for you 

[http://en.wikipedia.org/wiki/BackTrack](http://en.wikipedia.org/wiki/BackTrack)

---

### Post by nml on 2009-03-26
I'll look into Qemu tonight..

> using a VM like VirtualBox is great for testing out distros

I'll definitely look into that....I have XP on my mac using parallels, so I don't know why I didn't think of this to begin with....other than my total inexperience....

I assume using another distro through VirtualBox will be faster than the liveCD options.....

Are there good instructions around for installing and removing various distros using a VM...if so, where's the best place to start...

Mick
(trying to get a handle around a really large field of computer use....)

---

### Post by Simian Man on 2009-03-26
> **nml said:**
> 
I assume using another distro through VirtualBox will be faster than the liveCD options.....


Well that depends very much on the specs of your machine.  If you have enough memory running a VM with VirtualBOx is quite responsive.  However VMs can't currently expose the 3D capabilites of your video card, so 3D performance sucks (no compiz :().

The nice thing about a VM is that you can install software on it just as if it was a regular machine.  With Live CDs, you are limited to what comes on it.

Googling for tutorials gives a few promising hits.

---

### Post by markbuntu on 2009-03-26
I have 5 or linux 6 distros on my machine (some of them are broken/abandoned) but it is pretty easy to avoid problems if you install the distro to its own partition and put its bootloader in the same partition. Then you just need to add a few lines to the boot/grub/menu.lst on the mbr to chainload to that distros grub. This will avoid a lot of problems that can appear with kernel updates rewriting grub or your install changing the uuids etc.

For example these have been added by me to the end of the /boot/grub/menu.lst on hd0 which is my boot drive. They all have their own grub

#This entry added to get for 8.04 UnbutuStudio amd64 on sdb

title		Chainload Ubuntu 8.04 amd64
root		(hd1)
chainloader	+1

#This entry added for Mandriva i386 on sdc

title		Chainload Mandriva 2009
root		(hd2)
chainloader	+1


#This entry added for Intrepid on sdd

title		Chainload Intrepid
root		(hd3,0)
chainloader	+1

#This entry added for Jaunty on sdd3
title		Ubuntu Jaunty 9.04 kernel 2.28-6-generic
root		(hd3,2)
chainloader      +1

---

### Post by shane2peru on 2009-03-26
I must admit I enjoy dual booting.  ATM I don't have time to play around with other distros, but I have dual and even triple booted at one time just to see how it would go.  If you are truly interested in rolling up your sleeves and getting into Linux, I highly recommend Gentoo, or Slackware.  I have installed both it is a great learning experience.  I must say that Gentoo probably has the greatest documentation that is out there.  Slackware has good documentation as well, however it is in every config file that will be installed on your computer.  They are both fun, and very informative.  If you want simple distro's to play around with check out these two sites:  [www.distrowatch.com](www.distrowatch.com)  and [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)  <--- that one is a test to see which distro is right for you.  I have taken that test a gazillion times, it is fun.  Enjoy, and pass the knowledge you learn on to others!

Shane

---

