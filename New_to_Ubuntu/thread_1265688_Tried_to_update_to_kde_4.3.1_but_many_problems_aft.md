---
title: "Tried to update to kde 4.3.1 but many problems after"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by foska on 2009-09-13
Hi,

I tried to update my Kubutu install today to KDE 4.3.1 since I read that it contained a number of bug fixes.  After the upgrade however, my system has not function propoerly at all.  When I logon I get a screen with a "chequered" (black and white boxes like a chess board) background and shortly after that I get a dialog box saying " No system tray detected on this system. Unable to start exiting" When I click OK, the box disappears and I am left with the background described above (no icons or kickoff)  If I do Ctrl+Alt+F1, I can get a command prompt type interface where I can type my login name and password and do directory listings etc.  Can anyone help me to restore my system without having to do a fresh install?

---

### Post by yeats on 2009-09-13
You could try this:  There is a hidden file in your home folder called .kde (or .kde4 - could be either).  You could try moving it:

```
mv .kde .kde.bak
```

then when you log in, KDE will create a new environment for you.

---

### Post by Ms_Angel_D on 2009-09-13
Do not update with kpackagekit, this will cause the errors your speaking of. You probably noticed you had a huge number of blocked updates, for some reason kpackagekit will block packages incorrectly. I hear they are working on this.

What you need to to do is run the following at the command line

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I had this same issue when trying to upgrade my kubuntu to 4.3

---

### Post by foska on 2009-09-13
Thanx Ms_Angel,

I am actually in the process of doing this right now and  yes I did notice that they were a large number of blocked updates!

I'll be sure to report when the process is completed.

UPDATE:  Everything is work OK now and the solution is actually as per Ms_Angel_D's instructions

---

