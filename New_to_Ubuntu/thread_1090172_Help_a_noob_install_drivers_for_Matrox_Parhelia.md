---
title: "Help a noob install drivers for Matrox Parhelia"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Sonidos on 2009-03-08
I have been a user of Kubuntu for the last few months (Intrepid) and switched to Ubuntu because I was getting very inconsistent performance with audio from my asus motherboard.

Seems I swapped one problem for another.  I have a matrox parhelia on this workstation and I'm having major problems getting ubuntu and the matrox card to understand each other.

Initially, I have problems getting ubuntu to boot and it goes into low-rez mode because I don't get the gnome login.  I went to the Matrox site and downloaded the Parhelia driver for linux.  Cool.

But it hangs up during compiling and I get an error code.  Fine.  After tooling around the internet, I find that there are problems getting the matrox driver to load and an alternate driver is offered to get around the fact that the official matrox driver won't compile.  Must be a Debian/Ubuntu thing because Matrox makes no mention of supporting Debian/Ubuntu.

Ok, so I downloaded the revised driver [http://tuxx-home.at/archives/2008/10/13/T14_01_55/...and....same](http://tuxx-home.at/archives/2008/10/13/T14_01_55/...and....same) failure to compile.

I'm under the weather tonight with a stomach ache, but I want to get this fixed.  Hopefully, someone out there has a Parhelia card and got around this problem.  Searching "Matrox" and "Parhelia" doesn't offer too much info.  I'll be happy to take instruction and provide output or my approach to installation to see if I'm missing a step.

I checked my xorg.conf and it's pretty barren, so it didn't seem to figure out the video card and the monitor at all.

---

### Post by hansdown on 2009-03-08
Hi Sonidos.

I found some info. Hope it helps.

[http://www.google.ca/search?q=matrox+parhelia++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=matrox+parhelia++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Sonidos on 2009-03-08
Thanks for looking hansdown.  But I went there...just ran the command to check my video card -

MGA G550 AGP (rev 01)

But I get stuck at step 4 of the BinaryDriverHowto for Matrox Parhelia.  When I run sudo sh filenameyoudownloaded (yep, I used the right file name), the Matrox installer begins to run....then stops with an error.  aaargh..

---

### Post by hansdown on 2009-03-08
What is the error?

Some more good info.

[http://www.google.ca/search?q=MGA+G550+AGP+(rev+01)+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=MGA+G550+AGP+(rev+01)+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Sonidos on 2009-03-08
I'll give this a shot tomorrow and post errors.  I was on the tuxx site and there is more good info.  First thing, I have to determine if the mg or mx driver is the correct version for my card.  And apparently, I need to install some other pieces before running the driver.  I'm likely skipping a few important steps.

---

### Post by Kane_of_NOD on 2009-03-27
I'm having the same problem, by the way...


[http://ubuntuforums.org/showthread.php?t=1107992]("http://ubuntuforums.org/showthread.php?t=1107992")

---

