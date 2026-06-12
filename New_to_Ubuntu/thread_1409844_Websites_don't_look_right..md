---
title: "Websites don't look right."
date: 2010-02-18
forum: New to Ubuntu
---

### Post by ron_jeremy on 2010-02-18
Most websites (these forums included) I visit (**Firefox 3.6 on Ubuntu 9.10 x86**) just don't look right. I have installed/reinstalled Adobe Flash so many times using numerous different methods I think my head is still spinning. In fact, since installing Ubuntu this morning I've got zero work done because I'm too busy copy/pasting terminal commands or posting forum questions asking how to do super complex things like installing Flash, but I digress...

Anyway, according to Synaptic, my current 'flash' situation is as follows:

adobe-flashplugin
Adobe Flash Player plugin version 10
10.0.45.2-1karmic1

Any suggestions to help me on my way would be greatly appreciated. I followed the instructions (in blue) [in this first post]("http://ubuntuforums.org/showthread.php?p=3923465") but it did not work. I dug out an old HP notebook & installed Ubuntu on it & **Firefox 3.5** exhibits the same issues. The 2 images below illustrate the problem:

[IMG]http://i72.photobucket.com/albums/i181/thanasi67/general/flash-error.png[/IMG]

[IMG]http://i72.photobucket.com/albums/i181/thanasi67/general/facebook-error.png[/IMG]

---

### Post by lijcam on 2010-02-18
Try installing the MS true type fonts.

```
sudo apt-get install msttcorefonts
```

---

### Post by lovinglinux on 2010-02-19
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by dzon65 on 2010-02-19
Why don't you install flashplugin nonfree? (comes with the installer).

---

