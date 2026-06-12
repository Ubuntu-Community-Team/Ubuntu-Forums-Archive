---
title: "How do I install a driver for an Intel X3100 graphics accelerator"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-04
Hi
How do I install a driver for an Intel X3100 graphics accelerator.
I want to get DVDs to work and it seems i need to have a driver installed

---

### Post by Michael.Godawski on 2008-12-04
First go to System> Administration > Hardware Drivers and check if there is a option to activate the graphical drivers for your card.

---

### Post by Falc7 on 2008-12-04
That section is completely bare, and it says there are no proprietory drivers in use.

---

### Post by Michael.Godawski on 2008-12-04
Found this; perhaps it fits your needs:

[https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel](https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel)

---

### Post by Falc7 on 2008-12-04
Okay done that, although i still seem to be unable to get DVDs to work (which is what i am really looking for atm)

---

### Post by Tom--d on 2008-12-04
The intel driver is enabled by default. Don't worry about drivers.

DVD playback is totaly different.

A DVD from the shop (like a film) is encrypted. You need a decrypter to play it. Install libdvdcss2 here : [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb) 
Double click it.

Then install VLC player for DVD playback.

---

### Post by Falc7 on 2008-12-04
Yep, i have already installed that, here is the other thread i created, in which i was advised to make this one:
[http://ubuntuforums.org/showthread.php?t=1000264](http://ubuntuforums.org/showthread.php?t=1000264)
The DVD title screen plays fine, but when i select the movie, there are dynamic grey squares all over the vlc window

---

### Post by Tom--d on 2008-12-04
> **Falc7 said:**
> Yep, i have already installed that, here is the other thread i created, in which i was advised to make this one:
[http://ubuntuforums.org/showthread.php?t=1000264](http://ubuntuforums.org/showthread.php?t=1000264)
The DVD title screen plays fine, but when i select the movie, there are dynamic grey squares all over the vlc window

In VLC, make the Video output to 'noXV' or OpenGL.

---

### Post by karlmp on 2008-12-04
[http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

---

### Post by mgk57 on 2008-12-04
> **karlmp said:**
> [http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

Thanks for posting this link, I was looking for the same info on how to install a driver for the Intel X3100. Cheers!:D







Tasty [Food Hampers]("http://www.thehamperandgiftpeople.co.uk")
[Thorpe Cottage Country Guest House ]("http://www.thorpe-cottage.co.uk")- Dovedale

---

### Post by Falc7 on 2008-12-04
@mgk, after you followed that info, were you able to get DVDs to work?

---

