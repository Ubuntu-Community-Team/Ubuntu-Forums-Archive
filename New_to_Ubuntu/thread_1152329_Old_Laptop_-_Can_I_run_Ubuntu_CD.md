---
title: "Old Laptop - Can I run Ubuntu CD?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by maeflower on 2009-05-07
Update: Problem resolved! I installed Puppy Linux and it works great. Thanks!
 
I have a 10 year old Dell Latitude Cpi D300XT. I've tried a few times in the past to reinstall Windows 98, 2000 and even NT, but it never works. It seems to have had a harddrive failure. Then I got the idea to run Ubuntu from a CD and give my laptop a new life as a netbook for my brother. Some computers at school have Ubuntu installed so that it automatically logs on and opens a web browser, and when you close the browser it restarts... it's really cool, really secure, and perfect for my situation. But, I know nothing about installing it, or running it from disk. A flash drive probably won't work either since the thing predates USB plug-and-play (then again, maybe that was a Winodws issue). I've tried a few versions of Ubuntu already from CD and none of them want to start up completely. There's always some kind of error that comes up(different for every one). 
Does anyone have any suggestions on which version to run or anything? I just read through an old thread that suggested the problem might be in my CD drive, and that could be why I wasn't able to install Windows... but there is definitely something going on with my hard drive as well.
BTW, I was able to get Knoppix to run live from the CD, but I had no input. Don't know if there's an easy fix there.

---

### Post by jacksinn on 2009-05-07
You can try running a live CD to see how your system does. You could also try Damn Small Linux, or Puppy Linux for very small, low memory Linux options.
Your old laptop is definitely not without options!

---

### Post by ymra on 2009-05-07
Possibly but I doubt it.  If the computer was working correctly your chances would be better.

---

### Post by maeflower on 2009-05-07
Jacksinn: I've been attempting to run the Live CDs, but I can't get any to start completely. I will try your suggestions for he small verisons though. 
ymra: Thanks, but if my computer was working correctly, I would have just installed Windows. I'm hoping I can get to a point where I can run some diagnostics to figure out what piece of hardware is the culprit.

---

### Post by snowpine on 2009-05-07
I have an old Dell Latitude Cpx, probably about the same vintage as yours, and when I installed Ubuntu on it, it was almost unusably slow. I installed a lightweight distro called SliTaz instead. 

The following information might help you determine if your Cpi is up to the challenge:

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

Also keep in mind that running from a Live CD is slower and requires more ram compared to a hard drive install.

---

### Post by mkvnmtr on 2009-05-07
I have never had any luck running a Ubuntu live disk with less than 512MB of memory. But Puppy linux and DSL run great on 128MB. Running from either live disk you will think you have a new computer.

---

### Post by MrWES on 2009-05-07
> **mkvnmtr said:**
> I have never had any luck running a Ubuntu live disk with less than 512MB of memory. But Puppy linux and DSL run great on 128MB. Running from either live disk you will think you have a new computer.

+1 on Puppy

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by lkraemer on 2009-05-07
I would suggest Damn Small Linux or TinyCore 1.4.1 as a LiveCD test.
TinyCore is only 10Meg on the CD and works good.  The only problem
is you are going to need a LAN connection to download some apps
so you can play a bit. And it isn't Ubuntu, so things are somewhat
different.

I am running it on an OLD Compaq Presario 1672 350mhz K6-2 with
a 80 Gig drive and 192 Meg of RAM.  Works pretty darn good.

TinyME Acorn would be another good one to test.

lkraemer

---

### Post by Wiebelhaus on 2009-05-07
Na , not well anyway , by the way the new [puppy linux]("http://www.puppylinux.org/") for old systems is the bomb.

---

### Post by TheNosh on 2009-05-07
use puppy linux, it's great. it was actually the first distro i really used, and for the machine i had i couldn't have asked for anything better

---

### Post by maeflower on 2009-05-07
Haha, a lot of votes for Puppy! I downloaded it after jacksinn's first suggestion and have been playing with it ever since. It's working awesomely... more than I could have asked for! Thanks for your help everyone. By the way, I managed to get installed onto the hard drive and remove the CD, with 3 successful boots. So, it must have been a Windows issue that has paralyzed my beloved first laptop all these years. I'm connected to the net and it will be a perfect public access computer for my brother and his friends (who have a tendency to get viruses on any PC they touch). 
I love that the current version - 4.2 - is called Deep Thought! Haha, nice Douglas Adams reference.

---

### Post by stalkier on 2009-05-07
> **maeflower said:**
> Jacksinn: I've been attempting to run the Live CDs, but I can't get any to start completely. I will try your suggestions for he small verisons though. 
ymra: Thanks, but if my computer was working correctly, I would have just installed Windows. I'm hoping I can get to a point where I can run some diagnostics to figure out what piece of hardware is the culprit.

It sounds like the RAM is the problem with the LiveCDs not booting all the way through.You have to remember that the OS is loaded into the RAM. The more you have the better.

---

### Post by nathang1392 on 2009-05-07
all this talk of puppy gets me interested. i want to try it but i dont have anything suitable to run it on. im going to wait till my desktop wont run ubuntu anymore and i will throw it on it.

---

### Post by maeflower on 2009-05-07
Yeah, that could have done it. It only has 125 MB. It wouldn't explain the original problems with the Windows install though, but that could have just been an issue with the hard drive from unplugging the power source while the computer was running (oops). I think the data wipe and Pppy install fixed that. 
I think I'll stick with Puppy. It works great, and it's fast!

---

### Post by egalvan on 2009-05-07
> **nathang1392 said:**
> all this talk of puppy gets me interested. i want to try it **but i dont have anything suitable to run it on**. 
im going to wait till my desktop wont run ubuntu anymore and i will throw it on it.

I run Puppy 4.2 on the following range of computers:
(mainly triple-boot set-up)

Low-End
Pentium -II 400MHz , 128MB ram, no hard drive, run from RAM

High-End
AMD Phenom Quad, 8GB ram, two TeraBytes storage


surely you can find something within that range ? :)

The low-end machine was given to me last year...
"too obsolete for Windows"

---

### Post by Wiebelhaus on 2009-05-07
The point of Puppy Linux is that it can literally run on anything after 386.

---

### Post by nathang1392 on 2009-05-08
> **egalvan said:**
> I run Puppy 4.2 on the following range of computers:
(mainly triple-boot set-up)

Low-End
Pentium -II 400MHz , 128MB ram, no hard drive, run from RAM

High-End
AMD Phenom Quad, 8GB ram, two TeraBytes storage


surely you can find something within that range ? :)

The low-end machine was given to me last year...
"too obsolete for Windows"

i mean wouldnt it be kind of pointless to put puppy on a quad core set up? wouldnt it be just as good with a something like a nice pentium and 2 gigs of ram? what im trying to ask is would this be overkill, and could puppy make use of that much resource?

---

### Post by egalvan on 2009-05-08
> **nathang1392 said:**
> i mean **wouldnt it be kind of pointless to put puppy on a quad core set up**? 
wouldnt it be just as good with a something like a nice pentium and 2 gigs of ram?
 what im trying to ask is** would this be overkill**,
 and could puppy make use of that much resource?

Pointless???

Of course it is! :)

That's the point! :)

Overkill???

Again, yes it is.

Will Puppy make use of the resources?

You *could* get Puppy to use that much RAM,
 but that is not the real aim of distros such as Puppy.
If you are doing video transcoding or image manipulation that *requires* that much RAM, you may be better served by another distro.

It's all about choices,
and the *nix world gives us those choices.

In the end, use the distro that does what you want,
does what you need,
that you enjoy working with,
and that runs well on whatever machine you are working on.

And don't be afraid of picking three or more as your favorites!


And seriously, any computer made in the last five years is overkill for what 90% of the population use them for....
web browsing, email, music, the occasional video...

I am NOT suggesting that you dedicate a modern computer to running Puppy exclusively...
although it would run *very* well... :P
but dual- or triple-booting is a lot of fun...

The machine I am typing on now is a P-4, 2,8GHz, 2GB ram, 80GB disk.
It has Win-XP, Ubuntu (Gnome,KDE & xfce), Puppy and TinyCore.

(  TinyCore... 10 MEGAbytes of Linux goodness.
try it out at [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)  )

GRUB handles the boot chores quite well.

As  I said, it's fun to be able to play and experiment with all this fine software.

But the other side is that there is a large number of folks all around the world for whom a computer is a major investment.
So getting Puppy to run well on older, "obsolete" hardware is a worthy goal...
worthy of being "Ubuntu"

---

### Post by nathang1392 on 2009-05-08
> **egalvan said:**
> Pointless???

Of course it is! :)

That's the point! :)

Overkill???

Again, yes it is.

Will Puppy make use of the resources?

You *could* get Puppy to use that much RAM,
 but that is not the real aim of distros such as Puppy.
If you are doing video transcoding or image manipulation that *requires* that much RAM, you may be better served by another distro.

It's all about choices,
and the *nix world gives us those choices.

In the end, use the distro that does what you want,
does what you need,
that you enjoy working with,
and that runs well on whatever machine you are working on.

And don't be afraid of picking three or more as your favorites!


And seriously, any computer made in the last five years is overkill for what 90% of the population use them for....
web browsing, email, music, the occasional video...

I am NOT suggesting that you dedicate a modern computer to running Puppy exclusively...
although it would run *very* well... :P
but dual- or triple-booting is a lot of fun...

The machine I am typing on now is a P-4, 2,8GHz, 2GB ram, 80GB disk.
It has Win-XP, Ubuntu (Gnome,KDE & xfce), Puppy and TinyCore.

(  TinyCore... 10 MEGAbytes of Linux goodness.
try it out at [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)  )

GRUB handles the boot chores quite well.

As  I said, it's fun to be able to play and experiment with all this fine software.

But the other side is that there is a large number of folks all around the world for whom a computer is a major investment.
So getting Puppy to run well on older, "obsolete" hardware is a worthy goal...
worthy of being "Ubuntu"

ha. nice. so as far as computers go, one mans trash can be another mans puppy treasure.

:)

---

### Post by egalvan on 2009-05-09
> **nathang1392 said:**
> ha. nice. so as far as computers go, **one mans trash can be another mans puppy treasure.**

:)

Absolutely!

Exactly!

You need fairly heavy iron to run a heavy, modern distro...

But Puppy will take anything  you throw at it.

So enjoy Puppy!

---

