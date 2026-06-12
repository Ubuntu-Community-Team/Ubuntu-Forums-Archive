---
title: "Have No User Name"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Tedventure on 2009-06-17
I bought a laptop on eBay with dual boot.  Ubuntu came with no documentation or Username.  I haven't heard from seller yet.  I've never used Ubuntu or Linux before.  The only version id I've found is Gnome... I'll appreciate any ideas to get it to open so I can explore (reading the pocket guide now).  THANKS!!  Ted

---

### Post by Cheesemill on 2009-06-17
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by eagle416 on 2009-06-17
I just read that myself because I'm curious. It actually really scares me because I can see now how easy it is to break into a Ubuntu box/bypass security. What can I do to protect myself from that?

---

### Post by DGortze380 on 2009-06-17
> **eagle416 said:**
> I just read that myself because I'm curious. It actually really scares me because I can see now how easy it is to break into a Ubuntu box/bypass security. What can I do to protect myself from that?

Windows and OS X are just as easy to bypass.  ;)

You can password protect your recovery kernel through GRUB.

---

### Post by Cheesemill on 2009-06-18
> **DGortze380 said:**
> Windows and OS X are just as easy to bypass.  ;)

You can password protect your recovery kernel through GRUB.


Even this won't stop someone from booting with a LiveCD and recovering your data.
The best protection is to use full-disc encryption and keep your machine locked away but even this isn't fully secure.

Remember physical access = root access no matter what precautions you take.

See the following thread for more info:
[http://ubuntuforums.org/showthread.php?t=1188044](http://ubuntuforums.org/showthread.php?t=1188044)

---

### Post by tarps87 on 2009-06-18
> **Cheesemill said:**
> Even this won't stop someone from booting with a LiveCD and recovering your data.
The best protection is to use full-disc encryption and keep your machine locked away but even this isn't fully secure.

Remember physical access = root access no matter what precautions you take.

See the following thread for more info:
[http://ubuntuforums.org/showthread.php?t=1188044](http://ubuntuforums.org/showthread.php?t=1188044)

Although not a 100% fully secure solution you can password protect the grub menu or just remove the recovery entry form the list, then disable booting from removable media or over a network (In other words only allow it to boot from the hard drive with grub installed) now password protect you bios. This password can be reset by letting the motherboards battery run flat(This will take a few years and the computer will have to be unplugged for this length of time) or you can unplug the computer and remove the battery, to stop this buy a case with a hole for a padlock (an actual padlock not one of those laptop things). After all this the only way in is with an axe or other cutting tool (not including any holes in programs), so it should be enough to deter all but your most serious stalker :)
Really this amount for precautions are only needed when the computer will be in a public place i.e. computers in an internet cafe

---

