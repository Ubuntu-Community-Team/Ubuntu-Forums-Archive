---
title: "windows lack title bar, no text in terminal"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by johanus on 2009-08-07
On a new install of 9.04 I had some success in editing xorg.conf to add vert and horiz freq for my monitor. However, can't get good settings to lock in across reboots.
After running nvidia-settings as root so the settings could be saved to the xorg-conf file, I now find that all desktop windows lack a title bar; the terminal window shows no text, just a stark white rectangle.  I can tell that the "blind" window is working, but not seeing anything is daunting! :D

Video card is GeForce MX440; motherboard ASUS P4S533VL;

---

### Post by coldReactive on 2009-08-08
ALT+F2

type in metacity --replace

check Run in terminal

and tell us what happens.

---

### Post by johanus on 2009-08-08
Ok, that helped.  I now see that I at first lacked both menu and title bars.
Running your command restored  menu bars (and scroll bars), but I still have no title bars.
The desktop terminal screen now shows my prompt, but it still will not show text that I enter.  The prompt is followed by a small rectanglar box which I think shouldn't be there. :D

---

### Post by coldReactive on 2009-08-08
> **johanus said:**
> Ok, that helped.  I now see that I at first lacked both menu and title bars.
Running your command restored  menu bars (and scroll bars), but I still have no title bars.
The desktop terminal screen now shows my prompt, but it still will not show text that I enter.  The prompt is followed by a small rectanglar box which I think shouldn't be there. :D

That's because you specified that it should run the command that I told you to run in terminal. You can't enter anything until you close that terminal.

Close the terminal, if your titlebars disappear again, hit ALT+F2 again, and run metacity --replace WITHOUT CHECKING RUN IN TERMINAL.

You should never login to root on an ubuntu computer to install anything, even nVidia drivers.

Read this thread for nVidia drivers: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) and make sure you uninstall your current nVidia drivers.

---

### Post by johanus on 2009-08-09
Thank you again for the help. I now have normal windows.  I'll look closely at the link you referenced about installing Nvidia
drivers.

---

