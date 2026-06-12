---
title: "log on as root"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by m3t3ors on 2009-01-21
i need to log in as root to install nerolinux
but its not letting me as i didnt get an option during install to set a password any one help me out:(

---

### Post by jerome1232 on 2009-01-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You should be able to just run the installer with root privilages using sudo, use your own password to authenticate
```
sudo /path/to/installer
```

---

### Post by Joeb454 on 2009-01-21
As mentioned above, Ubuntu uses the "sudo" feature as opposed to logging in as root.

Lets say your install file is located on your Desktop, you could run ```
sudo ~/Desktop/nerolinux_install.file
```

Obviously using whatever the file name actually is ;)

---

### Post by donkyhotay on 2009-01-21
Also, it is against forum policies to explain how to enable root user. It's assumed that if you are not proficient enough to figure out how to enable the root account on your own, you do not have the experience required to need root access without using sudo.

---

### Post by m3t3ors on 2009-01-21
thanx i have it all wrote down somewhere but ive been decoating the office and cant find anything i need

---

### Post by Michael.Godawski on 2009-01-21
hi,

I ran an irc class about root and sudo recently. If you have some spare time you can look through the log:

[https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/01172009](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/01172009)

Also check out for future irc classes organized by the Education Focus Group :)

---

### Post by m3t3ors on 2009-01-22
thanks for that michael, il have a read of it

---

