---
title: "setting what happens when you insert usb device"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-10
i would like to set ubuntu so that when i insert a usb drive it shows up as a icon on the deskotop and doesn't show it's contents without me clicking the icon.  is there a way to do it?

---

### Post by kansasnoob on 2009-03-10
Install pmount from synaptic or go to terminal and:

```
sudo apt-get install pmount
```

Brief explanation from synaptic:

> pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

Now, if you use this drive in Win always remember to "safely remove" and even in Ubuntu remember to "unmount" before unplugging!

---

### Post by mamamia88 on 2009-03-10
thanks it worked

---

### Post by stoogiebuncho on 2009-03-10
Sounds like you've got this fixed, but there's a simpler way to do it if someone else with the same problem happens across this thread.

Open up Nautilus (your file manager) and go to File > Preferences > Media and uncheck "Browse Media When Inserted"

---

