---
title: "Hiding unwanted updates"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by abo999 on 2008-12-16
Next question...

When I first installed Ubuntu I updated it fully with the update manager and then installed the driver for my Radeon HD2400, which caused me no end of display problems... In the end I tore the thing down and did a re-install. No biggie since I'd not done anything with the machine other than the initial install.

To cut a long story short I believe I've pinned this down to the updates:

xserver-xorg-video-xxx

Is it possible to remove these from the update manager so that I don't:

1. keep getting the reminder to update and
2. accidentally update with them!

---

### Post by Locke_99GS on 2008-12-16
Find the package in synaptic (or aptitude) and force it to remain at whatever version you want it to stay at.

---

### Post by 2hot6ft2 on 2008-12-16
System>Administration>Synaptic Package Manager search for the packages you no longer want to update , select them one at a time and click on Package then Lock Version that's it. It wont try to update them anymore.

---

### Post by Michael.Godawski on 2008-12-16
The same but with a screenshot :)
[https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages](https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages)

---

