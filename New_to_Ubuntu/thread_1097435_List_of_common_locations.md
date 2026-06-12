---
title: "List of common locations?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-03-16
Hi, I was wondering if there was a list out there that would help newbies know where to put things that they download/install.

For instance, I recently learned that I should put the themes I download into /usr/share/themes (and then I have to change permissions?).  I presume I need to put icons I download into /usr/share/icons.

Is there more info out there like this?  For the most part, the file system is a complete mystery to me, and I suspect it is to many new users as well.

Thanks!

---

### Post by Bios Element on 2009-03-16
Hey Nixie, This might prove to be of some use. [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by Nixie Pixel on 2009-03-16
Thank you, that is a great start!  I am hoping to find something that can go into more detail, such as where I should put backgrounds, fonts, applications, drivers, and so on.  

Thanks again!

---

### Post by Bios Element on 2009-03-16
> **Nixie Pixel said:**
> Thank you, that is a great start!  I am hoping to find something that can go into more detail, such as where I should put backgrounds, fonts, applications, drivers, and so on.  

Thanks again!

Well backgrounds generally go in /usr/share/backgrounds but if it's just a single user system there's no reason why you couldn't toss them in a /home/username/.backgrounds folder.

Fonts appear to go in /usr/share/fonts but I've never tinkered with them so I can't give an answer on tinkering with them.

Applications usually go in /usr and kinda get tossed all over the place. I'm sure there's great logic behind it but I don't know it. All the files in there though are going to be handled by the package manager so you generally don't want to touch them.

Applications which are not handled by the package manager should go in /opt.

As for drivers, I have no idea but as they're usually handled by the package manager I'd take a guess that they're either in the /sys or /usr folders.

Hope my mostly ignorant response helps a bit. ^_^

---

### Post by nitrofurano on 2009-03-17
well, i normally use the following directories
(assuming you know '~/' is '/home/username/' - this is common on all unixes, i think... - '/usr/share/' seems to be for stuff you want to all users accessing them...)

~/.fonts - for installing typefaces
~/.backgrounds - for wallpapers
~/.themes - what you're seems to use

well, i personally were using this as well:
~/.gnome-color-chooser - for color schemes (well, i use gnome-color-chooser a lot...)

and since i'm all the time enabling and disabling stuff, i'm also have the following folders - it became as habit from the good times using MacOS-Classic (specially 7.1)

~/.fonts_disabled
~/.backgrounds_disabled
~/.themes_disabled

the wallpapers i used to use a script to random them when booting - and i move to _disabled those i don't enjoy at all...

the fonts at _disabled are those i don't want to have installed on the time i were using, for saving speed and memory, and having the font list smaller and a bit more organized (at least, not too much chaotic)

---

### Post by nitrofurano on 2009-03-17
i also use /opt/ directory a lot, specially for Wine, Java and Python apps and games
~/Documents from me is used to be a link to /mnt/sda4/Documents
and the /mnt/ folders i used to keep the same name of /dev/ partitions - like /mnt/sda2 from /dev/sda2 (it's a MacOS-X hfsplus partition), /mnt/sda4 from /dev/sda4 (another ext3 partition, just for documents, and being a bit safe from the eventual need of reinstalling Ubuntu - and when, documents i may have on the root partition (sda3) i used to backup to there from a live-cd, for example )

---

