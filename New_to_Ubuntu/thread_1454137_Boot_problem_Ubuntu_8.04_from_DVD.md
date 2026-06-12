---
title: "Boot problem Ubuntu 8.04 from DVD"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by michael__p on 2010-04-14
Hi everyone,
I created a Bio-Linux DVD ([http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0](http://nebc.nox.ac.uk/tools/bio-linux/bio-linux-5.0)), which is -as far as I understand- a Ubuntu 8.04 with some additional programs. When I try to boot from the DVD (I tried to start it as a live DVD instead of installing it) on a Lenovo L510 laptop without operating system it goes trough the first steps (some lines of code, "Loading Linux Kernel", another bunch of code), but always stops at "*Starting Common Unix Printing System: cupsd".
I have put the DVD first in the boot order and it also happens if I select manufacturer mode instead of normal. The DVD works on other computers and I can run a Knoppix live CD on this one.
Does anyone know what could be going wrong?
 
Thanks,
Michael

---

### Post by Jon Monreal on 2010-04-14
An [older thread]("http://ubuntuforums.org/showthread.php?t=279294") suggests that unplugging or deactivating your wireless card before startup might help.

If you can, try this and see if it works. If not, we can try something else.

---

### Post by michael__p on 2010-04-14
Thanks! Is it enough if I just turn the wireless off on the toggle switch? If so this doesn't make a difference, I get stuck at the same point. Actually I realized that during the previous steps I also got a failed on
"input: TPPS/2 IBM TrackPoints as /devices/platform/i8042/serio4/serio5/input/input9". Probably I also had that before and just missed it. 
Do you have any other suggestions?
Thanks, Michael

---

### Post by Jon Monreal on 2010-04-14
Yep, that was sufficient.

Do you have a copy of the vanilla Live CD that you could try?

---

### Post by michael__p on 2010-04-14
No, where do I get that from?

---

### Post by Jon Monreal on 2010-04-14
You would have to [download it from Ubuntu.com]("http://www.ubuntu.com/getubuntu/download") or [request a CD]("https://shipit.ubuntu.com/") from ShipIt, but that takes resources that you might not be willing to expend (mainly time). The reason I was wondering was to see if the standard distribution would work.

One thing to try now is (assuming Bio-Linux hasn't modified things too much), when you get to the screen where it asks you what you want to do, press F6 and modify the options by adding "apic=off" and "acpi=off", both minus the quotes, at the end of the line, and proceed from there.

---

### Post by michael__p on 2010-04-15
Unfortunately this also did not make a difference. I used Ubuntu 9.10 now instead, which runs without problems. I guess I can live with that and just wait till they update Bio-Linux to a newer version. Just sad that I don't understand any of all this.. Thanks for your help!

---

### Post by Jon Monreal on 2010-04-15
It's no problem. If you would like to put a word in for me, I appreciate any [testimonials]("https://wiki.ubuntu.com/Jon%20Monreal") added to my wiki page.

The good news here is that you can install any of the Bio-Linux packages in Ubuntu! [This page]("http://envgen.nwl.ac.uk/tools/bio-linux/other-bl-docs/package-repository") explains how you can get all of the Bio-Linux packages and functionality in Ubuntu fairly easily.

---

