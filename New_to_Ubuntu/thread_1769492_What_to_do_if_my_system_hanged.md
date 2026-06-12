---
title: "What to do if my system hanged?"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by H A NAZIR on 2011-05-28
When i open two many programs i.e web browsers my system often hanged and the whole screen full with lines .In windows7 i can easily solve this problem by pressing ctrl+alt+del keys.But in ubuntu how to solve this problem?
I have 1g.b of ram that is much for ubuntu but why system hangs?
If to do so how to come back into its original state

---

### Post by sikander3786 on 2011-05-28
Hi.

We need to know more about your system specs i.e, processor, RAM (we know already) and graphics card also.

At the time it hangs, do you remember any specific apps running except the browser. Flash being used in the browser etc? Also, which browser are we talking about, Firefox?

For killing a process, you can either press Alt + F2 and type *xkill* and then click the un-responsive window.

Or, press Ctrl + Alt + F1 and login to the tty1 (Terminal). Type,

```
killall firefox-bin
```

Or the name of any process that you want to kill. Then press Ctrl + Alt + F7 to get back to the GUI.

In my opinion, it would be even better to run a memtest on your RAM modules as any of them might not be in good health as the corrupted screen/lines point us to...

---

### Post by Thras0 on 2011-05-28
1 GB of RAM is not that much now a days. Gnome alone takes 2-3oo MB while idle. Google Chrome wastes about 9o-1oo megs too , so the more application you open the harder it is on your system :) 

Firefox 4 uses half of Chromes  needs (~5o megs).

Have you consider adding more RAM to your system ? or perhaps trying a lighter distribution.

**NOTE : flash eat through resources like crazy ^^

---

### Post by H A NAZIR on 2011-05-28
> **sikander3786 said:**
> Hi.

We need to know more about your system specs i.e, processor, RAM (we know already) and graphics card also.

At the time it hangs, do you remember any specific apps running except the browser. Flash being used in the browser etc? Also, which browser are we talking about, Firefox?

For killing a process, you can either press Alt + F2 and type *xkill* and then click the un-responsive window.

Or, press Ctrl + Alt + F1 and login to the tty1 (Terminal). Type,

```
killall firefox-bin
```

Or the name of any process that you want to kill. Then press Ctrl + Alt + F7 to get back to the GUI.

In my opinion, it would be even better to run a memtest on your RAM modules as any of them might not be in good health as the corrupted screen/lines point us to...
Usually i open Mozilla Firefox,Chrome,Gnome Media player and every time downloading of some files remain in progress
I also take memory test but there is no problems found

---

### Post by sikander3786 on 2011-05-28
> **H A NAZIR said:**
> Usually i open Mozilla Firefox,Chrome,Gnome Media player and every time downloading of some files remain in progress
I also take memory test but there is no problems found
memtest is supposed to run over-night. How did you try it? You need to reboot, press and hold <Shift> key as soon as the computer powers on and then from the Grub menu that pops up, select memtest.

You can also do it from a Live CD/USB. 'Test Memory' here:

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

