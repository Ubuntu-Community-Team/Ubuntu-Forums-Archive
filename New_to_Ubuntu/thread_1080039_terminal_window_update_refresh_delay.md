---
title: "terminal window update refresh delay"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by plasm980 on 2009-02-25
Sometimes (up to 10% of the time) when I enter a command into a terminal (such as ls), the terminal window is not refreshed with the new contents until either:

1) I press the enter key again
2) I click inside the window
3) I resize the window

While in the "limbo" state (command has executed, but terminal window hasn't updated to show new contents), the cursor has moved to the position in the window where it should be with the new contents.  Usually, none of the text is updated, though occasionally the limbo state will feature areas that are "torn" (as if some subareas of the terminal window have been updated).

From the symptoms, my first guess is that it's either X or compiz.  Any ideas on how to fix it?

Thanks!

My system:
HP dv5t
NVIDIA 9600M GT
Ubuntu 8.10 64-bit
GNOME 2.24.1
compiz 0.7.8

---

### Post by Xiong Chiamiov on 2009-02-27
See if the problem persists while using a different terminal emulator (for instance, konsole or xfce-terminal - I'm not quite sure on the names).

---

### Post by plasm980 on 2009-03-02
> **Xiong Chiamiov said:**
> See if the problem persists while using a different terminal emulator (for instance, konsole or xfce-terminal - I'm not quite sure on the names).

Thanks, it's much better now, but I still get the weird refresh delay every once in a while (maybe only 1% of the time).  Has no one else seen this problem before?

---

### Post by augustsaber on 2009-04-03
because 8.10 uses newer X.org codes, and that has some conflicts with NV's official linux driver. Try to use open source NV driver which are slower at 3D acceleration or, use other terminal emulators.

---

