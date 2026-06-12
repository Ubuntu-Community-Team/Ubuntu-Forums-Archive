---
title: "Ubuntu goes to terminal after update and reboot.."
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-03-19
Having just completed an update, and rebooting my PC, I get a terminal window requesting what I want to do next. I do get through the grub menu ok.

I've scoured the internet for possible solutions, but it all seems very vague. Some point to nVidia drivers, which could make sense since that's what I have installed.

I've tried a few commands, but nothing has worked. Even going into recovery mode doesn't help.

Any help would be greatly appreciated, as the pc in it's current state use is of no use to me at all.

---

### Post by isparkes on 2011-03-19
You'll need to put more info up please. Can you give the error message or take a photo of the screen and post it or something like that?

---

### Post by Baldrick_NZ on 2011-03-19
> **isparkes said:**
> You'll need to put more info up please. Can you give the error message or take a photo of the screen and post it or something like that?

Sure. Thanks for responding.

When you boot up, it goes through all the usual processes you'd expect - Grub, choose kernel, start-up. but instead of loading the desktop it loads a white terminal box in the top left of the screen with a black background.

Whilst in the grub menu, I've selected all the kernel options, including the recovery ones, but to no avail. The only one that appears to work is XP.

The terminal window is open as if it's waiting for something to be in-putted. There are no error messages.

I can use any command through the terminal, but can't seem to make it want to go to the Desktop ui.

Hope that helps.

PS: I've tried > sudo apt-get update which does update, but then I have to manually shut down the pc to restart. Once rebooted, I'm presented with the same problem.

---

### Post by wep940 on 2011-03-19
Try checking this link.  Pay attention to the 10.04 stuff as well as the 9.10 or higher section.  If you have problems, check the common issues section.  I hope that will help you.  If not, there are more threads on the net I can look at.

---

### Post by Baldrick_NZ on 2011-03-19
sorry, can't see link. please re-post...

---

### Post by rburkartjo on 2011-03-19
bal it seems that x is broken. try this when you boot into terminal login  with user name and then password
then run this command  sudo aptitude update && sudo aptitude safe-upgrade(if it asks for your password enter). then answer yes to any updates and install them. then run sudo reboot now (again if it asks for you password enter.)see what happens when you reboot. if still no x try this again from the terminal- sudo service gdm start. good luck

---

### Post by Baldrick_NZ on 2011-03-19
Needed a quick(ish) fix, so made a fresh install of 10.04. 

All good now. Thanks for your help all! Much appreciated.

---

### Post by Dlambert on 2011-03-19
For future note, after i upgrade i have to manually install my graphics drivers into the new kernel, or hold shift at boot and boot from previous kernel.

---

