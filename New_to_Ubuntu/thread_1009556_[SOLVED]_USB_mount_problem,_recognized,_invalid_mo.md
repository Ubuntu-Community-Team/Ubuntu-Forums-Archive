---
title: "[SOLVED] USB mount problem, recognized, invalid mount option"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by ThailandTom on 2008-12-12
I have read about this, but have lost the posts and cannot find, again. (maybe reading too much - am now tagging helpful posts.) 

I installed 8.04 using a USB stick. Install is fine, except:

installing with a USB drive does something funny to fstab (I don't know fstab very much - newbie.) Confuses usb for optical, or something...

"funny" - allows recognition of external usb drives but does not allow mounting, does not auto mount, "cannot mount volume"

I can force a mount, (but have lost that code/thread, too...) - clunky to do a terminal line to mount / unmount each session.

There is one line of code somewhere that can be commented out. Simply place a # at the start of the line. Lost that thread, too. Thought I had tagged, alas..

I promise to tag all helpful threads, so I don't have to post like this, anymore, but thank you for advice and pointing me in the correct direction.

---

### Post by ThailandTom on 2008-12-12
SOLVED: (google works well, too)

So excited to get going with Ubuntu, forgot to do the last bit of the install via usb instructions

[https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)

Look towards the bottom, and follow directions....

After Installing

After finishing the installation, edit /etc/fstab and make sure that /media/cdrom0 points to the CD drive and not to the USB stick. If you don't, you might get this error when trying to mount a USB stick: "Cannot mount volume. Invalid mount option when attempting to mount the volume." This is because the installer believes it is installing from a CD drive (bug 150872)

---

### Post by mc4man on 2008-12-12
```
cat /etc/fstab
```
if you want to take a look at your fstab (where the problem probably is

or 

```
 gksu gedit /etc/fstab
```

to edit it (commenting out the line your usb drive is on (or just delete the line

---

