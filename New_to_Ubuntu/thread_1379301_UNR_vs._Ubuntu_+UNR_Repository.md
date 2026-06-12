---
title: "UNR vs. Ubuntu +UNR Repository"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by ydnom89 on 2010-01-12
Is there any difference between downloading the Ubuntu Netbook Remix ISO directly and first installing regular Ubuntu and adding the UNR repository? I'm running an Eee PC 900, which runs on a Celeron, while UNR is tailored for the Atom processors; I'm curious if there's a difference. If not, which OS would work better for me?

---

### Post by some-what-Gnu-2-networks on 2010-01-15
the difference would be the packages left over from the ubuntu install, unless you deleted them

---

### Post by warfacegod on 2010-01-15
I'm dual booting 9.10 and 9.10 Netbook Remix. Remix may be "tailored" to the Atom but its doing very well on my Pentium 4 2.8 Ghz Hyper Thread. Then again so does normal 9.10. For your Celeron, I recommend Remix, its "lighter" on the hardware.

---

### Post by snowpine on 2010-01-16
Ubuntu and Ubuntu Netbook Remix are identical, except for the "launcher" interface optimized for viewing on small screens. Ubuntu Netbook Remix is **not** "tailored" for the Atom processor (lots of netbooks have other types of processor such as Celeron) and its hardware requirements are the same, as you can see here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You should make the decision based on which user interface you prefer (netbook launcher or "classic" Gnome desktop).

---

### Post by ydnom89 on 2010-01-16
Ok good to know. I suppose my real question would be does regular Ubuntu have better support with drivers? Specifically, my mouse click bar doesn't work half the time (it feels like I have to vice-grip it before I may get a response) and my webcam and mic (both onboard) are suspect.

---

### Post by warfacegod on 2010-01-16
> **ydnom89 said:**
> Ok good to know. I suppose my real question would be does regular Ubuntu have better support with drivers? Specifically, my mouse click bar doesn't work half the time (it feels like I have to vice-grip it before I may get a response) and my webcam and mic (both onboard) are suspect.

In that respect, they are essentially identical.

---

### Post by warfacegod on 2010-01-16
Here are some screen shots of my Desktops for each OS on the same machine:

---

### Post by warfacegod on 2010-01-16
Forgot to attach them. The dark ones are 9.10 and the lighter ones are 9.10 Remix.

---

### Post by ydnom89 on 2010-01-17
Ok that's pretty much what I expected... Has anyone figured out a solution to my particular problem?

---

### Post by warfacegod on 2010-01-17
> **ydnom89 said:**
> Ok that's pretty much what I expected... Has anyone figured out a solution to my particular problem?

What exactly is the problem?

---

### Post by ydnom89 on 2010-01-17
Well, the mouse click bar doesn't always work when I left-handed click. I hate using my touchpad, so this really annoys me. Basically I'm having sensitivity issues when I click. I don't know if this is a hardware issue or a driver issue. Even more interesting, whenever I do a clean reinstall it works a little less than decent and then it just seems to degrade in functionality.
As for the webcam and mic, I'm not sure, it didn't work before, but I haven't tested since I reinstalled.

---

### Post by warfacegod on 2010-01-17
Have you tried a different mouse?

---

### Post by ydnom89 on 2010-01-17
I have not... This is the onboard mouse only.

---

### Post by warfacegod on 2010-01-17
So if the touch pad is dodgy change the sensitivity and speed. UNR = System> Preferences> Mouse> General tab.

---

### Post by blackened on 2010-01-18
For the touchpad, try installing gynsaptics through apt-get:

```
sudo apt-get install gsynaptics
```

For the webcam install eee-control:
[LIST]
[*]Jaunty and earlier: [http://greg.geekmind.org/eee-control/]("http://greg.geekmind.org/eee-control/")
[*]Karmic: [http://danamlund.dk/eee-control/eee-control.html]("http://danamlund.dk/eee-control/eee-control.html")
[/LIST]

---

### Post by DZ* on 2010-01-18
> **snowpine said:**
> Ubuntu and Ubuntu Netbook Remix are identical, except for the "launcher" interface optimized for viewing on small screens. Ubuntu Netbook Remix is **not** "tailored" for the Atom processor (lots of netbooks have other types of processor such as Celeron) and its hardware requirements are the same, as you can see here.

If it's just the launcher, what do they mean by these Atom-specific optimizations? -

"What have you done with Intel to optimize the new platform for Atom?

-- Canonical has been working closely with Intel for more than a year on support for the Intel Atom processors. The optimizations mostly center around taking advantage of the power-saving extensions afforded by the Intel Atom processors, as well at some boot optimizations."

[http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical](http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical)

---

### Post by snowpine on 2010-01-18
> **DZ* said:**
> If it's just the launcher, what do they mean by these Atom-specific optimizations? -

"What have you done with Intel to optimize the new platform for Atom?

-- Canonical has been working closely with Intel for more than a year on support for the Intel Atom processors. The optimizations mostly center around taking advantage of the power-saving extensions afforded by the Intel Atom processors, as well at some boot optimizations."

[http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical](http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical)

A year or so ago, Canonical developed a "port" of Ubuntu called lpia (low power intel architecture). It was sold to hardware manufacturers (like Dell) who needed a custom OS for their netbooks, as well as available to the general public [here]("http://cdimage.ubuntu.com/ports/releases/"). It was not very popular and the project has been discontinued. "Regular" i386 Ubuntu runs just fine on the Atom in my experience, no special "optimizations" are necessary. Any recent Linux distro should run okay on the Atom, since support is built into the  Linux kernel itself. (I personally use Fedora on my eee and until recently Arch on my Dell Mini.)

---

### Post by blackened on 2010-01-18
> **snowpine said:**
> A year or so ago, Canonical developed a "port" of Ubuntu called lpia (low power intel architecture). It was sold to hardware manufacturers (like Dell) who needed a custom OS for their netbooks, as well as available to the general public [here]("http://cdimage.ubuntu.com/ports/releases/"). It was not very popular and the project has been discontinued. "Regular" i386 Ubuntu runs just fine on the Atom in my experience, no special "optimizations" are necessary. Any recent Linux distro should run okay on the Atom, since support is built into the  Linux kernel itself. (I personally use Fedora on my eee and until recently Arch on my Dell Mini.)

IIRC the benchmarks of lpia vs i386 showed only marginal differences in power consumption and it was concluded that maintaining a different set of packages for each architecture wasn't worth the limited benefits and that the extra build only served to draw efforts away from distribution-wide power conservation efforts.

From what I've read, there will be no lpia build for 10.04, unless someone in the community takes it upon themselves to make one.

---

### Post by DZ* on 2010-01-18
> **snowpine said:**
> Any recent Linux distro should run okay on the Atom, since support is built into the  Linux kernel itself. (I personally use Fedora on my eee ...

Do you know what kind of Atom "tricks" they used in Fedora? -

"All software packages on 32-bit (x86_32) architecture have been compiled for i686 systems, with special optimization for the Intel Atom processors used in many netbooks, but without losing compatibility with the overwhelming majority of CPUs."

(from [http://fedoraproject.org/wiki/Fedora_12_Announcement](http://fedoraproject.org/wiki/Fedora_12_Announcement))

---

### Post by snowpine on 2010-01-19
> **DZ* said:**
> Do you know what kind of Atom "tricks" they used in Fedora? -

"All software packages on 32-bit (x86_32) architecture have been compiled for i686 systems, with special optimization for the Intel Atom processors used in many netbooks, but without losing compatibility with the overwhelming majority of CPUs."

(from [http://fedoraproject.org/wiki/Fedora_12_Announcement](http://fedoraproject.org/wiki/Fedora_12_Announcement))

I'm not an expert... here's my layman's understanding: A lot of distros (Ubuntu included) are compiled for i386, so they will run on old Pentium 1 computers and the like. Fedora switched to i686 (like Arch, etc.) so it's optimized for newer processors (including the Atom) at the expense of leaving behind some very old hardware. (I think they have an alternate i586 version if you need it.)

---

### Post by warfacegod on 2010-01-19
> **snowpine said:**
> I'm not an expert... here's my layman's understanding: A lot of distros (Ubuntu included) are compiled for i386, so they will run on old Pentium 1 computers and the like. Fedora switched to i686 (like Arch, etc.) so it's optimized for newer processors (including the Atom) at the expense of leaving behind some very old hardware. (I think they have an alternate i586 version if you need it.)

Can you get an Ubuntu i686 compiled .iso?

---

### Post by snowpine on 2010-01-19
> **warfacegod said:**
> Can you get an Ubuntu i686 compiled .iso?

Not to my knowledge, but it has been suggested:

[http://brainstorm.ubuntu.com/idea/3154/](http://brainstorm.ubuntu.com/idea/3154/)

I'm not sure what you're getting at here... I thought you said back on the 1st page that Ubuntu i386 is working really well for you?

---

### Post by warfacegod on 2010-01-19
> **snowpine said:**
> Not to my knowledge, but it has been suggested:

[http://brainstorm.ubuntu.com/idea/3154/](http://brainstorm.ubuntu.com/idea/3154/)

I'm not sure what you're getting at here... I thought you said back on the 1st page that Ubuntu i386 is working really well for you?

It is. It was just idle curiosity on my part. An interesting read. Basically want I got from it was that a very precise and exact technology has been, yet again, reduced to matters of opinion by those that use it and those that design it.

---

### Post by ydnom89 on 2010-01-22
Interesting... Since I've heard of UNR, I've always been curious how they can claim it's been optimized to Atom processors. Cool!

---

### Post by warfacegod on 2010-01-22
How goes the quest for Touch pad domination?

---

### Post by ubunterooster on 2010-01-22
VISEGRIP!? Software does not respond to variences in pressure; this is likely hardware. :(

---

### Post by blackened on 2010-01-22
> **ubunterooster said:**
> VISEGRIP!? Software does not respond to variences in pressure; this is likely hardware. :(

It's software. I have the same make/model machine and the multi-touch can be really flaky if it isn't set up correctly. By flaky I mean barely works.

---

### Post by warfacegod on 2010-01-22
This could also *possibly* be an issue with one of the recent updates. I've notice, over the last week or so, that my Touch pad is much more sensitive than it was. The only thing that has been installed to my laptop is htop and the updates (for this install, ignoring the lunatic crap I'm doing to my other partition).

---

### Post by ubunterooster on 2010-01-22
> **blackened said:**
> It's software. I have the same make/model machine and the multi-touch can be really flaky if it isn't set up correctly. By flaky I mean barely works.
My bad :( I did not know this....now I do :) thanks for the correction

---

### Post by ydnom89 on 2010-01-22
Ubunurooster, your reactions amuse me. Whether it is a hardware issue or software issue, I have decided to forgo it for now until I can build a desktop. Then I'll have a stable PC to work on and then I can tinker with this netbook until I'm satisfied.

---

### Post by blackened on 2010-01-22
> **ydnom89 said:**
> ...I can tinker with this netbook until I'm satisfied.

You're obviously new here otherwise you would already know that it is a violation of the physics of the known universe to construct a sentence that contains or implies the words tinker, Linux, and satisfy.

Satisfaction in tinkering is a carrot on a string, the fun lies in tinkering. :D

---

### Post by warfacegod on 2010-01-22
> **blackened said:**
> You're obviously new here otherwise you would already know that it is a violation of the physics of the known universe to construct a sentence that contains or implies the words tinker, Linux, and satisfy.

Satisfaction in tinkering is a carrot on a string, the fun lies in tinkering. :D

I'd second that but it would be pointless. It's a Law much akin to E=mc2, the Pythagorean Theorem, or that whole gravity thing.

That's why I started this thread, because I wasn't satisfied with being satisfied.

[http://ubuntuforums.org/showthread.php?t=1379471]("http://ubuntuforums.org/showthread.php?t=1379471")

---

### Post by ydnom89 on 2010-01-23
Haha good to know. :D

---

