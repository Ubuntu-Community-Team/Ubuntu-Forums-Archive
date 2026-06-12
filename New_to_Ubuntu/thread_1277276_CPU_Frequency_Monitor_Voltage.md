---
title: "CPU Frequency Monitor Voltage"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by brain frog on 2009-09-28
I am new to ubuntu so am still learning so remember that in any reply.

Ubuntu is currently installed on an old pc parts cobbled together on my desk, its more of an experiment pc that im using to learn about linux/ubuntu.

the pc currently is not being used for anything more that mucking about and internet browsing and i wish to underclock the cpu.

Ubuntu has an automatic underclocking utility called CPU Frequency Monitor this is what i am experimenting with but it may be worth abandoning it.

I want it to be always underclocked i attempted this guide to keep it set at always underclocked after reboot it failed [http://ubuntuforums.org/showthread.php?t=1164470&page=2](http://ubuntuforums.org/showthread.php?t=1164470&page=2)

I have installed software that tells me cpu temp and voltage and CPU Frequency Monitor does not seem to be very well tuned.

2400 1.5v
2200 1.4v
2000 1.3v
1800 1.2v
1000 1.1v


Through tests in xp i know that the core is stable at 1000MHz at 0.8v and can go as low as 800MHz.

Commands in the thread i have pasted have shown the avaable setting/frequency for this software, but i would like to know how i can ajust them and the voltage settings for each so the options and voltages are of my choosing, aswell as choosing what mode it starts up in.

How would i do this?

Thankyou

---

### Post by sideaway on 2009-09-28
If you want to underclock it, you'll succeed in more stability if you do it at BIOS level.

---

### Post by brain frog on 2009-09-28
This was the first thing i thought of, i can only raise the cpu fsb clock in bios, no other options.

---

### Post by philinux on 2009-09-28
> **brain frog said:**
> I am new to ubuntu so am still learning so remember that in any reply.

Ubuntu is currently installed on an old pc parts cobbled together on my desk, its more of an experiment pc that im using to learn about linux/ubuntu.

the pc currently is not being used for anything more that mucking about and internet browsing and i wish to underclock the cpu.

Ubuntu has an automatic underclocking utility called CPU Frequency Monitor this is what i am experimenting with but it may be worth abandoning it.

I want it to be always underclocked i attempted this guide to keep it set at always underclocked after reboot it failed [http://ubuntuforums.org/showthread.php?t=1164470&page=2](http://ubuntuforums.org/showthread.php?t=1164470&page=2)

I have installed software that tells me cpu temp and voltage and CPU Frequency Monitor does not seem to be very well tuned.

2400 1.5v
2200 1.4v
2000 1.3v
1800 1.2v
1000 1.1v


Through tests in xp i know that the core is stable at 1000MHz at 0.8v and can go as low as 800MHz.

Commands in the thread i have pasted have shown the avaable setting/frequency for this software, but i would like to know how i can ajust them and the voltage settings for each so the options and voltages are of my choosing, aswell as choosing what mode it starts up in.

How would i do this?

Thankyou

See post #9 it may solve your problem
[http://ubuntuforums.org/showthread.php?t=1274455](http://ubuntuforums.org/showthread.php?t=1274455)

Set yours to powersave.

---

### Post by peculiar penguin on 2009-09-28
> Ubuntu has an automatic underclocking utility called CPU Frequency Monitor this is what i am experimenting with but it may be worth abandoning it.It's not "an automatic underclocking utility". IF your system supports dynamic frequency scaling, it will merely show you what's going on with that. It also allows you to choose between different CPUFreq governors in the kernel, which control how/when the system clocks up/down.

> I have installed software that tells me cpu temp and voltage and CPU Frequency Monitor does not seem to be very well tuned.

2400 1.5v
2200 1.4v
2000 1.3v
1800 1.2v
1000 1.1vThese default values are specified by the CPU manufacturer (resp. the BIOS), not the CPU Frequency Scaling Monitor thingy.

> Through tests in xp i know that the core is stable at 1000MHz at 0.8v and can go as low as 800MHz.

Commands in the thread i have pasted have shown the avaable setting/frequency for this software, but i would like to know how i can ajust them and the voltage settings for each so the options and voltages are of my choosing, aswell as choosing what mode it starts up in.
For under**volting** you'll need either a BIOS supporting this, or a patched kernel (from [here]("https://launchpad.net/%7Elinux-phc/+archive/ppa"), for example, or download, patch, and compile it yourself). See [this thread]("http://ubuntuforums.org/showthread.php?t=786402").

---

### Post by brain frog on 2009-09-28
Thanks for the responses.

I did manage to set it up so it is on powersave by default.

My setup does allow underclocking its just the options are not in the bios it is made of parts of older system and i have tested its underclocking in xp i am looking for having 1000MHz at .8v.

It appears asthough underclocking is the way to go.

I have an amd64 cpu single core and the guide sent only worked for intel.

I have looked at some software i have googled but could not find a good guide for those that are new to ubuntu that worked.

Who has underclocked there amd like i wish to and how did you do it?

---

