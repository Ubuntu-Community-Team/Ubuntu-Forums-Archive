---
title: "Live USB standby problem"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by shalfurn on 2010-11-14
Hi!

I'm trying to test out the standby part of UNR, and I haven't installed it to my netbook yet; UNR runs off of my flash drive.

But every time I select "Standby" from the menu choices, the screen goes black and I get:
"getpwuid_r(): failed due to unknown user id (0) ".
Then my netbook just dies (immediately shuts off), as if I had held down the power button. Trying to turn it on again shows no signs of standby.

My main question is, why does this error occur? Or am I trying to do something not possible (standby while running off the live usb)? Do I need to install it with a suitable swap size in order for this to work?

My netbook has had this problem before, it can hibernate but not standby to ram (for some odd reason that the hardware does not seem to be capable of explaining), and I am afraid this problem just shows that I can't solve it through software :(.

[SIZE="1"]Un-related to any ubuntu problems, I was thinking I needed to reflash my netbook's bios to the version previous....[/SIZE]

Any help would be great!

---

### Post by uRock on 2010-11-14
The live image does not have the ability to go into standby. What model netbook do you have?

---

### Post by shalfurn on 2010-11-14
I knew I was doing something wrong.
Would it have given me the same error? Or is that my netbook's fault?
I'm running ubuntu on a Msi Wind u100.
Thanks!

---

### Post by uRock on 2010-11-14
I have only attempted to use Suspend a couple of times and it failed. I have never tried to hibernate with the live image(CD nor USB)

---

### Post by shalfurn on 2010-11-14
That is dis-hearting news...as a student I find it vital.

I am interested in trying out standby/hibernation after installing it, but [http://wwww.ubuntuforums.org/showthread.php?t=1601203]("this thread") has frightened and confused me. I'll just try it anyway.

---

