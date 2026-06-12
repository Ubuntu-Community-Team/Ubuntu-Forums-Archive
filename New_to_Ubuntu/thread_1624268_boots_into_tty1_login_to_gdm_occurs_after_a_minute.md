---
title: "boots into tty1: login to gdm occurs after a minute or two"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by solar-ch on 2010-11-17
I've read other posts (from 9.10 onwards) where the problem of delayed startup is attributed to corrupted xorg and gdm, or indeed incorrectly installed nvidia drivers. I myself am not sure why this problem occurs in my case - I have a Xeon X5550 with 16GB and a nvidia quadro fx 3800 - and it doesn't matter whether I install 10.04 or 10.10 (64bit), it happens either way. I can't find anything in the logs (:0-greeter or boot or syslog etc.) that might indicate a stalling or crashing of service. Alas, my ubuntu diagnostic potential is quite limited.

I would appreciate any clear ideas people might have regarding what I can look for or even just where I should start.

Cheers,
Will.

---

### Post by solar-ch on 2010-11-18
**PS1.** This kinda thing could be what I'm suffering from -> [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/625239](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/625239)

**PS2.** I'm using X-updates pda (driver 260.19.21) and have purged xserver-xorg-video-nouveau beforehand...

---

### Post by matt_symes on 2010-11-18
Hi

You could try boot charting and try to see where it is stalling.

[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Kind regards

---

### Post by bcfieldi on 2011-01-10
This post is a little old but I figured I would tell how I fixed this issue myself. May not work for everyone but might as well put it up for someone's reference.

There are a number of solutions out there that call for altering your Xorg file or Grub, all that I did was ```
sudo update-grub
``` worked like a charm, automatically logs into tty7 now and no delay in start-up anymore.

---

