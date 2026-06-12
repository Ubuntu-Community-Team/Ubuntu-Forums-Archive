---
title: "Keyboard Symbols Missing or Mixed Up"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-20
Hello everyone,

I was playing around with Gparted, and made such a mess of things, it seemed easier to reinstall. I installed Hardy 8.04.3 from a Live CD.

I chose to start from scratch, saving nothing. Now a question about my Keyboard. Some of the characters have changed or have gone missing.

Ie.

I cannot get the "at" to work, shows as **"**
forward slash =** é**
question mark= **É**

Many other symbols are missing or show different symbols, when trying to access.

You get the idea.

I use a HP Keyboard.

Any ideasÉ

---

### Post by prshah on 2009-08-20
> **mikodo said:**
> 
I cannot get the "at" to work, shows as **"**
forward slash =** é**
question mark= **É**


You may have the keyboard layout set wrongly (to greek?). You can change it from System-Preferences-Keyboard-Layouts. Click the "Apply system-wide" button after changing to the appropriate layout (US?)

---

### Post by swoody on 2009-08-20
Just as prshah said, this seems to be the wrong layout selected for your computer. You may have overlooked it while you were reinstalling Ubuntu. Try as he says above, and that should get you back on track. Also, to prevent this from popping up in the future, completely remove your current layout (the incorrect one) from that list. Then you should be good to go :)

---

### Post by mikodo on 2009-08-20
> **prshah said:**
> You may have the keyboard layout set wrongly (to greek?). You can change it from System-Preferences-Keyboard-Layouts. Click the "Apply system-wide" button after changing to the appropriate layout (US?)

Yes, It was set for Canadian  layout, which seems to be for French and Inuit????

When I set the keyboard layout for USA, all is good! Even though I live just north of America in Canada. Go figure! Can't find the "Apply system-wide" button though, but the settings seem to remain as they should, with out it.

Thanks for the assistance.

---

### Post by prshah on 2009-08-20
> **mikodo said:**
> but the settings seem to remain as they should, with out it.

OK that's nice.

_If_ you find that the settings are not persisting across reboots, see any of these links 

[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

### Post by mikodo on 2009-08-20
> **prshah said:**
> OK that's nice.

_If_ you find that the settings are not persisting across reboots, see any of these links 

[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

Thanks for the work looking these up! I very much appreciate your time while doing this.

Mike

---

