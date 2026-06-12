---
title: "ibernation doesn't work"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by emmwee on 2009-03-18
For "ideeological" reasons, I'm very happy that I substituted Windows with Linux, and I'm satisfied with my Ubuntu that can do all what Windows can do, and I even find it more userfriendly than Vista.
There are only 4 things I would like to resolve. I will post my 4 problems in 4 separated threads.

4th problem:
Ibernation doesn't work. Why?

P.S. I have Ubuntu 8.10 Intrepid con Gnome. If I choose "ibernation" the system shuts down until I see the black panel with a blinking underscore, then an error message ("btyt-intr-co....... failed ....") and after that automatically I will have to enter my password and I'm back on my ubuntu desktop.

---

### Post by kaixi on 2009-03-18
What kind of errors do you get and which version of Ubuntu are you running?

---

### Post by DaveG825 on 2009-03-18
There is a very simple solution to your problem.

In order for Ubuntu to hibernate properly, you need to have a linux-swap partition. Even if you have a swap file, that won't cut it. If you didn't create swap during install (which it looks like you didn't), you're gonna wanna create it now. Open up the Partition Editor from System > Administration, then look at your hard drive. Hopefully, you'll have some unalocated space. If not, you're going to want to resize one of your partitions (probably the one with Ubuntu installed on it) to make enough space. Your linux-swap partition should be about 2 times the amount of physical RAM your system has.

So for example, if you have two gigs of RAM, make space on your hard drive for a 4 gig linux-swap partition. Then obviously, create the partition and hit apply (make sure to select "linux-swap" and a size of 4000 for 2000mb of RAM).

I'm assuming you can partition a hard drive, if you're clueless there's guides for it, or we can try and help you.

Good luck. :D

---

### Post by DaveG825 on 2009-03-18
Whoops, sorry I thought you said hibernation. XD

I apologize. Unless that is what you meant, then good luck. =p

---

### Post by emmwee on 2009-03-18
Thanks!
I'm a new to Ubuntu, and I fear ;-) that I have to begin to understand what partitions are and how I have to manipulate them. I installed ubuntu under vista with wubi -  without any idea about partitions. As you write it seems that I can change the values even now, after the installation, and create more place for linux.
It would be great if you can tell me a good manual online that illustrates to a beginner like me what partitions are and how I can change them. So, when I have a lit bit of time I will study this matter.

P.S. Sorry, my English isn't the best one ;-)

---

### Post by DaveG825 on 2009-03-18
Haha that's alright, I thought that I had made a mistake.

I know you can get to the partition editor now, but the problem is that you can't edit a mounted (running) partition. This means that you can't edit the partition with Ubuntu from your Ubuntu installation on that partition. Because of this:

I do suggest installing from a Ubuntu LiveCD (it's more simple than you may think). As far as I know, Wubi can't do much with actual partitions. Just download the CD image from the website, and use a program in Windows like Image Burn to get it on a CD-R. Make sure you've backed up your files in Windows, then slip the LiveCD in and restart your machine, making sure to boot from the CD (this should happen automatically for most). From there, hit "Install Ubuntu." The installation is pretty straightforward, but since you're new to Linux I suggest Googling "Ubuntu install help" or "Ubuntu install walkthrough" or something of that like.

OK, here goes. A hard drive can be broken up into "separate drives," so to speak, using programs called partition editors. These "seperate drives" are called partitions. Ubuntu and its LiveCD both have a partition editor included, called Gparted (GNOME Partition Editor), and you can access it from System > Administration > Partition Editor. You'll want a walkthrough to work with Gparted, but you'll want 3 partitions. A NTFS one for Windows, an ext3 for Ubuntu, and a linux-swap that's the size of your RAM times 2. This'll all be explained in whichever guide you choose.

I hope that I was of some help. If you have any more questions, we can sure help you. Good luck. :)

---

### Post by emmwee on 2009-03-19
Oh, for sure, what you write is a big help. I think it would be impossible for newcomers to get to "live well" with linux without the help forum. There are too many - small and big - problems that you meet at the beginnung when you try to get your machine as you want installing new programs.
Concerning the (re-)installation with a cd rom: I tried at the beginning to do so, but it was impossible. So someone in the forum told me to try with Wubi (see my old thead: [http://ubuntuforums.org/showthread.php?t=1066253](http://ubuntuforums.org/showthread.php?t=1066253)). And ... that's what I fear ... reinstalling would also mean to reinstall all programs (including to find once again around the web the solution why your audio doesn't work here and a certain file format doesn't work there ...).
So, if I could change the partitions in my actual system I would do that, but otherwise ... hm ... I'm not so sure ...

---

