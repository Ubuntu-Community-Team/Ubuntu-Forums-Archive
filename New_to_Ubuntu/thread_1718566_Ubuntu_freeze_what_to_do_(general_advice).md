---
title: "Ubuntu freeze: what to do? (general advice)"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by seragx99 on 2011-03-31
Hi guys! I've installed and re-installed Ubuntu a few occasions for now in many different pcs i've had over the years, but for some reason always something goes wrong (not saying ubuntu's fault). The reason why i am writing this right now is that my new install has frozen on startup and after reboot everything seems normal but i know deep down something will go bad any time. In previous installs when it freezes i simply hard shut-down but i know that's dangerous. My big question here is: *What to do when Ubuntu freezes and after that?* I mean is there anyway to generate crash reports and use them to fix the problem or repair mis closed files? TY!

---

### Post by ajgreeny on 2011-03-31
You really need to find out why the freezes occur, not how to get out of them when they happen, but let's deal with that in a minute.

What hardware do you have, particularly the graphics card, and have you run the memtest 86+ from grub; if not it is worth doing so to check that your memory modules are OK.  Let it run for a few hours, preferably overnight and look for error numbers on the bottom line before you stop it.  There should be none at all, and if any show it is one of the memory modules that is faulty; you will need to run the test with each module separately to find which one, if you have two or more memory modules in the computer.

You may be able to get out of a freeze more kindly by holding down  and then slowly typing REISUB with about 2 secs between each key press, or try Ctrl+Alt+F1 to get to a console, then login with username and password, then ```
sudo reboot
```  However if your keyboard is also frozen, as sometimes happens, you will not be able to do anything except a hard reboot.

---

