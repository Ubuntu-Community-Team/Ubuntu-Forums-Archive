---
title: "How to save Ubuntu?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by P-rench on 2011-07-04
I'm currently running Wubi Ubuntu but I would like to run a real verson of ubuntu on a partition. So my question is, how do I save all my settings, desktop, all of my downloaded programs, basically I want to take my ubuntu as it is now and just copy and past it to the new ubuntu install on the partition. is there anyway I can do this without having to start from scratch all over again?

---

### Post by androssofer on 2011-07-04
this any help?

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by frankbooth on 2011-07-04
Settings and configurations can be found in your home folder.
These are hidden (filename starts with a dot), example:
```

.Skype

```
This folder contains all your Skype settings (if it's installed).

To view these hidden folders, press Ctrl+H inside your home folder.
Or click, 'View -> Show hidden files'.

Either save your whole home folder, or choose the configurations you want to keep.

---

As for installed applications and packages...

You could generate a download script trough Synaptic Package Mangager, by going to: 'File -> Generate download script'.
But a simpler way would be to just type down the applications you want to keep and install them manually.

**EDIT:** The guide posted by the user above seems like a better solution :), but it sure seems complex.

---

### Post by Lars Noodén on 2011-07-04
All your settings are in your home directory.  So if you save your home directory, you save your settings.  Make a backup of you your home directory and restore it after doing the new installation.  

If you have the chance to make a separate /home helps if you rebuild your system often or try different distros and want to keep your settings.

---

### Post by Frogs Hair on 2011-07-04
> **P-rench said:**
> I'm currently running Wubi Ubuntu but I would like to run a real verson of ubuntu on a partition. So my question is, how do I save all my settings, desktop, all of my downloaded programs, basically I want to take my ubuntu as it is now and just copy and past it to the new ubuntu install on the partition. is there anyway I can do this without having to start from scratch all over again?

There are couple of threads with the same question . It is possible but not easy with potential for no joy ! Back up your current files to a removable device and do a clean installation or follow the instructions for moving Wubi to a partition .

---

