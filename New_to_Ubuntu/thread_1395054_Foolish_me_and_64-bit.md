---
title: "Foolish me and 64-bit"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by Megatron3000 on 2010-01-31
Well, so after having problems galore, i discovered today that i have a 64-bit processor, and that i have been running it with a 32-bit distribution. This might explain one or two things, no? So, i want to install everything anew, and i wonder which version you recommend. I don't need funky graphics, but i do need good audio production capacities. It seems that the Ubuntu Studio site advises me to get version 8.04, but since i don't want to install all of Ubuntu Studio (just a part of it), i want to start from a standard Ubuntu and then put some of the Studio inside. Now, the question is: 8.04 (and where would i get a livecd image for that), 8.10 (apparently no realtime kernel -i like my realtime kernel, could i make it run with 8.04?) or 9.04 (or maybe even 9.10, though i prefer relying on the more time tested distro's out there). Swift tips would be highly appreciated!

---

### Post by Megatron3000 on 2010-01-31
Woops, 8.04 seems to be readily available at the ubuntu site. and recommended by ubuntu studio.
ok

---

### Post by audiomick on 2010-01-31
Hallo.

Firstly, you shouldn't have any problems that can be attributed to running a 32 bit system on a 64 bit core. From every thing I have read, that works fine.

As far as your real time kernel goes, I have the impression that the easiest way there is in fact to install Ubuntu Studio. You don't have to install all of it, there is a selector during the install to choose which "branch" you want to include. Just leave out the one you don't want.

I think you are right about there not being a RT kernel for 8.10. I know that I started with an 8.04 install, and lost the RT kernel on the update to 8.10. I read something about it, that it wasn't there because of some development issue. To be quite honest, I haven't looked into it since.


As far as the version goes, I think that 9.10, after a number of birthing issues, has gotten pretty stable. However, if your system is running ok at the moment, I would suggest waiting for 10.04. That will be an LTS, i.e. you can go on with it for the next couple of years.

---

### Post by Thelasko on 2010-01-31
Follow the link in my signature.

---

### Post by J V on 2010-01-31
8.04 is old, karmic is doing fine now...

64-bit shoulden't make any difference on most apps, the problem is probably if you are using something prior to 8.04 xD

---

### Post by dolphinaura on 2010-01-31
use the 9.10 version of ubuntu (karmic)
and install the RT kernel (yes, 9.10 has the rt kernel)
as long as you apply all of the updates as soon as you install it, there should be no problems at all.

---

### Post by djchandler on 2010-01-31
> **dolphinaura said:**
> use the 9.10 version of ubuntu (karmic)
and install the RT kernel (yes, 9.10 has the rt kernel)
as long as you apply all of the updates as soon as you install it, there should be no problems at all.

Dittos on the RT kernel, also called low latency. Synchronizing with your midi connected devices is not a problem using the RT kernel. It certainly can be a problem using the "normal" kernel regardless of the speed of your processor. The issue is timing of interrupts vis-a-vis the midi or USB ports, and the RT kernel does that *a lot* more frequently.

Whether you use 8.04 LTS or 9.10 now will make little difference. A new Long Term Support release is due within the next 3 or so months, presumably 10.04 also called Lucid Lynx. You will be able to perform the upgrade to Lucid from either of those.

The critical aspect is the RT kernel, not necessarily whether it's 64-bit or not. If you have more than 2 gigabytes of RAM, by all means use the 64-bit. If you have 1 gigabyte or less of ram, you can use the 32-bit. It will use less overhead in terms of RAM usage while running.

This is a permalink to an article on my seldom used (due to age and infrequent posts) blog. Perhaps this will give you a little insight as to what your difficulties have been and why.

[http://djchandler.wordpress.com/2008/04/06/low-latency&#8212;whats-it-good-for/]("http://djchandler.wordpress.com/2008/04/06/low-latency%E2%80%94whats-it-good-for/")

---

### Post by steveneddy on 2010-01-31
> **J V said:**
> 8.04 is old, karmic is doing fine now...

64-bit shoulden't make any difference on most apps, the problem is probably if you are using something prior to 8.04 xD

8.04 isn't old, it is the LTS.

8.04 isn't the bleeding edge release, karmic is.

If you want stability, use the LTS, 8.04.

I am on 8.10 only due to a feature necessary for working daily on my laptop. Otherwise I would use the LTS myself.

I will wait for the next LTS and install that, 10.04.

If Ubuntu Studio recommends Hardy, then run Hardy.

Sometimes stability and reliability are features greater than the latest/greatest release.

---

