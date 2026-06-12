---
title: "random freezing?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by krupintupple on 2010-03-21
hey all,

my problem is that my machine randomly freezes and i've no real way to determine why this is happening. let me restate that, i don't know how, nor which logs to check to see why this is happening. some background: the ram doesn't shoot up, and the fans do not speed up, in fact, it just stops dead; this forces me to reboot via holding the power down.

i hope this helps, but my system is an acer AST180 (Athlon 64x2 Dual Core 3600+), 3GB DDR2, and the NVIDIA accelerated graphics driver (v195). i've been using it for about a year and have had no real snags. this is the first.

if anyone would care to lend a hand, i'd be very greatful!

---

### Post by r-senior on 2010-03-21
A freeze like that may not show anything up in the logs. Random freezes are often hardware issues but not necessarily so.

A live CD has a memory test menu option which would be worth a try. Are you overclocking the processor at all? Is the CPU fan working? Build up of dust inside the case? Vents blocked?

Is it a dual boot? Does the other OS work ok?

---

### Post by CiaoCiao on 2010-03-21
I've had several incidents like this over the years.  I am still using the same P4 I bought 8 years ago... :(

After much headaches and reading the internet, the first real problem ending up being a dying video card fan.  Fixed the fan, freezing problems went away.

My most recent problem turns out to be an overheated CPU.  the cooling fan bracket that the heatsink clips onto was broken.  Had a poor contact between the CPU and the heatsink.

Monitor your temperatures and physically inspect the fans, ensure everything is clean and working.  If a fan is noisy, just replace it.

Good luck, it can be a long road ....

---

### Post by krupintupple on 2010-03-27
thanks for both of your suggestions. i probably should mention this, but it is a dual-boot xp machine, and as much as i hate to say it, there's been no problems within windows. i'm not overclocking, or have made any modifications to the hardware - besides the dual-booting, which is pretty minor anyhow. 

it's frustrating, because this seems to only happen while i'm writing my term final!! i usually have openoffice running, and a few .pdfs in the background, using okular, and then firefox open, so i can check sources, or spelling, etc. so, it's not like i'm driving the RAM through the ceiling, or causing the CPU to melt from extreme use. i'm thinking that it might be a conflict, somehow, between okular or something, as last two times i merely clicked on the pdfs, it 'froze'.

also, let me explain the 'freezing' - the screen goes all blocky and random, mostly neutral colors, like an old-school NES game freezing, or screwing up. sounds weird, but maybe someone else had that happen too.

thanks for everyone's help!

---

### Post by the grey side on 2010-03-28
I've had somewhat similar problems, solved by installing a specific kernel:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1375948)

It is kernel 2.6.32.3 that worked for me, someone with the same problem had the issue reappear with later releases.
Have a look at these thread as well:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1331607](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1331607)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1309015](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1309015)

If this doesn't help, be sure that your hardware is working properly; you might want to run memtest86+ from GRUB for a couple of passes (although you should detect no problems if XP works fine).

If everything else fails, revert to 9.04 or wait for 10.04. Hopefully the problem is limited to 9.10.

---

### Post by krupintupple on 2010-03-28
thanks grey side, i'll be sure to check that out.

however, i might still try researching some other options, as i've noticed that it seems to particularly come about whenever i'm doing something that interfaces with KDE (okular, amarok, etc.), so i'm looking into that as well. however, i've got the feeling that you're spot on with this.

---

### Post by krupintupple on 2010-03-30
so, i've been checking around the boards and it seems that my issues are somewhat similar to other people's - mysterious graphic crash/lockup when firefox (or in my case, something involving KDE) is called.

i'll keep everyone posted.

---

### Post by krupintupple on 2010-05-06
so, i've solved the issue, it would seem.

i decided to investigate my machine, and removed/rotated/reseated all of the RAM, and used some canned air to get rid of some dust bunnies. it's been a month and the "issue" has simply not returned, so i suppose that this issue could be solved? sorry that i couldn't be of more help in this whole scenario.

---

