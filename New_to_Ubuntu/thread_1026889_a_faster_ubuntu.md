---
title: "a faster ubuntu"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-12-31
i came across the phoronix benchmarks, which revealed that ubuntu was slower than mac OS-X,and also that ubuntu was getting slower and slower as it advanced from one release to another.i also saw about Mark Shuttleworth talking of making it boot blindingly quick in ubuntu9.04.but,will we ever have a release focussed on dramatically increasing performance,doing stuff like brushing aside mac OS-X in terms of performance with all that eyecandy running,when can i expect to see Phoronix benchmarks proving ubuntu to be having an upper hand over mac? yeah,ubuntu is a fast,stable high performance OS,but can't it beat mac?i mean mac OS-X is a proprietary OS and nothing of that gentoo stuff has to be done to make it fast,it is simply faster.i don't want to slim down ubuntu like gentoo by kernel compiling,etc.,but still want it to be faster than mac OS-X.

---

### Post by donkyhotay on 2008-12-31
The more features you add the slower a system runs, it's just a fact of computers that can't be changed. Ubuntu will most likely become slower and slower as computers become faster (just like any other OS). However the advantage of linux (including ubuntu) is that you can customize it to do what you want. If ubuntu itself is too slow for what you want try xubuntu. If you want something REALLY fast try something that focuses on being lean such as DSL or puppy. Also benchmarks aren't always very accurate as hardware as a large factor as well as what applications your running.

---

### Post by stonecoldjha on 2008-12-31
but users who have used both mac OS-x and ubuntu seem to be more satisfied with mac when it comes to performance.does mac slow down?

---

### Post by albinootje on 2008-12-31
> **stonecoldjha said:**
>  i don't want to slim down ubuntu like gentoo by kernel compiling,etc.,but still want it to be faster than mac OS-X.
Arch Linux is for sure faster than Ubuntu on the desktop, to just give an example.
Arch Linux is build for i686. I think Ubuntu is still i486 optimized (A while back Debian stopped with i386 support afair).

You can also make Ubuntu faster by disabling things that you don't need.
I don't use bluetooth, so why would I want some bluetooth software running in the background ? Simply disable it.

---

### Post by linux_tech on 2008-12-31
A fast boot is always nice.  It would be even nicer if web pages would always load instantly.

---

### Post by Paqman on 2008-12-31
I'd be pretty wary of benchmarks comparing different OSes. It's really comparing apples and oranges.

Having said that, it'll be good to see some reduced boot times in Jaunty. A lot of people are doing some amazing work on boot times at the moment. Between these optomisations and the rise of SSDs we should have computers that boot pretty damn quickly on the horizon.

---

### Post by champkuo on 2009-04-08
[B][SIZE="3"][COLOR="Blue"]It's huge faster than 8.10,but some times it will dead down and
the home-rw's space that's made from the 9.04 Usb creator is only about 227 MB left,
that's not enough for me.

Please help "How to enlarge"! Thanks a lot for any suggestion![/COLOR][/SIZE][/B]

---

### Post by bumanie on 2009-04-08
My experience must differ from some others. I have found ubuntu to be quicker with each new distro both at boot and in general use. 9.04 boots quite quickly when ext4 filesystem is used (have not tried it with ext3 to compare, however). If you want something quick, use puppy or dsl, they are both very light distro's.

---

### Post by sdennie on 2009-04-08
I don't know why this old thread was dug up but, I can't stop myself from replying:

1) OSX actually IS similar to gentoo as far as "optimized for my hardware".  In fact, it's what gentoo wants to be.  OSX can only be installed on Apple machines (in theory) which gives Apple a very narrow spectrum of machines with predictable configurations to optimize for.  Linux will obviously never have that luxury.

2) It's not true that adding more features to something makes it slow.  In practice, it does happen but mostly because people think exactly that and find it acceptable.  A good example of something that is constantly adding features yet getting faster is the linux kernel.  The reason is that they consider "Performance" a feature.  Most developers are simply too lazy to do the same.

3) Benchmarks are meaningless unless they represent a common scenario for you.  Even they are meaningless unless you can be certain they represent an *accurate* scenario.  Benchmarking is hard and while I like the phoronix benchmarks, there are only 2 reasons to run them 1) You've identified something as slow and want to take measurements along the way as you attempt to improve it.  2) Chest thumping.

Edit:
Ooops.  Thought of a third: "To compare two machines in way you actually plan to use them".

---

### Post by 3rdalbum on 2009-04-08
Want to give us a benchmark?

The only benchmarks I've seen are ones that either show Ubuntu with a speed benefit for almost everything, or that show OS X better for some things and Ubuntu better for others.

Mac OS X has issues relating to data loss, apparant memory leaks and runaway processes. The former is probably the result of a 'feature' to improve the speed of file writing operations, the latter two appear to be causing a dramatic loss of speed in everything under certain conditions. Those certain conditions manifest themselves every day at the place my father works, and once this happens his workplace's dual G5 can easily be beaten by his 2005-model Sempron running Linux Mint.

---

### Post by zerhacke on 2009-04-08
I never understood the need for a fast boot.  How much does it matter that your computer booted to a login screen three seconds faster than mine when I only boot or reboot my computer once every 3 months?

---

### Post by Insane_Homer on 2009-04-08
> **zerhacke said:**
> I never understood the need for a fast boot.  How much does it matter that your computer booted to a login screen three seconds faster than mine when I only boot or reboot my computer once every 3 months?

think of the environment man!!!

I shutdown every night and boot between winblows (for the wife & skype) and 9.04 32bit and 9.04 64 bit.

So boot time of 30secs v 45+ seconds is significant enough for me to appreciate.

---

### Post by jamesrfla on 2009-04-08
After I install Ubuntu I always disable and services or program I don't need when I boot my Ubuntu up. In system>administration>services I disable Blue tooth because it is a desktop and I don't have blue tooth in it. Also in System>preference>session you can disable evolution reminder if you don't use it. Compiz takes up a lot of resources so if you don't use it disable it or remove it. Also every once in awhile Ubuntu does like a file system check. I here that can speed up your system but not sure how to force one.

---

### Post by zerhacke on 2009-04-08
> **jamesrfla said:**
> I here that can speed up your system but not sure how to force one.

With a journaled file system doing a fsck every now and then for no reason does not give a speed increase in file seek times.

---

### Post by LowSky on 2009-04-08
Speed tests are such hinderence to actual performances in real world environments. A few seconds here and there really mean nothing to a person. The only thing I would like to see done faster is the ability to rip a 2 hour movie in 10 seconds, or fold@home 10,000,000 proteins strains in a minute.

When it comes to speed if a process takes 15 minutes or more vs another systems, then I think of it as a problem. When I boot my PC I usually hit the power button and walk away to get a drink or use the bathroom, and when I get back its up and running. If you want instant on satisfaction look into some of those new psuedo-Operating Systems that are limited to a web browser and DVD playback. Otherwise getting angry over 15 seconds is like beating a dead horse, just not worth the hassle.

---

### Post by presence1960 on 2009-04-08
> **LowSky said:**
> Speed tests are such hinderence to actual performances in real world environments. A few seconds here and there really mean nothing to a person. The only thing I would like to see done faster is the ability to rip a 2 hour movie in 10 seconds, or fold@home 10,000,000 proteins strains in a minute.

When it comes to speed if a process takes 15 minutes or more vs another systems, then I think of it as a problem. When I boot my PC I usually hit the power button and walk away to get a drink or use the bathroom, and when I get back its up and running. If you want instant on satisfaction look into some of those new psuedo-Operating Systems that are limited to a web browser and DVD playback. Otherwise getting angry over 15 seconds is like beating a dead horse, just not worth the hassle.

+1

the only thing that matters to me is speed once the desktop is reached. I don't care if it takes 30, 45 or 60 seconds to reach the desktop because I am doing nothing on my computer during that process.

---

