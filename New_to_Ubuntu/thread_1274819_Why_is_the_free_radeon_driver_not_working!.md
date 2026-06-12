---
title: "Why is the free radeon driver not working!?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-25
Hi guys,

In an effort to get a decent usable dual screen setup I have decided to ditch the Catalyst fglrx drivers and try out the free ones with xrandr 1.2.... so I uninstalled the flgrx drivers and reconfigured my xorg.conf file, rebooted and now the laptop won't boot using the free drivers. It gets past the splash screen and then there are little specs of green at the top of the screen but doesn't get to the login window.

I've tried everything, completely removing the fglrx drivers, adding "radeon" and "ati" to the xorg.conf file under Device driver, purged all the fglrx packages (apart from the free drivers one of course) but I can't get it to work for the life of me.

Please help!

---

### Post by SuicideSmurf on 2009-09-25
> **humphreybc said:**
> Hi guys,

In an effort to get a decent usable dual screen setup I have decided to ditch the Catalyst fglrx drivers and try out the free ones with xrandr 1.2.... so I uninstalled the flgrx drivers and reconfigured my xorg.conf file, rebooted and now the laptop won't boot using the free drivers. It gets past the splash screen and then there are little specs of green at the top of the screen but doesn't get to the login window.

I've tried everything, completely removing the fglrx drivers, adding "radeon" and "ati" to the xorg.conf file under Device driver, purged all the fglrx packages (apart from the free drivers one of course) but I can't get it to work for the life of me.

Please help!

Have you tried using recovery mode to reset xorf.conf so that you can maybe get back to your desktop?

---

### Post by humphreybc on 2009-09-25
> **SuicideSmurf said:**
> Have you tried using recovery mode to reset xorf.conf so that you can maybe get back to your desktop?

Yes I have done that. I've run dpkg-reconfigure -phigh xserver-xorg which re-writes a new xorg.conf and it still does not work.

I'm in the LiveCD at the moment which runs off the free drivers that I want to use, and the dual monitor desktop runs great using these drivers, it even maximises to either screen instead of both screens which is why i'm changing!!

Now... just to get back into MY Ubuntu with the free drivers... anyone?

---

### Post by SuicideSmurf on 2009-09-25
> **humphreybc said:**
> Yes I have done that. I've run dpkg-reconfigure -phigh xserver-xorg which re-writes a new xorg.conf and it still does not work.

I'm in the LiveCD at the moment which runs off the free drivers that I want to use, and the dual monitor desktop runs great using these drivers, it even maximises to either screen instead of both screens which is why i'm changing!!

Now... just to get back into MY Ubuntu with the free drivers... anyone?

Hmmmmm, may I suggest installing the Ubuntu 9.10 Alpha 6? It it already surprisingly stable, and the opensource ATi drivers are more advanced.

---

### Post by humphreybc on 2009-09-25
I'd prefer not to upgrade to Alpha releases... had some problems in the past with Betas and even Release Candidates. And I'm not really keen on a fresh install as our internet is so slow it would not be able to download all the software that I'd have to re-install. My system is fine, it's just I need to get these open source drivers working and then all will be dandy.

PS. Does anyone know why I can't chroot to my install directory on the live CD?
I get this when I try:

```

ubuntu@ubuntu:~$ sudo chroot /media/disk
chroot: cannot run command `/bin/bash': Exec format error

```

I am using a 32 bit LiveCD on a 64 bit system... so that could be why. Or the fact that my hard drives are formatted to ext4 instead of ext3... but I'm pretty sure I have chroot successfully before.

It'd be good if I could chroot to my directory because then I can go about removing all traces of fglrx drivers from the LiveCD.

---

### Post by SuicideSmurf on 2009-09-25
> **humphreybc said:**
> I'd prefer not to upgrade to Alpha releases... had some problems in the past with Betas and even Release Candidates. And I'm not really keen on a fresh install as our internet is so slow it would not be able to download all the software that I'd have to re-install. My system is fine, it's just I need to get these open source drivers working and then all will be dandy.

PS. Does anyone know why I can't chroot to my install directory on the live CD?
I get this when I try:

```

ubuntu@ubuntu:~$ sudo chroot /media/disk
chroot: cannot run command `/bin/bash': Exec format error

```I am using a 32 bit LiveCD on a 64 bit system... so that could be why. Or the fact that my hard drives are formatted to ext4 instead of ext3... but I'm pretty sure I have chroot successfully before.

It'd be good if I could chroot to my directory because then I can go about removing all traces of fglrx drivers from the LiveCD.

Then I'm sorry I don't know. I wish you luck :)

---

### Post by humphreybc on 2009-09-25
Ah I think I might just re-install Ubuntu 9.04.... it shouldn't take that long, I'll just go to the library tonight and download the programs I need. Grr... oh well... the dual screen goodness is worth it :P

24" full HD 1080P + Wharfedale Diamond 9.1 speakers = luxury for movies :P

---

### Post by humphreybc on 2009-09-25
I just re-installed Ubuntu on my system with ext4 as default and boy, a fresh install using ext4 with open source drivers, what a speed improvement!! It's so much quicker and feels so much more responsive.

How do I enable "normal" visual effects with the open source drivers? I'm pretty sure the open source drivers support 3D for my ATI HD2600?

---

