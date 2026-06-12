---
title: "permission denied and you are not the owner for folders"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-21
I am getting very frustrated trying to install stuff and not having access to my folders and files. I downloaded stuff that I need to put files into the folders of the programs but I either can't find the folders in the first place or I get permission denied or you are not the owner and can't do anything. Example...I found a solution to play Yoville on Firefox and have to put a file in the firefox folder..which I can't find. I have an applet for Awn which needs a file put in schemas..permission denied. I also get the message..you are not the owner. This is my machine and I'm the only user. What the?? I have downloaded the pocketbook guide and spent hours each day for about five weeks trying to work out how to get everything going in Ubuntu but I'm about ready to jump on the Install disk and snivel back to Windows. I used to think I was reasonably intelligent till I tried to switch to Ubuntu. Thunder bird was working fine till I logged on this morning..now it won't send mail. AAAAAAAAHHH. If it wasn't for all the great people on this forum I would have been gone weeks ago. Thankyou to all those guys who have helped me. :)

---

### Post by Greenwidth on 2010-01-21
You can open Nautilus (I'm guessing you're using Gnome) as root with:

```
gksudo nautilus
```

but be careful!

To find where an app is try:

```
whereis <app name>
```

---

### Post by spiderbatdad on 2010-01-21
Definitely fundamental to linux experience is understanding file permissions. File permissions exist for security and to ensure the user doesn't accidentally break the system...that is you have to do it on purpose.
There are loads of tutorials on line explaining linux file permissions. You have to look for hidden files often to add to firefox directories...generally inside .mozilla in your home folder. Sorry you are getting frustrated. It is going to take some time to learn your way around.

---

### Post by rogue_0111 on 2010-01-21
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

or

[http://linuxreviews.org/beginner/](http://linuxreviews.org/beginner/)

or

[http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/](http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/)

---

### Post by spiderbatdad on 2010-01-21
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ThePinkWitch on 2010-01-21
Thankyou. Atleast I know where Firefox is now :)

Reading all the links you guys left. Thanks.

---

### Post by ThePinkWitch on 2010-01-21
> **rogue_0111 said:**
> [http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

or

[http://linuxreviews.org/beginner/](http://linuxreviews.org/beginner/)

or

[http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/](http://peter.upfold.org.uk/blog/2006/07/18/a-guide-to-files-and-folders-on-linux/)


The last one of these links is Particularly good. Really easy to understand. Thanks :)

---

### Post by cenzorrll on 2010-01-21
welcome to the linux learning curve.  It can be a bit overwhelming at first, but eventually you'll start to understand how everything works, even if you haven't done something before.

a few things i've learned, not an exhaustive list, but most developers and distributions seem to follow something like this.

-executablee files (what starts firefox, thunderbird, etc) are usually found in /usr/bin, /usr/sbin (anything with "bin" really) this is where you look if you have to go through folders to find a program to open a file with

-/etc is pretty much what it sounds like, it's a hodgepodge of settings and parameters for your system. if you need to change some system setting, then it's probably in here (remember, there's a reason only the root can change these files)

-any settings that are dependent on a user (mail for thunderbird, specific firefox settings, awn themes and such) are most likely going to be found in a hidden folder in your home directory, /home/user/.config for instance.

-/var contains files that are automatically changed by the computer (such as log files, and i think apt packages, i don't really do much here except realize how i don't really know how to read a log file)

-/dev is your devices, cdrom, hard drives, usb sticks, etc. BEFORE they are mounted.  it's kind of like a bookshelf, you need to pull a book off and open it (mount it) before you can read it.

- $ man <command> is the mother of all "what do all these letters mean and what the hell am i doing in the terminal?" questions. (whenever i'm given a command on the forums i've never used before I *always* do a "man <command>" so i know no one is trying to screw with me)

---

### Post by warfacegod on 2010-01-22
Thought you might want to know that if you can't find what your looking for it may be hidden. Crtl+H to show and hide hidden folders.

---

### Post by rogue_0111 on 2010-01-23
> **ThePinkWitch said:**
> The last one of these links is Particularly good. Really easy to understand. Thanks :)


Glad to help.

If you could only help me write assembly language in exchange:)

---

### Post by rogue_0111 on 2010-01-23
> **warfacegod said:**
> Thought you might want to know that if you can't find what your looking for it may be hidden. Crtl+H to show and hide hidden folders.

Good one warfacegod. I learned something new.

---

### Post by ThePinkWitch on 2010-01-24
> **cenzorrll said:**
> welcome to the linux learning curve.  It can be a bit overwhelming at first, but eventually you'll start to understand how everything works, even if you haven't done something before.

a few things i've learned, not an exhaustive list, but most developers and distributions seem to follow something like this.

-executablee files (what starts firefox, thunderbird, etc) are usually found in /usr/bin, /usr/sbin (anything with "bin" really) this is where you look if you have to go through folders to find a program to open a file with

-/etc is pretty much what it sounds like, it's a hodgepodge of settings and parameters for your system. if you need to change some system setting, then it's probably in here (remember, there's a reason only the root can change these files)



-any settings that are dependent on a user (mail for thunderbird, specific firefox settings, awn themes and such) are most likely going to be found in a hidden folder in your home directory, /home/user/.config for instance.

-/var contains files that are automatically changed by the computer (such as log files, and i think apt packages, i don't really do much here except realize how i don't really know how to read a log file)

-/dev is your devices, cdrom, hard drives, usb sticks, etc. BEFORE they are mounted.  it's kind of like a bookshelf, you need to pull a book off and open it (mount it) before you can read it.

- $ man <command> is the mother of all "what do all these letters mean and what the hell am i doing in the terminal?" questions. (whenever i'm given a command on the forums i've never used before I *always* do a "man <command>" so i know no one is trying to screw with me)

hey this is really helpful ..thanks :)

---

### Post by ThePinkWitch on 2010-01-24
> **warfacegod said:**
> Thought you might want to know that if you can't find what your looking for it may be hidden. Crtl+H to show and hide hidden folders.

Thankyou :)

---

### Post by philinux on 2010-01-24
This might help.

---

### Post by ThePinkWitch on 2010-01-26
> **philinux said:**
> This might help.

Thankyou :)

---

