---
title: "Laptop's Volume Control Scroll Doesn't Work Properly"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by jfolta on 2009-06-16
I am using a Toshiba Satellite A 135-S4467 laptop. The physical volume control slider on the bottom of the laptop controls the volume of the headphones instead of the master volume. It worked properly on Windows. Please Help!! Thank you.!!

---

### Post by Mark Phelps on 2009-06-17
Laptop vendors generally use customized hardware and MS Windows always supplied the companion drivers for that hardware.  With any Linux distro, you can't use those drivers, so you're stuck with what the kernel detects and loads.

If you're using 9.04, there's every possibility the kernel simply isn't detecting the hardware.

To see if it is, open a terminal, type "xev", put the cursor inside the box, and manipulate the volume control.  If you see key events scrolling past in the larger terminal window, that's good.  If nothing happens in the larger terminal window, that means the kernel doesn't see that hardware -- and you're out of luck.

---

### Post by jfolta on 2009-06-17
when I change the volume the terminal screen goes to "key map notify event" and then nothing really changes. does that mean the kernel didn't detect my hardware??? But the volume scroll actually changes volume, but it changes the headphone volume instead of the master volume.

---

