---
title: "xorg won't open"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Scott_MacAdam on 2009-12-31
hey everyone, i need to open/edit xorg to fix my screen resolution but it won't open, it just jumps right back to the command prompt.

This is what it looks like:

tyler@tyler-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for tyler:
tyler@tyler-desktop:~$ 

Any ideas?

~Scott MacAdam

---

### Post by bkratz on 2009-12-31
> **Scott_MacAdam said:**
> hey everyone, i need to open/edit xorg to fix my screen resolution but it won't open, it just jumps right back to the command prompt.

This is what it looks like:

tyler@tyler-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for tyler:
tyler@tyler-desktop:~$ 

Any ideas?

~Scott MacAdam



If you are running 9.10 see this thread

[http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

---

### Post by danastasio on 2009-12-31
if you want to open the file, you using the wrong command, 

either

```
gksudo /etc/X11/xorg.conf
```

OR

```
sudo nano /etc/X11/xorg.conf
```

will open the file for you.

---

### Post by gabo.cr on 2009-12-31
Are you using Karmic?
The "xorg.conf" file is not located in the same place as before.
You would have to create the file to make specific changes.

---

### Post by Scott_MacAdam on 2009-12-31
yep, that appears to be it. so I have to create an xorg then that will override the automatic systems?

The problem is that the resolution by default only goes up to 800x600 but the screen should be more like 1200 x 800.

---

### Post by gabo.cr on 2009-12-31
You can follow the instructions at the Thread link given by "bkratz".

---

### Post by gabo.cr on 2009-12-31
Somebody gave me [this link]("http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html").
Those instructions are a lot easier to follow.
I just did it and it works perfectly.
Good luck!

---

