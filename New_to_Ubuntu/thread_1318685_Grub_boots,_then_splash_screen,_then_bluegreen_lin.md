---
title: "Grub boots, then splash screen, then blue/green lines and loads to corrupt."
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Sourmiloko on 2009-11-07
Hi, Somebody please help me! So IDK why but today turning on my computer, it went to load up as normal and after the splash screen the screen showed all these green and blue lines and finally loaded to a desktop filled with white and black horizontal lines and magenta squares. I think somehow my OS was corrupted, and I would like to reinstall Ubuntu. The only problem is, I cant load up the gnome desktop to change anything. I would like to install ubuntu without formatting /home. but I dont know how. Can I do something off my LiveCD(which I'm using now)? I have went into Recovery mode and had it check and fix all the options I could. But still loads the same corrupt screen.

PLEASE HELP!

---

### Post by Sourmiloko on 2009-11-07
[Bump!] please help!

---

### Post by cariboo on 2009-11-07
There is nothing wrong with your installation, it more than likely is a driver problem. What video adapter do you have and are you using the restricted drivers?

If you are using the restricted drivers try the following, press Ctrl-Alt-F1, at the prompt type:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

This will move the configuration file to a backup leaving, with no /etc/X11/xorg.cong, next at the prompt type:

```
sudo reboot
```

This will reboot your system and hopefully get you back to a working desktop.

---

### Post by Sourmiloko on 2009-11-07
Will this work in LiveCD? Or should I enter recovery mode on the actual OS?

---

