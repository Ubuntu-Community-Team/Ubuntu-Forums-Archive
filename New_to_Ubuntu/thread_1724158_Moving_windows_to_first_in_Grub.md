---
title: "Moving windows to first in Grub?"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by djm227 on 2011-04-08
Hi all,

I am selling this crappy netbook I have tomorrow to some guy from craigslist.  I installed Ubuntu on it, thought I used Wubi, but apparently I messed it up and did a full install by accident.

I don't have time to mess around with uninstalling Ubuntu and restoring XP, so I'm just trying to make this as painless as possible for this guy, and move XP to the first thing on the Grub list.

I googled this, and something said to run "sudo gedit /boot/grub/menu.lst" and edit the list, but that command returns nothing in 10.10.  Can anyone help me move XP to first in grub?

---

### Post by cheapie on 2011-04-08
It's /boot/grub/grub.cfg ever since 10.04 for upgrades and since 9.10 for clean installs.

---

### Post by Paqman on 2011-04-08
If you install startupmanager you can change the default OS without having to mess about with text files.

---

### Post by garvinrick4 on 2011-04-08
+1 with paqman:  if you do not know how to change in  /etc/default/grub and update just download the startupmanager in GUI
* Should learn how to work with /etc/default/grub at one time or another though*
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

---

### Post by Hedgehog1 on 2011-04-08
To get windows in the first physical position in the grub menu on 10.10, do these two steps:

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

```
sudo update-grub
```

When you reboot, Windows appears before Ubuntu in the grub menu, and will do so from now on.


***The Hedge***

:KS

---

### Post by djm227 on 2011-04-08
Thanks guys, I edited the file to change the timeout to 1 second, and used Hedgehogs method to change the boot order.  I would of used startupmanager, but the wireless card in this needs a driver.

With one second timeout and windows at the #1 spot, it shouldn't even be noticeable.  I'll still let the guy know it's on there, but at least this way it's no extra work for him to get to Windows.

---

### Post by Dutch70 on 2011-04-08
Shoulda left it at 10 and charged him extra for Ubuntu ;) ...lol j/k.

---

### Post by djm227 on 2011-04-08
> **Dutch70 said:**
> Shoulda left it at 10 and charged him extra for Ubuntu ;) ...lol j/k.

lol I was thinkin about it.

---

### Post by garvinrick4 on 2011-04-08
In upper right of your thread in thread tools mark as solved please.

---

