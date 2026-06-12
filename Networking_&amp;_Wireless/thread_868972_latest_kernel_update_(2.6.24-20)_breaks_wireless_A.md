---
title: "latest kernel update (2.6.24-20) breaks wireless AND wicd?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2008-07-24
anyone else with this issue?

---

### Post by dpologea on 2008-07-24
Yes, I have this problem too. After the update to the latest kernel 2.6.24-20, I can not use wireless anymore. I have to use the previous version (2.6.24.19).

---

### Post by moore.bryan on 2008-07-24
well, i guess it's good to know it's not just me. to "gerry-rig" it to work, i found my issue to be with the experimental ath5k module. if you add the line ```
blacklist ath5k
``` to your /etc/modprobe.d/blacklist file, that should set it straight.

---

### Post by skankster on 2008-07-24
I got round it by booting to 2.6.24-19. You can also uninstall the update.
Obviously the route to fix is down to personal preference. :)

---

### Post by pixolex on 2008-07-25
> **moore.bryan said:**
> anyone else with this issue?

The same problem here...but for me just the 2.6.24-17 works NOW!!! 

With the -20 the wireless led just don't work.

---

### Post by easygod on 2008-07-25
> **moore.bryan said:**
> anyone else with this issue?

This  morning,I update the kernel to -20,then I can't find the wireless. 

how soon the new patch comming..

---

### Post by Archmage on 2008-07-25
2.6.24.20 is for testing purpose only. Why are you using a instable kernel on a stable OS?

---

### Post by moore.bryan on 2008-07-25
> **Archmage said:**
> 2.6.24**-**20 is for testing purpose only. Why are you using a **un**stable kernel on a stable OS?
how is it unstable if it was in the list of daily updates? the current [stable kernel]("http://www.kernel.org/") is 2.6.26, anyway...

---

### Post by steveneddy on 2008-07-26
> **moore.bryan said:**
> how is it unstable if it was in the list of daily updates? the current [stable kernel]("http://www.kernel.org/") is 2.6.26, anyway...

But not in Ubuntuland. Hardy is on this kernel program and when the kernel is ready, it will be put out for non-backport and proposed users to use.

Just because the actual Linux kernel is up to .26 doesn't mean that the Ubuntu Hardy kernel will keep up. We stick with a kernel and implement the fixes and repairs that the devs deem necessary.

---

### Post by Master Chief on 2008-07-26
> **steveneddy said:**
> ...Just because the actual Linux kernel is up to .26 doesn't mean that the Ubuntu Hardy kernel will keep up. We stick with a kernel and implement the fixes and repairs that the devs deem necessary.

Err correction; the problem here is that the developers can't keep up with the latest Kernel versions, while other distro's can. Just a fact.

---

### Post by steveneddy on 2008-07-26
> **Master Chief said:**
> Err correction; the problem here is that the developers can't keep up with the latest Kernel versions, while other distro's can. Just a fact.

This is incorrect. If you are going to have an LTS release, you have to keep a stable version of a kernel. Once you get a stabel version, it is easier to maintain an LTS version with one kernel version than a parade of new kernel versions. Desktop is only three years, after all.

Heck, I still use the kernel from 6.06 Server Edition in my LTS Ubuntu server from two years ago and it still runs fine.

This is what Ibex is for, new kernels and bleeding edge software.

Just because Kernel.org releases a new kernel does not mean that it is meant for the general consumer. The developers will tweak the kernel for each distro.

---

### Post by kostkon on 2008-07-26
Obviously, all of people who got the update have the *Proposed* repository enabled. This repository is only to be used by advanced users to test packages that are meant to be released later as official updates. These packages in most cases are not for general use.

If you want to have a normal system and get only the official updates, please go to *System -> Administration -> Software Sources* and deselect the *Proposed* repository option.

The vast majority of the users did not get this update, obviously.

---

### Post by moore.bryan on 2008-07-26
> **steveneddy said:**
> But not in Ubuntuland.
very true... i do need to keep reminding myself we live in a *somewhat* different linux world than many other distros.
> **Master Chief said:**
> Err correction; the problem here is that the developers can't keep up with the latest Kernel versions, while other distro's can. Just a fact.
i don't know if they *can't* keep-up, but i know they *don't*.
> **steveneddy said:**
> This is incorrect. If you are going to have an LTS release, you have to keep a stable version of a kernel. Once you get a stabel version, it is easier to maintain an LTS version with one kernel version than a parade of new kernel versions. Desktop is only three years, after all.
the stable version of the kernel **is** 2.6.26.
> **steveneddy said:**
> Heck, I still use the kernel from 6.06 Server Edition in my LTS Ubuntu server from two years ago and it still runs fine.
of course it's going to work fine, but there's a lot of us in "ubuntuland" who have hardware that never *quite* worked on earlier kernels and each one is a vast improvement... we're just hoping for the "perfect" one! ;-)
> **steveneddy said:**
> This is what Ibex is for, new kernels and bleeding edge software.
afaik, the kernel in intrepid is 2.6.26, so why not the updated 2.4.24 for the rest of us?
> **steveneddy said:**
> Just because Kernel.org releases a new kernel does not mean that it is meant for the general consumer.
however, when a new *stable* kernel is released, that **is** for the general consumer.
> **kostkon said:**
> Obviously, all of people who got the update have the *Proposed* repository enabled. This repository is only to be used by advanced users to test packages that are meant to be released later as official updates. These packages in most cases are not for general use.
very true, kostkon...
 > **kostkon said:**
> The vast majority of the users did not get this update, obviously.
this i'm not to sure of. one of the first pieces of "advice" i received in these forums was to enable this repo... i wouldn't be surprised if **a lot** of other people were also affected by this.

---

### Post by kostkon on 2008-07-26
> **moore.bryan said:**
> this i'm not to sure of. one of the first pieces of "advice" i received in these forums was to enable this repo... i wouldn't be surprised if **a lot** of other people were also affected by this.
That's a bad advice you got there. I have not seen this happening, to be honest. Thus, I am pretty sure the numbers of users having this repository enabled without knowing the consequences is very low.

I believe the majority of the experienced users here do not recommend to others to enable this repository. They may recommend you to enable the *Multiverse* and at the most the *Backports* repository.

---

### Post by gjoellee on 2008-07-26
2.6.24-20 was a ad update! keep on using 2.6.24-19 and don't install 2.6.24-20 for many this kernel does not even boot!

---

### Post by steveneddy on 2008-07-26
> **moore.bryan said:**
> 

the stable version of the kernel **is** 2.6.26.



But not for Hardy. Hardy's stable kernel is the 2.6.24-xx kernel and will probably stay that way through the life of the LTS.

Like I said, If you want a newer kernel, use Ibex.

Or you could always compile your own kernel.

Since I don't have time for constant tweaking and prefer a stable system, I'll stay with the stock Hardy kernel.

Not to hijack the thread, I use the proposed updates and my -20 kernel works great except for the wireless light blinking again with 3945 Intel wireless.

Bug filed.

[COLOR="Red"]**IMHO, a stable kernel maintained by talented developers makes for a stable release.**[/COLOR] There is nothing wrong with an old kernel, as long as the hardware works on that kernel. There are many threads discussing kernel compilation on the UF for those who feel they need a newer kernel.

---

### Post by moore.bryan on 2008-07-27
> **kostkon said:**
> That's a bad advice you got there.
perhaps, but it has never led me wrong thus far...
> **steveneddy said:**
> Or you could always compile your own kernel.
yeah, i've done this before and it is incredibly time consuming, although i did see quite a jump in responsiveness on some ends...
 > **steveneddy said:**
> [COLOR=Red]**IMHO, a stable kernel maintained by talented developers makes for a stable release.**[/COLOR] There is nothing wrong with an old kernel, as long as the hardware works on that kernel. There are many threads discussing kernel compilation on the UF for those who feel they need a newer kernel.
i **completely** agree... and you point-out the possible "fatal flaw" in using an older kernel: hardware (the bane of linux's existence)!
;-)
[quote=gjoellee]2.6.24-20 was a ad update! keep on using 2.6.24-19 and don't install 2.6.24-20 for many this kernel does not even boot![/quote]
i wouldn't go this far... i've had no problems after my wireless tweak.

---

### Post by stefutu on 2008-08-08
After the latest update two days ago, me and my co-worker, both using Ubuntu are not able to use the wireless. 
It is very easy to install the  updates. But how do I uninstall them. I removed (not completely removed)the Wi-Fi radar and Network manager and I installed WICD. Now I can see the wireless networks but it will not connect. It is not working! I cannot get a wired connection so we are stuck here.. I will keep looking on how to uninstall the updates in Ubuntu 8.04.
Oh both me and my co-worker have the Intel (R) 4965AGN installed.

---

### Post by moore.bryan on 2008-08-08
so, you can **see** the networks, but not connect? if you open a terminal and type "ping www.google.com" (without the quotes), what prints-out?

---

