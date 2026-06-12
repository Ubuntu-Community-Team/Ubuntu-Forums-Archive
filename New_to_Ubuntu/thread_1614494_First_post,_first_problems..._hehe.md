---
title: "First post, first problems... hehe"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by sagoy on 2010-11-05
Good day to all

I've been interested in Ubuntu for well over a year now, but I never had a chance to get it, because I was too lazy to learn something new, and downloading the ubuntu desktop installer would lake a long time since the Internet connection here isn't super fast, plus my DVD burner died on me a year ago and I haven't replaced it yet.

Now I'm getting a new laptop, and we want to run Ubuntu on it. So I decided to try out Ubuntu on my old desktop so I searched around, found wubi, and used that to install Ubuntu.

My desktop just has 512mb of RAM and 80Gb of space. Small right? :(
Well this pc has 2 partitions, about 40Gb each, and I took 10Gb off of Drive D to install Ubuntu with wubi.

Everything went smoothly, a little dragging, but still smooth.

After the installation I noticed some problems

1. Sound didn't work
2. Ubuntu kept on lagging like hell.

Well for the first problem I noticed that when I boot on windows first, then reboot and go to ubuntu, sound doesn't work, but when I go Ubuntu first, sound works fine.

For the second problem, I noticed it only lags like hell if I enable the "3rd level graphics mode". When I switch it back to "No flashy effects" or something, it's bearable, but still lags sometimes..

So is ubuntu really eating up my 512mb of ram that much?

I tried to do free -m and got this

  total       used       free     shared    buffers     cached
Mem:           493        488          5          0         44         88
-/+ buffers/cache:        355        137
Swap:          254        120        134

NOTE: I AM A COMPLETE UBUNTU NOOB, if I ever need to do something in terminal please tell me specific codes. Thanks much... I'm still going to continue trying out Ubuntu until I get my new laptop and then I'll see if I can run Ubuntu on it, since I heard new hardware might not be supported yet.

---

### Post by kaldor on 2010-11-05
WUBI is unstable if you ask me. I tried it once and got very wonky results (including the two issues you have).

If you can, I'd greatly recommend you try to partition your HD. 80 GB is not a huge lot, but 30 GB to Ubuntu should be okay.

Welcome to the community, by the way :)

---

### Post by sagoy on 2010-11-05
Thanks. Yeah I was just trying out wubi, but for the new laptop, I'm going to look for a way to get it on a CD or a USB stick. So 10.04 isn't really slow at all? or lagging? or buggy with sound? I've heard Ubuntu is fast, that's why I was wondering why it's laggy after I installed it.

---

### Post by kaldor on 2010-11-05
> **sagoy said:**
> Thanks. Yeah I was just trying out wubi, but for the new laptop, I'm going to look for a way to get it on a CD or a USB stick. So 10.04 isn't really slow at all? or lagging? or buggy with sound? I've heard Ubuntu is fast, that's why I was wondering why it's laggy after I installed it.

Well, Ubuntu is on the more "bloated" end when it comes to Linux (in my opinion) and in some cases may seem slow.

My workaround was to remove Ubuntu-one software. That sped it up on a real machine. Not sure about WUBI, though.

---

### Post by yeats on 2010-11-05
> My desktop just has 512mb of RAM and 80Gb of space. Small right?

This should be plenty to run Ubuntu, depending on what your needs are.

> After the installation I noticed some problems

1. Sound didn't work
2. Ubuntu kept on lagging like hell.

Can you post what kind of hardware you're installing on?  Specifically, what kind of video card and sound card do you have?  Also, which version of Ubuntu? (people generally will assume 10.10 since that is the latest release)

---

### Post by tkoco on 2010-11-05
> **kaldor said:**
> Well, Ubuntu is on the more "bloated" end when it comes to Linux (in my opinion) and in some cases may seem slow.

My workaround was to remove Ubuntu-one software. That sped it up on a real machine. Not sure about WUBI, though.

I agree about the bloat. Sagoy, if you have no intention of using Bluetooth with Ubuntu, then remove "bluez" packages. If you will not be printing, remove "cups" packages. Removing these will help speed up the desktop. If you develop a need for these packages, you can always add them back.

---

### Post by cipherboy_loc on 2010-11-05
I run a "similar" system on my laptop with 512MB ram and 80GB disk space. I dedicated 30GB to Ubuntu out of that 80GB. After a lot of modifications, my laptop as a snappy boot up time <1m 30s. For the boot up I recommend the use of BUM ([COLOR=Red]b[/COLOR]oot [COLOR=Red]u[/COLOR]p [COLOR=Red]m[/COLOR]anager). Remove any un-needed start up processes (Like bluetooth, etc), but be careful about which ones you remove. It can leave your system in an unstable (or even un-bootable) state. I also ditched GNOME in favor of Fluxbox, but you can speed up the GNOME post-login time (I forgot where I saw that article...). 


Anyways, I agree with Tkoco. Remove all and any un-needed packages (Mono, Bluez, Cups, etc, etc). Its best to use Synaptic (alt+f2, and type in "gksudo synaptic" without the quotes. Enter your password) to find and remove any un-needed packages.

---

### Post by tkoco on 2010-11-07
> **cipherboy_loc said:**
> I run a "similar" system on my laptop with 512MB ram and 80GB disk space. I dedicated 30GB to Ubuntu out of that 80GB. After a lot of modifications, my laptop as a snappy boot up time <1m 30s. For the boot up I recommend the use of BUM ([COLOR=Red]b[/COLOR]oot [COLOR=Red]u[/COLOR]p [COLOR=Red]m[/COLOR]anager). Remove any un-needed start up processes (Like bluetooth, etc), but be careful about which ones you remove. It can leave your system in an unstable (or even un-bootable) state. I also ditched GNOME in favor of Fluxbox, but you can speed up the GNOME post-login time (I forgot where I saw that article...). 


Anyways, I agree with Tkoco. Remove all and any un-needed packages (Mono, Bluez, Cups, etc, etc). Its best to use Synaptic (alt+f2, and type in "gksudo synaptic" without the quotes. Enter your password) to find and remove any un-needed packages.

In addtion to all of the items which have been said, if you are not going to burn CDs/DVDs on your system, remove all CD/DVD burner programs. Why? A system daemon is used to watch the CD/DVD burner for blank media and that daemon chews up a lot of time. The only safe method which I found that makes the daemon "go away" is if there are no CD/DVD burning programs on the system.

Again, if you need CD/DVD burning capability, you can always add it back in.

---

