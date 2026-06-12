---
title: "mythubuntu uninstall problems"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by zabergan on 2008-12-12
I'm running ubuntu 8.10 on my computer and I recently installed mythubuntu but didn't really like it so I uninstalled it using the synaptic package manager but now I have some problems on setup. After I boot I get this message:
"No exec line in this session file in mythubuntu. Running the GNOME failsafe session instead."
Then after I click ok to continue I get another message:
"This is the failsafe GNOME session.You will be logged onto the Default session of GNOME without the startup scripts being run. This should be used to fix problems in your installation."
Then I click ok and ubuntu runs normally.
Is there any way I can get rid of these messages?

---

### Post by LowSky on 2008-12-12
sudo apt-get autoremove
sudo apt-get update $$ sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

---

### Post by zabergan on 2008-12-12
[QUOTE=LowSky;6356817]sudo apt-get autoremove
sudo apt-get update $$ sudo apt-get upgrade
sudo apt-get install ubuntu-desktop[/QUOTE

Tried that then re-booted but got the same messages

---

### Post by dub11 on 2008-12-13
Hi Zabergan

You and I seem to be the only people in the universe with this problem.  I too am new to Ubuntu.....and to the plethora of "bum steers" that ricochet around these forums.

After a whole day of uninstalling, reinstalling, re-uninstalling, re-reinstalling I finally solved the mystery.....and as usual it is  quite simple.

If you look in your $home directory (make sure check the "show hidden files" box in the view menu!) you will see a file called .dmrc (the offender).

Edit this file and replace the variable "mythbuntu" with "gnome".  Thats it.  End of story.  Simple as that!!!

[Desktop]
Session=gnome

Good luck.

---

