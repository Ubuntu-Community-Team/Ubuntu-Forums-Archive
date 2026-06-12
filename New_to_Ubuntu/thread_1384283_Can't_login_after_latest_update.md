---
title: "Can't login after latest update"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by pocket_andy on 2010-01-18
Hi there,

I'm having some problems logging in after installing an update in 9.10. After entering my password and hitting enter, the splash screen comes up followed by a blank screen, then another splash screen appears, then I am presented with the login page again.

I can login using ctr+alt+f3. "Startx" gives an xauth error and "sudo service gdm restart" brings me back to the login screen.

Any ideas?

---

### Post by lidex on 2010-01-18
Try this at a command prompt:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

### Post by bakerjs on 2010-09-10
I just had this problem and realized it was because my disk space was full.  I then logged in through Ctl-Alt-F3, deleted some large files, and rebooted.  That solved the problem.

---

### Post by Jazzy_Jeff on 2010-09-10
> **bakerjs said:**
> I just had this problem and realized it was because my disk space was full.  I then logged in through Ctl-Alt-F3, deleted some large files, and rebooted.  That solved the problem.

This thread is a little old, don't ya think?

---

### Post by lidex on 2010-09-14
> **Jazzy_Jeff said:**
> This thread is a little old, don't ya think?

Sure. Some just come late to the party. ;)

---

