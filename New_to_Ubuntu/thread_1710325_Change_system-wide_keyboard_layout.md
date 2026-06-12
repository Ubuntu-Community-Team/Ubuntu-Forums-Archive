---
title: "Change system-wide keyboard layout"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by dericke on 2011-03-19
Using xubuntu 10.10

I use a Dvorak keyboard layout, which I selected at installation. The problem is that I am trying to set up two other users on the system to use QWERTY. I can't find a way to change the system default keyboard layout, which seems to now be Dvorak.

Where do I change the layout system-wide? Ideally I'd have a user-specific Dvorak layout for myself, and default to US standard layout otherwise. But I can't find the setting. Xfce 4 settings manager only changes user settings, and I have the keyboard settings set to defer to system settings, which are apparently Dvorak. In the Settings Editor, under keyboard-layout > Default, I see properties for XkbModel:logiaccess (correct) and XkbDisable:TRUE, but none for Xkblayout, and the Add Property button is disabled. I also found instructions to edit /etc/X11/xorg.conf, but no such file is there. Where do I change this system setting?

---

### Post by pauljwells on 2011-04-12
I've been struggling with this for weeks too!
Finally I found this:

```
sudo dpkg-reconfigure keyboard-configuration
```

I think it does what you want. It changes the settings in /etc/defaults/keyboard but it also has to regenerate the kernel boot image so I don't think just changing the file by hand will do anything.

Hope this helps...

---

### Post by vpmm99 on 2012-09-29
here you have the solution :
 [http://ubuntuforums.org/showthread.php?p=11936770](http://ubuntuforums.org/showthread.php?p=11936770)


modify as root the following file
/etc/default/keyboard

---

### Post by oldos2er on 2012-09-29
Old thread closed. Please don't bump old threads.

---

