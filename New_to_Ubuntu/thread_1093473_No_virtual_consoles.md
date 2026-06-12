---
title: "No virtual consoles"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ZZaa211 on 2009-03-11
I use Ubuntu8.04, latest updates as of today, 11Mar09. Using on a pc w. 1GB RAM,AMD 2700 CPU, Gnome 2.22.3, Linux 2.6.24-23-generic kernal, ATI 9600 graphics card, dual boot with XP Home.

Problem: for last two times I have used the Linux partition (last used in early January09), I have been unable to access virtual consoles at all. Keystrokes: Alt-Fx are all trapped by Gnome. *Even when these keystroke traps are disabled in Sytem>Keyboard_Shortcuts* still can't access virtual consoles. Keystroke: Alt+Ctrl+Fx does not work at all. I have not added any new software nor have I changed keyboard traps except to try to access virtual terminals.

I use virtual consoles fairly often. I could find nothing in existing forums, except the suggestion to use *sudo telinit x*.  ps -A|grep tty shows that the terminals exist as far as the system is concerned. ALT and CTRL keys work under XP for use in OO, GIMP, etc.

I co-teach an intro' to Ubuntu class here in the Northwest, so I need to know what to tell students in re: accessing virtual terminals. What is the new, improved way to access virtual consoles under the latest Hardy Heron upgrade? :o

Thanks for your help with this issue! :D

---

### Post by kestrel1 on 2009-03-11
You should just be using CTRL, ALT & F1 to F6 for this CTRL, ALT & F7 should get you back to xserver.

---

### Post by ZZaa211 on 2009-03-11
> **kestrel1 said:**
> You should just be using CTRL, ALT & F1 to F6 for this CTRL, ALT & F7 should get you back to xserver.


Correct. Still I am unable to access any virtual consoles. I will try a previous update (from GRUB boot menu) to see if my problem comes from the latest, greatest upgrade of 8.04. Disappointing when a long term feature of Unix/Linux is suddenly unavailable.

Thanks for the reminder that CTRL+ALT+F7 "returns" to Xserver "console". :)

---

### Post by kestrel1 on 2009-03-12
Found a very old thread: [http://ubuntuforums.org/showthread.php?t=220271](http://ubuntuforums.org/showthread.php?t=220271)
It is suggested there that you try CTRL, ALT & F6 first for some reason. Can't see why that should work though.
Edit: 
Just found another thread that may help: [http://ubuntuforums.org/showthread.php?t=246909](http://ubuntuforums.org/showthread.php?t=246909)

---

