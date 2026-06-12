---
title: "Help Lost Grub"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by John Hale on 2009-04-05
I installed an extra 1gb of ram into my computer 512mb before, and when I tried to reboot ubuntu got stuck on that black start up screen, I wait 10 minutes and it didn't change so I turned it off at the wall, now it boots straight into ubuntu and I can't get into windows
Help

---

### Post by scragar on 2009-04-05
Grub will still be installed, check your:
/boot/grub/menu.lst
file for the **hiddenmenu** option and make sure it's turned off. Also try changing the time it waits.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by enri2 on 2009-04-05
maybe this will help you
[http://ubuntuforums.org/showthread.php?t=1114171](http://ubuntuforums.org/showthread.php?t=1114171)

---

### Post by fooman on 2009-04-05
if you would like to have a gui to make the change,  install startupmanager....you can change those settings as well as many others with it.

to install,  use add/remove,  synaptic,  or just open a terminal and type (or copy/paste) the following:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

under the "boot options" tab...make sure that "use timeout in bootloader menu" is checked and set the time you would like it to display.

hope that helps.

---

