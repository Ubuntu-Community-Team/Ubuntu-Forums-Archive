---
title: "X11 Problem?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Joomla12 on 2009-02-25
I downloaded a Debian theme package called "Ultimate Edition" that came with many things including a uSplash skin. In all honesty it wasn't that amazing...I changed the uSplash theme back to the default Ubuntu theme and now I get an error after booting from Grub that it doesn't recognize the resolution code. It tells me to hit space to continue or enter to choose a different option. I go into the menu to choose a new code and it works fine. The problem is that it doesn't save the configuration. Any help is appreciated.

---

### Post by stim on 2009-02-25
I'm guessing your splash screen is buggered and that is what your system is complaining about. Try reconstructing the symbolic link to your splash screen.

```

sudo ln -s /usr/lib/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so

sudo dpkg-reconfigure linux-image-`uname -r`

sudo reboot

```





[http://ubuntuforums.org/showthread.php?t=255573]("http://ubuntuforums.org/showthread.php?t=255573")

---

### Post by Joomla12 on 2009-02-27
I'll try this. Thanks for the post.

---

