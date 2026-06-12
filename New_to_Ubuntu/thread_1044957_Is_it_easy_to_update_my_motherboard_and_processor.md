---
title: "Is it easy to update my motherboard and processor?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by iason on 2009-01-19
Hi all,

I am wanting to build a media server and right now have an old dell laying around that I would just like to get a 1tb drive and install ubuntu to run boxee.  In the near future I am looking at getting a new mainboard and processor specifically for the media server then using the same drive.  Will it be as simple as transferring the old drive over and ubuntu will pickup the new hardware changes?  or will I have to reformat and install?

---

### Post by jrusso2 on 2009-01-19
How old a Dell are we talking about?  Got the specs for it?

---

### Post by stderr on 2009-01-19
It should be OK. Linux (& Ubuntu) cope rather well with motherboard and processor changes. I switched from an Asus skt939 based on nForce (+ AMD X2) to a Gigabyte LGA755 based on Intel (+Intel Duo) with no side effects :) But you never know... changing a motherboard and CPU is always "interesting" from an OS standpoint.

---

### Post by Skripka on 2009-01-19
> **iason said:**
> Hi all,

I am wanting to build a media server and right now have an old dell laying around that I would just like to get a 1tb drive and install ubuntu to run boxee.  In the near future I am looking at getting a new mainboard and processor specifically for the media server then using the same drive.  Will it be as simple as transferring the old drive over and ubuntu will pickup the new hardware changes?  or will I have to reformat and install?

You're asking for trouble, swapping mainboards--i'd be very surprised if you got Ubuntu to even get past the loading bar-let alone run poorly.  swapping CPUs onto the samy mainboard aren't a problem really-presuming we're talking same # of cores.

---

### Post by iason on 2009-01-20
Not sure what the dell specs are off hand, i think its a 1.8 celron.  I guess the best thing would be to partion a small portion for the os, then del it and reinstall, leaving the rest for storage.  what would be a good size if so?

---

### Post by jrusso2 on 2009-01-20
The reason I am asking for the model is that to swap CPU's you need to use the same socket and have bios that will accept that CPU or upgrade to it.

Now Dell often doesn't do this.

Also the older Dells like the one I have are not really ATX so you can't easily swap motherboards.  The power supply plug is proprietary.

---

### Post by linux_tech on 2009-01-20
One of the benefits to ubuntu is portability. You can often take the hard drive out and use it in a different pc, and it will run.

---

### Post by Skripka on 2009-01-20
> **linux_tech said:**
> One of the benefits to ubuntu is portability.  You can often take the hard drive out and use it in a different pc, and it will run.

It may run...but odds are good you'll have to reinstall lots of libraries to get everything working again (such as onboard audio, graphics drivers, etc)-and if one has partitioned their HDD in root, home, swap-reinstalling *buntu is easy and fairly painless and may be less trouble.  There's no way of knowing until you try to see how bad/unstable the results are.

---

### Post by txcrackers on 2009-01-20
> **Skripka said:**
> It may run...but odds are good you'll have to reinstall lots of libraries to get everything working again (such as onboard audio, graphics drivers, etc)

Sorry, but I believe this advice to be inaccurate: Linux installations typically come with **all** of the drivers that have reasonable levels of support. If the hardware is at least close to "standard" chipsets, it'll work right out of the box. Stick with the "generic" kernel and it'll run just about anything.

I've had one hard drive that lived through four different motherboards (and CPUs) with no real issues. And this was a couple of years ago - hardware support has only gotten better since then.

---

### Post by stevoo on 2009-01-20
i am pretty certain that when swapping CPU there will be no problem. 

Now when you change motherboard you may end up with some problems there. I am 90% sure than on window if you changed mOBO you had to reinstall or reformat the hard disk. 
Now with Linux since HAL is being used to maintain hardware, i can not say for sure if that will be the case. 

If i were you i would first back up everything before doing anything else ....

---

### Post by iason on 2009-01-21
deled comment.  page cached, didnt read above.

---

