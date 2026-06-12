---
title: "Wicd Download issues......"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Nylo on 2008-09-04
Ive had it with NM and am moving to Wicd.  The problem is its not downloading.  Im following the instruction to a tee but I must be doing something wrong.  It says some of the indexes didn't download or its old or it does not exist.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by imdano on 2008-09-04
Right now the repository doesn't have the newest version anyway.  Get the newest version here: [http://wicd.net/latest/changes](http://wicd.net/latest/changes)

---

### Post by Nylo on 2008-09-05
> **imdano said:**
> Right now the repository doesn't have the newest version anyway.  Get the newest version here: [http://wicd.net/latest/changes](http://wicd.net/latest/changes)

Thanks for the link.

Unfortunately it will not load due to the fact Network manager is present. Solution?

---

### Post by imdano on 2008-09-05
You have uninstall network-manager and nm-applet. You can do it with ```
sudo apt-get remove network-manager nm-applet dhcdbd
```

---

### Post by Crafty Kisses on 2008-09-05
Does it give you the exact dependiences or index it is missing.

---

### Post by dodle on 2008-09-05
Make sure you download .deb packages of NM before you uninstall it!  If Wicd doesn't work for you, you won't be able to connect to the internet and re-download NM.  I don't like Wicd, it kept messing up on me.

---

### Post by imdano on 2008-09-05
If you have an ethernet cable you can usually just open a terminal and run ```
sudo ifconfig eth0 up
sudo dhclient eth0
```to get back online.

dodle, do you remember what version of wicd you were using?  And what was messing up?

---

