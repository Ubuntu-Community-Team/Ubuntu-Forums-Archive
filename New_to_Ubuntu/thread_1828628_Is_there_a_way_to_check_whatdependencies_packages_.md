---
title: "Is there a way to check whatdependencies/ packages my system is missin?"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by zengrz on 2011-08-19
I did something stupid.

I was trying to install a program, but the installation ended up failing due to some missing dependencies and those dependencies could not be found in the archive using apt-get. So I tried to undo the installation of all the other files I had successfully installed, since I assumed that I would not need them for any other programs. Then I discovered apt-undo.

So, I was happily undoing everything without realizing that apt-undo is recursively uninstalling other packages that was previously installed in the system. Finally, I was asked to uninstall ubuntu-desktop, then I realized something went wrong.

I am pretty sure that I have uninstalled a lot of packages that I do not intend to uninstall. Although my system runs well right now, I am a bit paranoid about the missing packages. Is there a way to perform a check to see if my system or any programs is missing any important packages?

Thanks~

---

### Post by Lucradia on 2011-08-19
I'd like to know this as well as how to force a dependency check on a system that doesn't check for depends when installing most packages even though it has apt.

---

### Post by LowSky on 2011-08-19
You can force an install but not a dependency check as far as I know. Ubuntu and every other distro that uses apt-get does dependency checks.

What is the program that cannot be installed.

---

### Post by capink on 2011-08-19
```
sudo apt-get install -f
```

If you run the above command and it does not do anything, it means you have nothing to worry about.

---

### Post by oldos2er on 2011-08-19
```
apt-get check
```

It's safe to remove ubuntu-desktop, which is a metapackage.

---

### Post by s.fox on 2011-08-19
Thread moved to [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by zengrz on 2011-08-19
Thanks for all the replies, I guess my system is fine for now, lol

---

### Post by zengrz on 2011-08-19
> **LowSky said:**
> What is the program that cannot be installed.


Well, actually I forgot. But I remember it is some kind of stream player that is crudely ported to Ubuntu from Windows, and there are only two packages out of many that are missing...

Thanks anyways!

---

### Post by zengrz on 2011-08-19
Maybe I will ask the question the other way around: Is there a way to check for isolated packages?

Thanks!

---

### Post by MattBD on 2011-08-19
Run the following command in the terminal to check the dependencies for a package:
```
apt-cache depends packagename
```

---

### Post by oldos2er on 2011-08-19
> **zengrz said:**
> Maybe I will ask the question the other way around: Is there a way to check for isolated packages?

If I understand you correctly ```
sudo apt-get autoremove
``` is what you're looking for. ```
man apt-get
``` has a lot of info on the various apt-get options.

---

### Post by zengrz on 2011-08-20
nice! you guys are so cool!:guitar:

---

