---
title: "boot screen"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by impatientboi on 2009-10-21
when the boot screen pops up and asks me to select which operating system to install from, it is a plain black screen with white text . . . .is there anyway i can change this so it's got a pretty picture in the back ground instead of the boring black one?

---

### Post by pgar23 on 2009-10-21
I dont know how solid this is with this answer, but from my experience so far (using ubuntu for 2 years) I am almost positive that you cannot add a background image to the GRUB boot menu. You can only edit it, WITH CAUTION though. If you edit or delete the wrong things, your system is liable to be unbootable.

But before you edit this file, make a back-up of it.
```

sudo cp /boot/grub/grub.conf /boot/grub/grub.conf.bak

```

To edit:
```

sudo gedit /boot/grub/grub.conf

```

---

### Post by fooman on 2009-10-21
i used the following guide *years ago* to make a very nice looking grub menu. i cannot say if it still works or not,  but looking at the most recent posts....it does not look good.  :(

[http://ubuntuforums.org/showthread.php?t=208855&highlight=grub+suse](http://ubuntuforums.org/showthread.php?t=208855&highlight=grub+suse)

you *can* however,  change it to a nice, pretty blue w/white text (or other colors) by installing startup-manager.  it is available from synaptic,  or open a terminal and type or copy/paste the following into it:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > administration > startup-manager

when it opens look under the "appearance" tab.  put a check next to "use colors in bootloader menu".  blue and white is what it is set to....you can change that there as well.

hope that helps.

---

### Post by pgar23 on 2009-10-21
Found something that is very relative to what you are looking for.
It states that it is for Fedora but has general description of howto.

Follow my advice about backing up those files before editing them though.

[http://www.osresources.com/1_5_en.html](http://www.osresources.com/1_5_en.html)

---

