---
title: "Appearance-Settings in Ubuntu?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Akatsuki26 on 2010-02-05
When I go onto the Appearance-Settings, I click on Visual Effects.

So there are three of them, the worse ones, the better ones, and the good ones.

So mine are set to the "worse" ones, but when I click on "good ones" then it says that's not possible?

Why?

(I'm running Ubuntu 9.10 Karmic Koala)

Thanks a lot!

---

### Post by baddnady23 on 2010-02-05
Your video card may not support the higher settings.  What kind of card to you have?

---

### Post by TBABill on 2010-02-05
When you install Ubuntu you are not using the proprietary driver for your video card until you enable it. Without it enabled you are using a generic 2D driver that will not support the effects. You need to enable the proprietary video card (nVidia, ATI, etc) driver and then increase your desktop effects settings.
 
I am not on my machine to be able to guide you to them, but do a quick search of the forums for how to enable the non free repositories. Once you do that you can go into Synaptic and download the driver for your card, if available. You'll also be able to download flash and other media capabilities that are not pre-installed in Ubuntu.

---

### Post by ssulaco on 2010-02-05
Go to System>Administration>Hardware Drivers and see if Ubuntu sees your card you will have to enable it
if its not there go to System>Admin>Software sources>Ubuntu software tab,and make sure "Proprietary drivers for devices (restricted)" is ticked also see if Main, Universe and Multiverse are ticked.

---

