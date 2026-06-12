---
title: "machine wont boot - only get just past ubuntu progress bar"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by capnthommo on 2009-04-23
hi everybody.  when i try to boot i get just past the ubuntu progress bar and then i get some random colours at the top area of the screen and it freezes at that.  i dont even get as far as the login screen.  please tell me i dont have to reinstall jaunty cos i was just about to backup and - well - y'know.
last night i added some Ati/xorg (ithink) drivers from synaptic and all seemed ok but maybe there is now a conflict somewhere.  i would just like to get to a stage where i can log on and remove what i added.  i don't think (hope) that there is anything more serious wrong - just need to get logged on can anybody help?

Course, i would choose release day to have a problem wouldn't i - that's me all over - timing!
cheers
nigel

---

### Post by Hemmer on 2009-04-23
I have had similar problems with my ATI Radeon Xpress 200M which I managed to resolve by purging the fglrx drivers:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

The driver I'm currently using in my /etc/X11/xorg.conf is "ati". To get logged in as root, choose Recovery Mode option while booting (assuming your using grub), then edit away!

---

### Post by capnthommo on 2009-04-23
Thanks Hemmer
All ok now.  thanks for the link - printed and saved in case!
boots up now - we'll see how it continues.
cheers
nigel

---

### Post by Mortus Pryde on 2009-04-23
One newbie to another, with ATI cards be careful of the restricted/propriatary drivers. As of 9.04 the Catalyst 9.3 driver is no longer supported and the Catalyst 9.4 and Mesa drivers have dumped a bunch of cards from the support.

My ThinkPad in my sig uses a Radeon Mobility 9600 rv340 M10 that is no longer supported by Catalyst and Mesa. I have to look into tweaking the ATI/Radeon opensourse drivers.

---

