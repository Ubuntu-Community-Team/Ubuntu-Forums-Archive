---
title: "Wine Permissions(WoW)"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by 0_o on 2009-12-01
Hello, I have been a casual user of various versions of Linux for about two years now. (Mosly just online tutorials, I have no real knowledge)

I recently installed Ubuntu 9.1 for fun, and I am trying to get World of Warcraft to run, but unfortunately I don't have much of an idea of what I'm doing other than what the guides I have read say to do.

I have installed all the games and it is time to start downloading and installing the patches. The thing is I can't access the wine folder anymore to even start WoW.exe.

I can't even find it browsing via Nautilus; before I installed Wrath I was able to no problem.

Everywhere says that the wine folder is located in
```
/home/username/.wine
```
but there seems to be no .wine folder in my user folder.

When I navigate to that directory through the terminal using
```
cd /home/johndoe/.wine
wine WoW.exe
```
I get the following:
```
wine: /home/johndoe/.wine is not owned by you
```
I have have read that Wrath messes up the folder's permissions, but I am very unclear on how to fix this so I can start up wow.exe and continue to download the patches.

---

### Post by Ahadiel on 2009-12-01
Check the owner of .wine:
```
ls -l /home/username | grep wine
```

And then:
```
chown username.username /home/username/.wine
```

---

### Post by 0_o on 2009-12-01
Thank you, I was able to make the /.wine folder my own, now I have to do the same with the World of Warcraft folder and I am unclear on the formatting.
Location of WoW folder:
```
/home/johndoe/.wine/drive_c/Program Files/World of Warcraft

```
What I am trying to use and failing with:
```
chown johndoe.johndoe /home/johndoe/.wine/drive_c/Program Files/World of Warcraft
```

---

### Post by ed-koala on 2009-12-01
This is a known issue with WoW due to the latest patch to their launcher. Here's the solution:

[http://ubuntuforums.org/showthread.php?t=1339198]("http://ubuntuforums.org/showthread.php?t=1339198")

Also check this out:

[http://ubuntuforums.org/showthread.php?t=1340643]("http://ubuntuforums.org/showthread.php?t=1340643")

---

### Post by Ahadiel on 2009-12-01
> **0_o said:**
> Thank you, I was able to make the /.wine folder my own, now I have to do the same with the World of Warcraft folder and I am unclear on the formatting.
Location of WoW folder:
```
/home/johndoe/.wine/drive_c/Program Files/World of Warcraft

```
What I am trying to use and failing with:
```
chown johndoe.johndoe /home/johndoe/.wine/drive_c/Program Files/World of Warcraft
```

Spaces delimit arguments, so you'd have to escape the spaces with "\ " or encapsulate the whole path in quotes.
```
chown -R johndoe.johndoe "/home/johndoe/.wine/driver_c/Program Files/World of Warcraft"
```

-R = recursive.

---

### Post by polpak on 2009-12-08
```
chown -R johndoe.johndoe /home/johndoe/.wine
```

This is probably sufficient.

---

### Post by samsam_eli on 2010-01-10
I tried this and got "operation not permitted"

---

### Post by Ahadiel on 2010-01-10
Try adding a 'sudo' in front of it.

---

