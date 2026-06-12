---
title: "CD Tray"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by physwizz on 2009-05-10
How can I stop the DVD tray from going back as soon as I open it?:(

---

### Post by Didius Falco on 2009-05-10
Are you using Intrepid 8.10? That's a confirmed bug, according to the Release notes:

> **CD eject problems**

  After ejecting a CD tray containing a disc, the tray will be immediately retracted, making it difficult to remove the disc ([bug 283316]("https://launchpad.net/bugs/283316")). This can be worked around by pressing the eject button again before the disc is fully mounted, after which it will stay open. We expect to fix this in a post-release update.  
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Reading through the bug report, I found this:

           > I can confirm that with udev 124-8 from Intrepid I see the cdrom closing problem on eject; with udev 124-9 from intrepid-proposed I no longer see the problem. eject, eject -t, and eject -T work as expected, as well as ejecting other block devices.
 @Glenn Sullivan: when you say that all fixes do not work for you, does that include the udev package in intrepid-proposed?
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316)

In plain English, that means to go to **System/Administration/Software Sources**, go to the **Updates** tab and click the radio button for **Pre-Released Updates (Intrepid Proposed)** and then run **Update Manager**.

The update you are looking for specifically is **udev 124-9**. I'm still running an install of 8.10, so I'm going to reboot and try this out - I have the same problem.

I hope this helps...us both <G>

Regards,

Didius

On Edit:

It worked for me

---

### Post by physwizz on 2009-05-20
I solved the problem by going to update manager and installing all of the updates.:p

---

### Post by glotz on 2009-05-20
:)

---

