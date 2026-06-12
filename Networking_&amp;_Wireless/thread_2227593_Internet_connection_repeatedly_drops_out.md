---
title: "Internet connection repeatedly drops out"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by rudy5 on 2014-06-03
Not a new problem, not to me or this forum. But I haven't been able to find an explanation, or even a solution that might be applicable.

I go through periods when I do not have a reliable wireless internet connection on my Toshiba laptop running Ubuntu 10.4. I can go weeks or even months without a problem, then I'll run into these what I call "sunspots". My computer will suddenly lose connection to the internet. I'll click a link to launch apage, the little "I'm thinking" circle starts spinning, and spins, and spins, and spins, then I'll get a "Problem finding page" error message, followed shortly by a message that I'm now disconnected from the internet, followed a few moments later by a "Password authentication required" dialogue box. 

Reconnecting within the same browser session worked, for a little while; but then that stopped working, and I had to resort to more extreme measures. Rebooting would usually solve the problem, albeit only for a few hours, or an hour anyway. Sometimes, it'll solve the problem for fifteen or twenty minutes. Sometimes, like tonight, I might have a few moments of connection before the connection is broken. (This is my third try now at getting this query posted.) 

After a few weeks of this, these "sunspots" went away, and I could go for weeks or even months without this problem. I'm interested in a solution, sure, esp. one that doesn't involve some elaborate workaround, e.g. USB-to-Ethernet conversion this-or-that, digging deep into the guts of the computer to downgrade / replace this or that driver that the last upgrade I did screwed up, or whatever. But even more than this .. .

Does anybody have a scientific-rational explanation for what is happening? It's a newish experience for me, in thirty years of using computers. I'm not used to this sort of erratic behaviour from 1/0 machines: either they work, all the time, or they don't work, at all: that's been my experience. The intermittent nature of this problem, and the fact that it has persisted over a few years, strongly suggests to me that it's not a hardware issue but the result of some level of software interference / manipulation / ****ery of sort happening in the background.

Does anybody have any light to shet, What happens to a computer that causes it to lose its mind like this? Is this a brand-new problem (no), and if not, has anyone out there who's encountered it ever been able to sort out what causes this issue?

Holding my breath, and crossing my fingers that I can post this before the sunspots act up again .. .

---

### Post by varunendra on 2014-06-05
> **rudy5 said:**
> ....Does anybody have a scientific-rational explanation for what is happening? It's a newish experience for me, in thirty years of using computers. I'm not used to this sort of erratic behaviour from 1/0 machines: either they work, all the time, or they don't work, at all: that's been my experience. The intermittent nature of this problem, and the fact that it has persisted over a few years, strongly suggests to me that it's not a hardware issue but the result of some level of software interference / manipulation / ****ery of sort happening in the background.

Does anybody have any light to shet, What happens to a computer that causes it to lose its mind like this? Is this a brand-new problem (no), and if not, has anyone out there who's encountered it ever been able to sort out what causes this issue?....

Not really a scientific explanation, and probably not an explanation you haven't already guessed, but here's what I know as the reason of above behaviour -

In one line, the reason is - **"Lack of proper mutual coordination among manufacturers, firmware/driver and kernel developers."**

Drivers and the kernel are developed by different teams/individuals, while the device and firmware come from the manufacturers. Even though the device remains the same, and the drivers *usually* get better with each new version, certain things may cause such erratic behaviour in-between. For example, if the manufacturer introduced some critical change in their firmware, and didn't provide details to the driver/kernel developers, things are bound to break and it may sometimes take a long time to catch up again. Similarly, sometimes a critical change in the kernel code causes 'Regressions' in drivers which takes some time to fix. Even if everything is going smoothly and consistently, sometimes a bug occurs in a new version of driver, although this kind of problem is usually fixed as soon as reported (at proper places, like bugzilla or launchpad).

You usually don't experience such issues in Windows or Macs because the development of device/firmware/drivers are done by the same entities there (the device manufacturers and their 'In-House' developers). So they know in advance what changes need to be made in the driver code to keep things nice and clean. In the world of Linux, most of the software development is done by different volunteer groups, and the level of mutual coordination/cooperation or pace of development is simply not good enough to keep things always smooth.

Now if you are interested in trying a few fixes/workarounds, which may or may not be as simple as you wish, we can start with a diagnostics report generated by 'wireless_script' mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by rudy5 on 2014-06-07
Thank you Varun, your reply is indeed informative and (therefore) helpful. I'll do what I can to help by following your suggestion about reporting the issue when it arises.

Typically, this system senses that we're talking about it, and it is on its very best behaviour --- hasn't timed out since I posted this!

I'll report back here as well.

---

### Post by rudy5 on 2014-09-09
Well, that lasted about two days. The problem recurred; I tried to follow your steps Varun, and ended up with a file on my computer. But it was a huge file, and every time I tried to get on-line to ask you how to post it here, my connection dropped out!

No worries, I soon solved the problem, with this blue wire here. I'll be upgrading this old laptop soon enough anyway. Mark this one SOLVED, I guess. Thanks!

---

