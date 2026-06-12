---
title: "ubuntu 10.04 livecd will not boot on desktop pc"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by McToast900 on 2010-09-06
First of all i should mention that this is my first attempt at linux so im a complete novice.  I've seen quite a few posts about this, but none of the solutions seem to be working,  but here's the problem and what ive done about it so far:

[B]My hardware

[/B]GeForce 8800 GTS  GFXcard
Intel core 2 duo 3.00 GHz processor
NVidia 650i chipset
2GB 600 MHz RAM

[B]What actually happens

[/B]the cd seems to start loading. but the mouse will appear and the loading screen will remain and i can't do anything (accept move the cursor round the screen :P) if i press f6 on boot it appears to be stopping after testing sensors? (whatever that means)

[B]The CD itself

[/B]i downloaded the .iso and put it through md5sum to make sure its working properly.  i then burned it and tried it out.  no luck.  i think that the CD itself is actually fine. (i'm posting this on a laptop using the livecd ive made.)

[B]Things I've tried

[/B]
[LIST]
[*]Making a new CD although as explained above i dont think this is the issue
[*]entering the following into the GRUB boot entry seperately (found a similar thread which suggested these):
[LIST]
[*]xforcevesa
[*]acpi=off
[*]noapic
[*]i915.modeset=0
[*]i915.modeset=1
[*]nomodeset
[*]removing 'splash' and 'quiet'
[/LIST]
[/LIST]
Any help would be much appreciated! as i said complete beginner here so some of this explanation may not make any sense.

---

### Post by yeats on 2010-09-06
Assuming you've seen this, but posting it anyway:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

This same thing happened to me when trying to install on a recent model HP laptop.  

The other thing you can do is burn an alternate CD, which does not rely on the X server to install:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by Jazzy_Jeff on 2010-09-06
If you are sure you want to install I would recommend the alternate install cd as well. I too have problems using Live CD's on my computer. The alternate install cd always works.

---

### Post by cake nom nom on 2010-09-07
you could also try using 32 bit if you did 64bit or 64 if you did 32 

try using Ubuntu 9.10 also its much more stable anyway & most people stay one distro behind I hear

---

