---
title: "Ubuntu doesn't like new video card"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Sea Bisquick on 2009-11-09
Hi.

I installed 9.04, was working fine, upgraded to 9.10, which also seemed to be working fine. I put in a new video card, and Ubuntu works no more.

I had an nVidia 7800 gs, and upgraded to an HIS (ATI) Radeon 4670 agp card. The problems start after selecting the boot option. The Ubuntu boot logo is a bunch of weird colors, and not the right size. I tried booting from a 9.04 live CD, with the same result. I'm guessing the video card and Ubuntu are not getting along. Any suggestions as to how to get Ubuntu to work with this card?

System:
Asus P4P 800 SE mobo w/ P4 3.4 EE
HIS Radeon 4670 AGP 1GB video
Audigy 2ZS platinum sound card

---

### Post by konqueror7 on 2009-11-09
try fixing your xorg,,,on the GRUB menu, select the one with the 'recovery' option, it will load an interface and select fix xorg or x,,,if i remember correctly its 'xfix',,,try that and reboot, then install a updated driver...

---

### Post by realzippy on 2009-11-09
So you try to run your new ATIcard with your nvidia-driver!?
I do not know if the new ATI fglrx driver is the right one for your card.
If so,hit ALT+ctrl+F2 after attempting to start X to open terminal and try:
**sudo apt-get install fglrx** and reboot.You can also boot in recovery mode.

---

### Post by realzippy on 2009-11-09
> **konqueror7 said:**
> try fixing your xorg,,,on the GRUB menu, select the one with the 'recovery' option, it will load an interface and select fix xorg or x,,,if i remember correctly its 'xfix',,,try that and reboot, then install a updated driver...


..think you will only need to change the line "driver" from **nvidia** to **vesa** and reboot,then install fglrx. (or radeon)

---

### Post by konqueror7 on 2009-11-09
> **realzippy said:**
> ..think you will only need to change the line "driver" from **nvidia** to **vesa** and reboot,then install fglrx. (or radeon)

fixing the xorg would just restore the generic xorg.conf, so atleast he could boot inside, then install the proper driver, but it could work with changing the driver, haven't tested switching video cards,,,haha...

---

### Post by LowSky on 2009-11-09
boot to recovery mode, choose xfix, then install new driver when you reboot

---

### Post by QIII on 2009-11-09
Check your new card for compatibility with ATI's Catalyst 9.10 and driver.

It was made available specifically to Canonical for inclusion in Karmic (although I hear it is generally available now.)

It's in the repos, so you should be able to get the newest driver without much ado.

(I'm using it on my machine with ATI graphics and it is great.)

---

### Post by Sea Bisquick on 2009-11-12
Thanks for all the advice. Here's where I'm at:

I can install 9.04, but afterwards it won't boot. I can boot into recovery mode and use shell commands normally. I tried fixing x from the recovery mode to no avail. I then downloaded and installed the latest proprietary driver from the ATI site and installed it as per the posted instructions, which still did not work.

I know that 9.10 includes the latest drivers from ATI, but that disk doesn't even make it to the normal installation screens, and running from the live CD doesn't work either.

This video card (it's an _AGP_ Radeon 4670 from HIS) required a special hotfix to be able to install the latest Catalyst Control Center in *Windows*, so I'm not hopeful for its support in Linux. At this point I'd be happy to be able to just run a Linux distro, whether or not the features of the card are useable.

Is there something I'm missing? :confused:

Thanks again.

---

