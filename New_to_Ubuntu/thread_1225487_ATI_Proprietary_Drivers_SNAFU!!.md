---
title: "ATI Proprietary Drivers SNAFU!!"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by 0RB1TAL on 2009-07-28
So, I am fairly new to Ubuntu. Ive installed 9.04 on a box for streaming media to the tv. Been having a repeat issue that once the ATI binary X drivers (Radeon X1650) and the system reboots, something happens that I can only assume is some sort of driver corruption - after the initial Ubuntu splash screen, it will only display a RGB pixelated mess... and will not move past this... Ive tried getting it to boot in 'safe driver mode' etc, w/o success.
After formatting a couple times, I dl-ed the proprietary driver from ATI's site (Catalyst driver v. 9.3 x86). However, when I open Hardware Drivers, the menu displays "No proprietary drivers are in use on this system"... And just stares at me... No indication its running a search  - I walk away and come back 10 min later and still nada.
Kinda hitting a wall here - any help would be great!!

---

### Post by jimsheep on 2009-07-28
last i heard, 9.04 does not support proprietary drivers for the ATI Radeon series...i have an X800 that i'm stuck using the open source drivers in 8.10, because the proprietary drivers didn't work for it either.

suggestions:
-wait until ATI either releases the source for their drivers or creates a proper driver for Linux
-Buy an NVidia card.

---

### Post by philcamlin on 2009-07-28
> **jimsheep said:**
> last i heard, 9.04 does not support proprietary drivers for the ATI Radeon series...i have an X800 that i'm stuck using the open source drivers in 8.10, because the proprietary drivers didn't work for it either.

suggestions:
-wait until ATI either releases the source for their drivers or creates a proper driver for Linux
-Buy an NVidia card.

i wouldent rush out and by an nvidia card yet just wait a little longer and see what happens :popcorn:

---

### Post by 0RB1TAL on 2009-07-28
Ya, I went back and checked AMD's site and it seems I misread the fine print: "The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above."
Any thoughts on how I can get this to run... and be stable?... I tried the binary X drivers again, aaaaaand the attached img is what happened on reboot this time... 


Really dont want to go back to Vista, but Im a little outta my element here.[IMG]file:///C:/Users/Nexus/Desktop/IMG_0258.JPG[/IMG]

---

### Post by halitech on 2009-07-28
if you want to use the ATI drivers, install 8.04 instead of 9.04 where the drivers should work.

---

### Post by connorh123 on 2009-07-28
Hi.
I have an ATI Radeon 7500, and I've had some troubles with 9.04, not ATI itself. In 8.04, it worked great. However, I wasn't on 8.10 that long to come to a decision. But, the graphics don't look that bad on 9.04 for me.

---

### Post by halitech on 2009-07-28
> **connorh123 said:**
> Hi.
I have an ATI Radeon 7500, and I've had some troubles with 9.04, not ATI itself. In 8.04, it worked great. However, I wasn't on 8.10 that long to come to a decision. But, the graphics don't look that bad on 9.04 for me.

did you install the ATI driver or are you using the open source drivers?

---

### Post by 0RB1TAL on 2009-07-28
> **halitech said:**
> if you want to use the ATI drivers, install 8.04 instead of 9.04 where the drivers should work.

Guess Ill grab an .iso of an earlier distro and see if that works... Any reason I need 8.04 vs. 8.10?

---

### Post by connorh123 on 2009-07-28
I'm using an IBM Laptop. So it was installed.

---

### Post by halitech on 2009-07-28
I suggested 8.04 as it is an LTS release and you won't need to worry about upgrading the video card for 3 years while it is supported.

---

### Post by halitech on 2009-07-28
> **connorh123 said:**
> I'm using an IBM Laptop. So it was installed.

what was installed? the card or the driver? *lost*

---

### Post by connorh123 on 2009-07-28
The driver.

---

### Post by halitech on 2009-07-28
> **connorh123 said:**
> The driver.

so you have the 9.3 ATI catalyst driver installed for an unsupported card? how did you manage that?

---

### Post by 0RB1TAL on 2009-07-28
Great... 8.04 it is then...

Thanks!!

---

