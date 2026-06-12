---
title: "Running Bash scripts outside terminal window?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Tnoty on 2010-01-30
Hello. I'm new to bash scripting in Ubuntu. I've been playing around a bit, writing scripts and trying to figure out if there is a way to run the scripts "outside" of the terminal window. So far I've only seen them run in terminal window.

---

### Post by kayvortex on 2010-01-30
Well, the scripts are just commands for the shell to interpret in sequence, and the shell has no other purpose than to interpret user commands at a terminal; so, unless I am very much mistaken, I doubt you'll find a shell that can run scripts "outside the terminal". If you want things to run outside of the terminal, then you'll need to use GUI libraries to draw and handle the windows for you, which is way beyond the shell's scope (by design).

---

### Post by SecretCode on 2010-01-30
You could run them from the Alt-F2 'Run Application' window. You could run them from [cron]("https://help.ubuntu.com/community/CronHowto") jobs. You could run them from other bash scripts!

---

### Post by kaibob on 2010-01-30
Perhaps this is obvious but you can run scripts from a launcher on your desktop or from a panel. They can also be run as Nautilus scripts.

---

### Post by oldfred on 2010-01-30
Nautilus scripts can be run from your Nautilus right click scripts if in this (hidden) folder in your home, my home shown.

/home/fred/.gnome2/nautilus-scripts
All executable files in this folder will appear in the Scripts menu. Choosing a script from the menu will run that script.

---

