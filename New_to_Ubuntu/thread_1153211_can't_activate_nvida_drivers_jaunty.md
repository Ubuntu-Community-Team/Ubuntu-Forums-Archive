---
title: "can't activate nvida drivers jaunty"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-05-08
i tried doing it through hardware drivers but thats not working then i tried installing from a downloaded drvier from there site but it says it appears i'm running a x server but i stopped gdm can someone please help me out this is annoying

---

### Post by ubuwatson on 2009-05-08
When I first installed Jaunty, the drivers were not available, it wasn't until the second or third reboot that restricted drivers showed up on the panel.  You might need to run update manager once or twice before they show - give it chance it does work.

I had the same problem installing nvidia drivers manually, it kept saying that the x-server was still running, there is a trick to get it to install - if you have no luck getting the restricted drivers to show I will help you out - but try to get the restricted drivers first if you can.

---

### Post by mamamia88 on 2009-05-08
ok i will try update manager and then try again but in case that doesn't work i have downloaded the driver from nvidia website i read how to install online but for some reason it says im running an x server even though i issued the command to stop gdm.  is there a way to completely exit x so i can install it already?

---

### Post by Chemical Imbalance on 2009-05-08
> **mamamia88 said:**
> ok i will try update manager and then try again but in case that doesn't work i have downloaded the driver from nvidia website i read how to install online but for some reason it says im running an x server even though i issued the command to stop gdm.  is there a way to completely exit x so i can install it already?

Are you at a console prompt or in GNOME?

You have to press ctrl+alt+F1 to drop to your first virtual console.

Then you have to kill the xserver and finally install the driver.

---

### Post by mamamia88 on 2009-05-08
> **Chemical Imbalance said:**
> Are you at a console prompt or in GNOME?

You have to press ctrl+alt+F1 to drop to your first virtual console.

Then you have to kill the xserver and finally install the driver.

ok i was doing cntrl-alt-f3 like someone suggested in another thread i'll try that  nope that didn't work what could be going on?

---

### Post by Chemical Imbalance on 2009-05-08
> **mamamia88 said:**
> ok i was doing cntrl-alt-f3 like someone suggested in another thread i'll try that

f3 is fine.  f1 is your first console, f3 is your third virtual console and so on.

---

