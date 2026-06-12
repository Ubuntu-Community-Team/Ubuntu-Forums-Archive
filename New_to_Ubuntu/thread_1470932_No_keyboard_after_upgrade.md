---
title: "No keyboard after upgrade"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by tennesseebrewer on 2010-05-03
I have VMWare player, and I have upgrade Ubuntu to 10.04 and now my keyboard does not work. It works fine in all other environments, but will not register. I can't even log in!

Anyways... here are the specs of my computer:
Dell XPS 400 2004 model
Intel Pentium D processor
Generic Dell USB keyboard

The mouse works fine, but like I said, no keyboard controls.

Any help would be greatly appreciated... I really want to see the new Lucid Lynx!

Also, a side note, will Gwibber run on Karmic? Just in case I can't upgrade... I would like to try using that program as well. Thanks!

---

### Post by mikmitch on 2010-05-03
Same issue with two different machines running VMware.  Thought I'd join the forum to share my solution :) Here is my simple fix:

Enable on screen keyboard with the Universal Access preferences (click the stick figure inscribed in a circle on the bottom right of the login screen) note: may require reboot for keyboard option to show up.

Log in as normal

Strangely enough, the keyboard seemed to work fine afterward... not sure what causes the error.  

If issue persists, try :  sudo dpkg-reconfigure console-setup

---

### Post by tennesseebrewer on 2010-05-05
Thanks! It worked... now, it won't see my internet connection (wired) through VMWare.

---

