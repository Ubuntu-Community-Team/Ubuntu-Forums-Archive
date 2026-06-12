---
title: "sudo nvidia-settings not remembering"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by earthpigg on 2010-12-25
Hi,

My buddy interrupted an update for reasons beyond my comprehension. oh yeah, he was playing a video game and wanted the interruption to go away and stop slowing the game down... sigh.

afterwards, x was all jacked up. 3/4 of the screen would wrap around to the opposite side, 800x600, few error messages, etc.

i did this:

sudo dpkg --configure -a (or whatever the exact command is that synaptic provides)

system -> admin -> additional drivers -> disable all

restarted computer, no drivers being used as expected.

went back to system -> admin -> additional drivers -> re-enabled the nvidia driver

sudo nvidia settings -> change the display from 800x600 to auto, save to x config file, quit.


and things are pretty much back to working, except that nvidia-settings will not remember the display's resolution and defaults to 800x600 every reboot.

going to system -> admin -> nvidia x server settings or sudo nvidia-settings allows him to quickly set the resolution to 'auto' and get things working, but it's a pain to have to do this every time. various combinations of running it from the terminal and from the menu, and 'merge to existing x config file' being checked and unchecked aren't making a difference.

it's a 10.10 system that had been in-place upgraded from 10.04, and the video card has always been perfectly well supported prior to my buddy interrupting the update.

ideas?

---

### Post by TeoBigusGeekus on 2010-12-25
Backup your /etc/X11/xorg.conf file somewhere and delete it.
Reboot and enter recovery mode.
```
sudo nvidia-xconfig
```
to generate a new xorg.conf file.
Then 
```
sudo reboot
```
Once in gui
```
gksu nvidia-settings
```
and try again.

EDIT: Perhaps your problem is related to [this]("http://www.psychocats.net/ubuntu/graphicalsudo"), ie. using sudo instead of gksu for nvidia-settings affected only the root's configuration file.

---

### Post by earthpigg on 2010-12-25
did all of that exactly, using gksu, still no dice.

i did learn something new, however: it only affects his user account. when i login as myself, the problem does not present. it is also not present at the gdm login screen, which should have been my first hint.

time to go dotfile hunting. to save myself time, does anyone know which dotfile(s) i need to delete or copy over from my user account on his machine?

---

### Post by earthpigg on 2010-12-25
mmk, no obvious dotfile. .nvidia-settings-rc wasn't it, and there doesn't seem to be anything relevant in his .gconf, .gconfd, .config, or any other obvious dotfolders.

i could probably delete all of his dotfiles, but that would be throwing the baby out with the bathwater.

what dotfile did i overlook?

---

### Post by TeoBigusGeekus on 2010-12-25
Just an idea: why don't you create a new account for him, copying in his new home folder the settings he needs most (ie. browser's folder, mail client's folder etc.) from his old one? 
Just saying...

That's why I love Openbox nowadays: a handful of configuration files - when something goes wrong, you know where to look.

---

### Post by earthpigg on 2010-12-25
great idea.

---

