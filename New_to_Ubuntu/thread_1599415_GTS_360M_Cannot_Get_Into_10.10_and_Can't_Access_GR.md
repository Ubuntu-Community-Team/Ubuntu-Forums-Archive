---
title: "GTS 360M Cannot Get Into 10.10 and Can't Access GRUB...?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by chazdraves on 2010-10-17
Greetings, all!

I've been using Ubuntu on and off for a couple years now and I've rarely had much of a problem (save wifi in ye olde days).

Recently, I bought a new laptop and there seems to be an issue with the GTS 360M and 10.10 as I've seen other posts like this. Unfortunately, I still haven't found how to fully fix this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178)

I get images almost identical ---^

[http://ubuntuforums.org/showthread.php?p=9953273](http://ubuntuforums.org/showthread.php?p=9953273)

This worked for installing 10.10 ---^

Now, however, I cannot get into 10.10. When I startup there is no boot loader for me to select "Safe Graphics Mode" and I cannot find a button to access GRUB/or anything. No matter what I mash, Ubuntu continues to load and I end up at the "maze-like image".

I've tried two different downloads and two different installs now with the same result. If someone can tell me how to install the nvidia drivers via the boot disc to my primary install? Or if someone can tell me how to edit something using the boot disc? I'm at a loss. If I could get into Safe Graphics Mode I could install the nVidia drivers and be rockin' but the usual GRUB screen with:

*Insert Current Kernel Here*
*Insert Current Kernel Here* (Recovery Mode)

Doesn't come up...

Thanks in advance!
- Chaz

---

### Post by sandyd on 2010-10-17
> **chazdraves said:**
> Greetings, all!

I've been using Ubuntu on and off for a couple years now and I've rarely had much of a problem (save wifi in ye olde days).

Recently, I bought a new laptop and there seems to be an issue with the GTS 360M and 10.10 as I've seen other posts like this. Unfortunately, I still haven't found how to fully fix this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178)

I get images almost identical ---^

[http://ubuntuforums.org/showthread.php?p=9953273](http://ubuntuforums.org/showthread.php?p=9953273)

This worked for installing 10.10 ---^

Now, however, I cannot get into 10.10. When I startup there is no boot loader for me to select "Safe Graphics Mode" and I cannot find a button to access GRUB/or anything. No matter what I mash, Ubuntu continues to load and I end up at the "maze-like image".

I've tried two different downloads and two different installs now with the same result. If someone can tell me how to install the nvidia drivers via the boot disc to my primary install? Or if someone can tell me how to edit something using the boot disc? I'm at a loss. If I could get into Safe Graphics Mode I could install the nVidia drivers and be rockin' but the usual GRUB screen with:

*Insert Current Kernel Here*
*Insert Current Kernel Here* (Recovery Mode)

Doesn't come up...

Thanks in advance!
- Chaz
keep on mashing escape to get to the grub menu
then on the *Insert Current Kernel Here*, press 'e'
at the end of the kernel line , with a space between and no quotes, put tin 'nomodeset'
press CTRL+X  to boot.

---

### Post by drs305 on 2010-10-17
The Grub 2 menu should display if you hold down the SHIFT key during boot. Once it does, you may see a recovery mode entry. You can also highlight an entry and press "e" to edit the entry; at that point you could add kernel options to the end of the linux line (such as "nomodeset").

---

### Post by chazdraves on 2010-10-17
> **drs305 said:**
> The Grub 2 menu should display if you hold down the SHIFT key during boot. Once it does, you may see a recovery mode entry. You can also highlight an entry and press "e" to edit the entry; at that point you could add kernel options to the end of the linux line (such as "nomodeset").

ESC did not work and only starts spamming ^[ ^[ ^[ across the screen.

Holding SHIFT, however, works the first time every time. I'm now in and installing the nVidia drivers.

I hope this can help anyone else having this problem. And thanks again!
- Chaz

---

### Post by aresthedog on 2010-11-30
Same problem :(
ASUS G51JX - nvidia GTS 360M
10.10 32 & 64

---

