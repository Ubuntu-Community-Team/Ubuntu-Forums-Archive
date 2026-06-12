---
title: "Laptop driving me nuts with installs......GGRRRRR"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-05-04
I have on old Compaq Presario M2000 Laptop, 256Gb Ram, 40Gb Hdd 1.7Ghz Pent M with Intel VGA adapter..

It has been the most frustration machine I have ever tried to install Ubuntu on

I originally loaded 10.04 Beta on it and it fired up fine, then I installed fwcutter for the Broadcom wireless card...and all was fine..

Then I did the 10.04 release package update...BIG Mistake..got to the first splash screen and it hung...

I played with it and found that if I used my SuperGrub disk ( the ver with the orange background with green text highlight ) I could get to the initrd file and boot it...but only in safe graphics mode..

In safe graphics mode it performed well...with hi-quality graphics and even the wirless worked...so to me that indicates that it is not a graphics driver issue...

what I dont understand or have worked out is why it wont boot from the Hdd without hanging, but if I use my supergrub disk I can manually boot it

When booted thru SuperGrub, the system performs like it should...

Can I still download the Beta 10.04 from somewher just to prove that I am not crazy





NOTE: I have had experience with loading Ubunut on various machines, including dual boot  :)

---

### Post by byStanderone on 2010-05-04
...nothing to prove really,...read from the forums that the devs are working on somekind of bug on the officially released lucid....tho am not sure of its current status as of yet. anyway the peeps are doing their thing, and i salute them.

---

### Post by Ducatiboy Stu on 2010-05-04
Not only have I had issues with lucid, but Karmic 9.10 wont play nice either....kernels above .14 wont load and run.... 

I still dont know why Lucid runs via supergrub

---

### Post by lkraemer on 2010-05-04
Would it be possible for you to increase the RAM to 512 or 1 Gig?

What about trying the Alternate Install CD?

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 


Here is a link to the previous versions.
[http://distrowatch.com/index.php?distribution=ubuntu&month=all&year=all](http://distrowatch.com/index.php?distribution=ubuntu&month=all&year=all)


lk

---

### Post by Kafubie on 2010-05-04
I would try and chuck it out the window.
8)!!!

---

### Post by Ducatiboy Stu on 2010-05-05
I re-installed 10.04 beta....

And it works like a charm....which makes me suspect the boot process..

It works just the same as when I had to boot 10.04 RC via supergrub..

I just have to remember NOT to do any upgrades :popcorn:

---

### Post by lkraemer on 2010-05-05
There has been a BUG identified with the Splash screen (Plymouth if I 
remember correctly) and that might be your problem.  Hopefully, it will
be fixed soon.  I was one of the Lucky ones that everything seemed to work
right out of the box on my Gateway.

[http://ubuntuforums.org/showthread.php?t=1469475&highlight=Plymouth+Splash](http://ubuntuforums.org/showthread.php?t=1469475&highlight=Plymouth+Splash)

Glad you got it all installed.

lk

---

