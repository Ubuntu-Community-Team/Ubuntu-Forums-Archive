---
title: "Ubuntu 32 or 64 bits on an Atom with 1gb of RAM?"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by nicocarbone on 2010-08-30
I am building a small PC using an Intel Atom D510 with 1gb of RAM. It will be used mainly for web surfing.

Of course I am installing in it Ubuntu 10.04, but I can't decide between 32 and 64 bits. On one hand 64 bits uses more RAM (remember I only have 1 gb) and has some problems with Flash, but on the other, it is faster, which can be important when using a slow processor like the Atom. Besides, I've read on various web pages that programs compiled in 64 bits usually assume that the processor has more capabilities (like SSE) and, by using them, can be more efficient.

What would you suggest I choose? Has anyone tested the difference between 32 and 64 bits on an Atom?

Thanks you very much

---

### Post by lukeiamyourfather on 2010-08-30
Isn't the Atom 32-bit only? Either way, 32-bit is all you need since there's only 1GB of memory.

---

### Post by lukeiamyourfather on 2010-08-30
Never mind, that processor is 64-bit.

[http://ark.intel.com/Product.aspx?id=43098](http://ark.intel.com/Product.aspx?id=43098)

Regardless, 32-bit is all you need.

---

### Post by kerry_s on 2010-08-30
go 64 bit it runs better. i'm using 64 bit on the atom.

---

### Post by soldier1st on 2010-08-30
> **kerry_s said:**
> go 64 bit it runs better. i'm using 64 bit on the atom.
i disagree, he only has 1GB memory and 64bit will take alot of that so until he has more memory the 32bit version will be better. now if the system had say 3GB or more then i could see 64bit being useful as then it could better take advantage of that extra memory.

---

### Post by scorp123 on 2010-08-30
> **soldier1st said:**
> i disagree, he only has 1GB memory and 64bit will take alot of that so until he has more memory the 32bit version will be better. now if the system had say 3GB or more then i could see 64bit being useful as then it could better take advantage of that extra memory. Fully agree with you. 64-bit with only 1 GB of RAM is totally pointless.

---

### Post by kerry_s on 2010-08-30
i only have 1 gb ram, look at the screen shot, it runs better then 32 bit, everythings faster, video playback is great, i would get choopy movies sometimes with 32 bit, only happens on some 1080p's now.

just add 1gb swap & don't worry about the ram.

it's not about how much memory, 64 bit is a performance system, yes it supports more memory, but thats not all it does.

---

### Post by scorp123 on 2010-08-30
> **kerry_s said:**
>  everythings faster I doubt you see any noticeable speed differences on a low-end CPU like the Atom :D

> **kerry_s said:**
>  it's not about how much memory, 64 bit is a performance system, yes it supports more memory, but thats not all it does. A 64-bit OS also **_uses_** more memory. Simple fact of life. With only 1 GB of RAM it's simply not worth the overhead. Different story if you have 4 GB or 8 GB in your system ... then yes, forget about 32-bit and/or PAE and go straight for 64-bit. But with only 1 GB of RAM ... naaah.

---

### Post by philinux on 2010-08-30
> **nicocarbone said:**
> I am building a small PC using an Intel Atom D510 with 1gb of RAM. It will be used mainly for web surfing.

Of course I am installing in it Ubuntu 10.04, but I can't decide between 32 and 64 bits. On one hand 64 bits uses more RAM (remember I only have 1 gb) and has some problems with Flash, but on the other, it is faster, which can be important when using a slow processor like the Atom. Besides, I've read on various web pages that programs compiled in 64 bits usually assume that the processor has more capabilities (like SSE) and, by using them, can be more efficient.

What would you suggest I choose? Has anyone tested the difference between 32 and 64 bits on an Atom?

Thanks you very much

64 bit will use more memory. Make your own mind up.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by nicocarbone on 2010-08-30
Thanks everyone for your answers.

I see that there are different opinions about what is better, so I decided to do some tests myself. I used a borrowed PC with an Intel Atom 230 (1.6Ghz single core, hyperthreading enabled) and 1Gb of RAM (my D510 has not arrived yet), and did some internet benchmarks on Ubuntu 10.04.1 64 and 32 bits. 

I booted the system using a USB image of both OS, and installed Chrome Stable and Flash in the 64 bit system, and Chrome Stable in the 32 bits system (Chrome has Flash built-in in the 32bit version). In both versions, I installed some extensions in order to simulate how I plan to use the PC: Adblock, Docs PDF/PowerPoint Viewer, and the Chrome Ambiance theme and scrollbar. The results were the following:


Peacekeeper ([http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)):

64 bits: 1259
32 bits: 895


GuiMark (Flash version, [http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html](http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html)):

64 bits: ~10fps
32 bits: ~6fps


Youtube: (360p, [http://www.youtube.com/watch?v=_EN1y8o7XFM](http://www.youtube.com/watch?v=_EN1y8o7XFM)):

64 bits: smooth playback, 400mb of RAM used, around 60% of each core used (2 cores because Hyperthreading is enabled)
32 bits: not smooth playback, 310mb of RAM used, around 50% of one core, and 100% of the other


Based on this tests, browsing experience is much better using the 64bit version of Ubuntu in an Intel Atom. It is true, the 64 bit version uses more memory, but the performance is really better. In fact YouTube is usable in 64bits, but not in 32 bits.

I am really surprised by the Flash results, considering that in the 64 version the plugin must be used inside a wrapper and that the built-in Flash of Chrome x86 is optimized. But I checked this results a couple of times and they are right. What do you think?

---

### Post by Jazzy_Jeff on 2010-08-30
It really doesn't matter what we think at this point. I would go with the version that ran better in your tests. And you can always upgrade to 2 gig of ram later on that computer.

---

### Post by Jim_in_Omaha on 2010-08-30
> **nicocarbone said:**
> Thanks everyone for your answers.


Youtube: (360p, [http://www.youtube.com/watch?v=_EN1y8o7XFM](http://www.youtube.com/watch?v=_EN1y8o7XFM)):

64 bits: smooth playback, 400mb of RAM used, around 60% of each core used (2 cores because Hyperthreading is enabled)
32 bits: not smooth playback, 310mb of RAM used, around 50% of one core, and 100% of the other



90 meg more for the youtube video? Small price to pay for the performance..

---

### Post by scorp123 on 2010-08-30
> **nicocarbone said:**
>  What do you think? Respect! But please be aware that other factors such as background tasks (which may produce I/O in the background) and caching may drastically influence your benchmarks one way or the other. So if you really really feel that 64-bit is worth it despite using a bit more memory ... go ahead. You benchmarked the system (respect!) in question so you're really the only one here who is qualified to make definitive statements about its performance under 64-bit vs. 32-bit.

My personal opinion is that 1 GB of RAM is not enough ... so if I (and I repeat: this is my personal opinion) really wanted to go 64-bit I'd at least add more RAM to that system ... 

:D

---

### Post by kerry_s on 2010-08-30
i told you so. :lolflag: (you know i had to)

wait till you try movies, the playback is nice, usually only 720p is recommended on the atom, but i've played a lot of 1080p movies just fine, there are some that do stutter or slow mo.

the 3d games are run nice to, if you play those.

don't worry about the extra ram use it's well worth it, i'v yet to experience problems & even swap has always been less then 100mb. besides if your not using it your wasting it. :D

---

### Post by M93 on 2010-08-30
32 is better for ur amount of ram + its recommended for most users
64 is not recommended for daily desktop usage, besides its got some flash problems, thunderbird issues and some 32bit programes might not work
so stick with the 32 till then :)

---

### Post by kerry_s on 2010-08-30
> **M93 said:**
> 32 is better for ur amount of ram + its recommended for most users
64 is not recommended for daily desktop usage, besides its got some flash problems, thunderbird issues and some 32bit programes might not work
so stick with the 32 till then :)

yeah right, **everything** works fine on mine, even flash, i can listen to pandora & play flash games at the same time.

i'v got pandora playing now, have transmission downloading movies, while browsing the web, forums, even watching some videos.
if this is what they call problems, i'll take them.

---

### Post by oldos2er on 2010-08-30
> **M93 said:**
> 64 is not recommended for daily desktop usage

Not every word that drips from the mouth of Canonical is infallible Holy Writ. Here's a different opinion from [http://ubuntuforums.org/announcement.php?f=343](http://ubuntuforums.org/announcement.php?f=343)

"The closure of this forums is based on the fact that *64 bit Ubuntu has matured and there are very few 64 bit specific issues*."

If you have 64-bit capable hardware (plus more than a tiny amount of RAM), use 64-bit Ubuntu.

---

### Post by ShakeyJake on 2010-08-31
> **oldos2er said:**
> If you have 64-bit capable hardware (plus more than a tiny amount of RAM), use 64-bit Ubuntu.

I couldn't agree more. There are zero 64-bit issues these days and the benefits (negligible though they may be) are well worth it. I was forced to go 64-bit a few years back when I got 8GB of memory and there used to be loads of problems and niggles. None of that these days though.

Is the 32 vs 64 bit ram thing something I could test using VMs? Or would the process of using a VM bias/negate the test?

---

### Post by nicocarbone on 2010-08-31
Well, I got the D510MO. I finally installed Ubuntu 10.04.1 64bits, and I am very happy with it.

It is true, 1Gb of RAM can be a problem if you do heavy multitasking or use a lot of tabs in the browser, but it is not a problem to me. Also, as someone say, I can always add another stick of RAM latter.

I have just one concern, it appears that the Atom D510 does no have frequency scaling. Does anyone know if this is a problem of the CPU or a limitation of Ubuntu and the version of the Linux kernel it's using? Has anyone succeeded in enabling frequency scaling in a Atom D510?

---

### Post by uRock on 2010-08-31
I have the Atom in my netbook and I use the 32bit install. Runs 2x as fast as the XP that came with it. Linux has a lot to prove before I'll use 64bit again.

---

### Post by ShakeyJake on 2010-09-01
What does

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

output?

---

### Post by nicocarbone on 2010-09-01
> **ShakeyJake said:**
> What does

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

output?

I did what you say, and the output was: 

```

cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: No existe el archivo o directorio

```

It is in Spanish, and it mays something like "file or folder does not exist".

Any suggestions?

---

### Post by Automat2 on 2010-09-01
I'm using 64bit because I've got a AMD quad-core and 4GB RAM, and I got some problems with certain apps like Flash. Nothing major, and nothing unsolvable, but the statement "zero issues", compared with the 32bit version, it seems a bit wrong to me.

---

### Post by ShakeyJake on 2010-09-01
So I tested the difference architectures using a VM and was quite surprised by the results. Setup: 2 identical Ubuntu 10.04LTS VMs, one with x86 and the other x64. Each has 2048MB of ram, 2 3.2GHz cpu cores and 128MB of video ram. They are, in every way, identical. Each simply had the OS installed to a 16GB disk and then.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install conky
```

Conky was then modified to show (in size 24 letters no less)

```
Operating System:
${execi 3600 lsb_release -d | cut -f 2}
Architecture:
${conky_build_arch}
Memory Usage:
$mem/$memmax = $memperc%

```

I loaded up conky and system monitor, the systems were left to idle (screensavers turned off) for 10 mins. And the results?

[IMG]http://lh3.ggpht.com/_B8hZv60xItE/TH6gSKXgWZI/AAAAAAAAAHA/4iL9QkBptpo/s1280/Screenshot.png[/IMG]

As you can see, 64-bit uses double the memory just sitting at the desktop. Double! A third of a GB just idling is quite substantial if you only have a GB such as the atom being discussed here. Maybe there is something to be said for 32-bit on a low-hardware platform.

NOTES:
This test was conducted with virtual machines. This was good, as two identical machines could be created but may be subject to some sort of skewing by the act of running through the virtualisation layer.

Host machine (in case you're wondering what affect this may or may not have on the VMs):
Phenom II 955 (4x3.2GHz), 8GB Corsair Dominator 1600MHz DDR3. Virtual disks are on a WD Caviar Black that is _not_ the host machine OS drive. Host machine OS is Ubuntu 10.04 LTS x64.

CPU usage was identical in both machines. At the exact second I took the screenshot the 32-bit was using slightly more, but it could just as easily have been the other way round.

Lastly, in my haste to position everything so everything could be seen, I put the virtualbox window over the architecture output of the 32-bit machine. Rest assured it says '(i686)' under there. Didn't notice this 'till I was writing this post and I've already closed everything down. ](*,)

EDIT - My x86 image was a while old, whilst I didn't have a x64 image on this machine so I torrented a fresh one. That might explain why the x64 has '10.04.1' shown in conky. I have no idea what effect this (presumably newer version of ubuntu) has on memory use.

---

### Post by kerry_s on 2010-09-01
i can tell you my memory use, was around a 100 more then 32 bit. i didn't really care though, as the performance was well worth the extra ram use. 

what do you have ram for if you don't want to use it?

---

### Post by uRock on 2010-09-01
I'd rather use my RAM for FF and VBox instead of the 64bit kernel's stuff. I just went back to 32bit from 64bit and I don't see it running any slower and I have been running 2 vboxes, while doing my regular stuff.

---

### Post by KdotJ on 2010-09-01
I have an atom in my nebook, also with 1gb of ram. I have got 64bit ubuntu on it, and never even thought about putting 32bit ubuntu on it. I don't see the point, the processor is capable of 64bit, so why deprive it?
64bit is the way forward, so why not go with it if you can. Ubuntu 64bit is practically issue free for the most and I've personally never had any problems with it at all.

---

