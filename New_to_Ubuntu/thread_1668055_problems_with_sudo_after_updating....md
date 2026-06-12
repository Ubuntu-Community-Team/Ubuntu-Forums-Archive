---
title: "problems with sudo after updating..."
date: 2011-01-15
forum: New to Ubuntu
---

### Post by 543432321234 on 2011-01-15
hi there, I've been having problems with using sudo ever since i updated it about a month ago. one day, i opened up the update manager, updated a few things, restarted the computer, and a couple days later, tried to install a program through the terminal using the sudo command. after i typed in "sudo apt-get install bluez" it asked me for my password. i typed it in, hit enter, and it said that i typed the wrong password. i checked my spelling, no errors. its all numbers, so capslock has nothing to do with it. i tried using synaptic package manager the same day, and it asked me for my password, and it said that was wrong too. any suggestions?

I am also running Ubuntu desktop 10.04

---

### Post by kn0w-b1nary on 2011-01-15
so you can still login? or is it automatic?
have you tried launching a root prompt from GRUB recovery mode and typing in "visudo" and made sure your username was listed? you can also type "passwd" and change the password, reboot, login as root (no-graphics), launch GUI (not sure how to in Gnome, but in xubuntu it's "start xfce4"), then change your password. Should fix it.

Hope this helps!

---

### Post by 543432321234 on 2011-01-15
Could you please explain how to get into the GRUB prompt? sorry, im a complete newbie to all things linux. also, i tried the "passwd" line in teerminal and it said "Authentication token manipulation error".

---

### Post by kn0w-b1nary on 2011-01-15
when starting your computer, before the splash (the ubuntu and dots) hit Shift repeatedly, (you have to be fast) and it might take several reboots to get it. You will "GRUB loading" and then a menu. Select recovery mode (if there are several, choose the one closest to the top. In the next menu, Select "exit to root prompt"

There you go!

---

### Post by 543432321234 on 2011-01-15
it is finally working! thank you so much!

---

### Post by kn0w-b1nary on 2011-01-16
you are welcome!

note: i consider this as a security breach, so just be aware!

---

