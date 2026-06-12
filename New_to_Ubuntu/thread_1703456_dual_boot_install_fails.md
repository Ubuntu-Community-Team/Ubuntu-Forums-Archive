---
title: "dual boot install fails"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by cybermonkey on 2011-03-09
Somebody gave me a desktop pc with Vista, so I decided to try Ubuntu 10:10. I downloaded the desktop version and burned it to a cd. I first tried the "Try It Out" option of booting from the cd, and everything worked well. No problems with wireless, sound or anything.
That inspired me to install it as a dual boot, but it all works fine until the following message appears:

[drm: radeon_dvi_detect]  *ERROR* DVI-D-I: probed a moniter but no l invalid EDID

And then the install will go no further. The moniter worked fine when I was just trying it by booting from the CD, but doesn't seem to be recognized with the install.

I searched the forums before posting to see if this problem had already been solved, and came across an answer that suggested pressing the esc button at the first purple screen and choosing an option that would come up. Unfortunately, I pressed esc at every purple screen that arose from start and nothing happened. Also, I now can no longer find the post to see what options the person suggested to try.

I am completely new to linux and would appreciate any help I can get.
If it helps, this is my pc:

Compaq Presario sr2150nx, 3.33ghz, 512kb L2 cache,533mhz frontside bus,
ATI RADEON XPRESS 1100 Chipset
1.5g PC2-4200 DDR2 SDRAM memory

Thank you for any help ypu can give.
I really want to try Ubuntu!

---

### Post by col48 on 2011-03-09
This post doesn't deal with the issue (sorry!)
but *_maybe_* the thread you saw was this one:

[http://ubuntuforums.org/showthread.php?t=1479411](http://ubuntuforums.org/showthread.php?t=1479411)

---

### Post by cybermonkey on 2011-03-09
Thanks, but that link seems to refer to someone who actually did get ubuntu installed and then had problems.
I was unable to finish my install because of it not being able to recognize a moniter.
. . . even though it all worked good just booting from the cd.

I really want to dualboot and work with it for a week or so, because I am seriously considering ditching vista altogether for this.

Why is the moniter there when booting from the cd and then not there when I try to install?

---

### Post by oldfred on 2011-03-09
It is press any key at the beginning when the figure & keyboard are shown. then press f6 for options.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

I have nVidia and have had to use nomodeset, both for install and first boot since 10.04. Also try generic if Radeon setting does not work.

---

### Post by cybermonkey on 2011-03-09
:p  Thank you! When I pressed f6 for options, there was a list with Nomodeset on it. When I used the arrow keys to scroll down to it an "X" appeared beside it and that was all I had to do.
I consider myself very fortunate that it was that easy because being new to linux all of that code on the pages you referred me to scared me silly!

I now have Vista and Ubuntu and look forward to becoming familiar with Ubuntu. As soon as I am, out goes Vista!

---

