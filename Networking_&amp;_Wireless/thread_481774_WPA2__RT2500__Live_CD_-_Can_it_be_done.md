---
title: "WPA2 / RT2500 / Live CD - Can it be done?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by daniel_summers on 2007-06-22
I have a question.  (OK, that's obvious, huh?)  I'll start with my question, then give some background to help explain what I'm trying to do, if it's not clear from the question.

I have an Averatec 6240 laptop, with an AMD 64 chip and 1.5GB RAM, and an RALink RT2500 wireless card.  I know from reading the [sticky post]("http://ubuntuforums.org/showthread.php?t=318539") at the top of the forum that his technique specifically does not work with RALink cards.  Following [the link he suggests]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5") at the Serialmonkey forum, that describes an FC6 technique.  (Ndiswrapper is not an option...)  [Another post]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3931") on the Serialmonkey forum suggests using "rt2x00" if you need WPA2 support.  (It also states that RALink doesn't support it, but that's bull - if it's in the Windows driver, it could be in the Linux driver.  But I digress...)  I don't see that package anywhere in the repositories - ```
apt-get install rt2x00
``` says that the package cannot be found.

I'd really like to be able to make this thing connect up without installing it (the "why" is in the background below).  If it's possible to download a package on a USB stick, and modify the version off the live CD once it's loaded into memory, that would be absolutely great.  Does anyone here have experience with this particular set of hardware?

A little background...  I currently have another machine running Ubuntu Feisty, which I set up while my Windows Vista laptop was out of commission.  It had been a few years since I had run Linux, and I was **very** impressed with the way Ubuntu recognized the wireless card in that machine, and let me securely connect to my wireless network with it.  (It has problems occasionally, but that was one of the reasons my wife stopped using that computer when it had XP - it wouldn't stay connected to the network.)

Since I've gotten my laptop working again, I've found that it's 4 months from the release of Vista, and there still is not a video driver for my chipset (SiS M760).  The manufacturer doesn't talk to end users, and the laptop company doesn't even acknowledge this model number when discussing Vista, which is strange since it's specs are consistent with what Visa will support.  It's a "shared memory" chipset, though, so without a driver, the CPU is doing all the video work, and it can't benefit from the 128MB I currently have allocated for it.

Anyway, I really like Ubuntu.  I've run a couple of different flavors of Linux, and this is by far the best I've tried (knocking SimplyMEPIS off the top spot on my list).  I'd like to put Ubuntu on this laptop, but before, the wireless has been the hardest thing to get running.  It caused kernel panics under FC2, was flaky under White Box (RHEL clone), and "just never worked" under SimplyMEPIS.  Before I wipe and reload (which would be significant), I want to try to get the wireless working well by using the live CD.

Thanks!

---

### Post by cecilkorik on 2007-06-22
Doesn't look like it's possible with the LiveCD.

From the [rt2x00 download page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"), it seems they only have the new rt2x00 driver working with absolutely bleeding-edge kernels (2.6.22-rc1 and higher... 2.6.22 is still in the release candidate stage, not released yet)

So if the only driver that's going to work properly for you is the rt2x00 it looks like you'll have to either install your own kernel (I'm pretty sure you need a real installation to do that) or wait until the kernel on the LiveCD catches up.

Have you considered making a backup image of the whole drive before installing Ubuntu using something like [Partimage]("http://www.partimage.org/Main_Page") on the [System Rescue CD]("http://www.sysresccd.org/Main_Page") (not affiliated with Ubuntu, but handy to have around...)? If you do that, you can give Ubuntu a full try out and if it still doesn't work after a lot of hacking around, you can just put the old system back onto the drive with your backup image.

Edit: I looked a little bit closer and it seems like the rt2x00 driver is included with Feisty's 2.6.20 kernel image. If the LiveCD is using that kernel, it should already be installed, no package necessary. Try just doing:
modprobe rt2x00
From a terminal, see if that does anything useful for you.

---

### Post by daniel_summers on 2007-06-23
> **cecilkorik said:**
> 
Edit: I looked a little bit closer and it seems like the rt2x00 driver is included with Feisty's 2.6.20 kernel image. If the LiveCD is using that kernel, it should already be installed, no package necessary. Try just doing:
modprobe rt2x00
From a terminal, see if that does anything useful for you.

Thanks for that - I will, and let you know how it goes.  Thanks for the other suggestions as well - I'll certainly give them a shot if the modprobe doesn't work.  :)

---

### Post by daniel_summers on 2007-06-23
Well, I gave it a shot.
```
modprobe -r rt2500
modprobe rt2x00lib

```worked, but I couldn't get it to recognize the RT2500 card in my laptop.

I also followed the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=434952") (about setting up RALink's RUtil utility), but I never could get the right combination.  The "rutilt" program would only run once, immediately after "modprobe rt2500".  Any other time, it simply came back "Segmentation fault (core dumped)".  The biggest problem was that any selection I made in the utility, it prompted me for the root password.  I tried everything I could think of ("ubuntu", the user; "root"; blank; I even tried setting a password using "sudo passwd"), but I could not get it to do anything.

I've noticed that a lot of the "this doesn't support WPA" articles are from 2006 or earlier.  (I found one that said NetworkManager doesn't support WPA at all, especially with Atheros chipsets.  However, that's what I'm using on my other Ubuntu machine, and it worked out-of-the-box.)

I may give this a few months.  I might also go over to Serialmonkey's forum and see if I can find out anything.  This laptop is over 2 years old - not bleeding-edge by any stretch of the imagination.  Thanks for your advice.  :)

---

### Post by daniel_summers on 2007-07-05
Well, I'm typing this reply from my laptop with a fresh install of Ubuntu Feisty!  :)  Woo hoo!

(I discovered through the course of [conversing with some folks over on the rt2x00 forums ]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3984")that although my other Feisty box says I'm using WPA2, I'm actually using WPA with AES.  Once the latest version of RutilT came out, I gave it a shot, and it worked first time.  I'm even getting faster network speeds than I got with Vista!)

---

