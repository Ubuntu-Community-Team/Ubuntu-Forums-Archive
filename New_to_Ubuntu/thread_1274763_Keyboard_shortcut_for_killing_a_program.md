---
title: "Keyboard shortcut for killing a program?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by hybridanime00x on 2009-09-24
Hello. I'm fairly new to Ubuntu, and I was just wondering if it is possible to create a keyboard shortcut that will kill a program in the foreground. My computer is pretty slow, so a shortcut of this sort would be very handy for stopping a particularly slow app.
Thank you.

---

### Post by cariboo on 2009-09-24
You can create a launcher for xkill:

Right click on the desktop and select Create Launcher then see the screenshot for what to enter.

---

### Post by Bimps on 2009-11-14
System --> Preferences --> Keyboard Shortcuts

Click Add. Type the name of the shortcut; whatever you choose is fine.
In the **Command** field, type ***xkill***.

Click Apply. To assign a keyboard shortcut, just click on where it says "Disabled" and assign the new shortcut.

---

### Post by 7raTEYdCql on 2009-11-14
I prefer the old terminal approach.

ps -eaf | grep "name of the progra"
This returns a process id.
kill "process id returned"

Though xkill is also a easier, more modern option.

---

### Post by WitchCraft on 2009-11-14
> **i.mehrzad said:**
> I prefer the old terminal approach.

ps -eaf | grep "name of the progra"
This returns a process id.
kill "process id returned"

Though xkill is also a easier, more modern option.

pkill firefox
is a more efficient way.
furthermore:
killall firefox

---

