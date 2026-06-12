---
title: "Xubuntu: Install without losing Gnome?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by James1293 on 2010-05-28
Hello,
I was planning on trying xubuntu (xfce?). I've found a few different suggested forms of installation.

Which package/command should I install/execute in order to have a choice between gnome and xfce when I boot ubuntu?

Thanks!

---

### Post by atomizer on 2010-05-28
You can install xubuntu-desktop from synaptic. It will install the whole xubuntu desktop with programs like abiword and pidgin and so on.

You also can install the meta-package xfce4.

This will install a minimal desktop.

You can choose between Gnome and Xfce in your login screen.
When you click your username there will appear a session menu.

---

### Post by James1293 on 2010-05-30
Thanks!
When I tried to install "xubuntu-desktop" package, it said it was going to uninstall some other packages. Why would that be?

EDIT: formaldehyde_spoon, the meta package worked, and didn't remove anything. Thanks for the input!

---

### Post by formaldehyde_spoon on 2010-05-30
I don't know what/why it said packages will be removed, but I installed Xubuntu on an Ubuntu machine yesterday.

You won't lose Gnome, but your boot up will forever look like Xubuntu instead of Ubuntu (that's fine by me, I prefer it) and bear in mind that it is a little more work to **remove** Xubuntu than it is to install it.
apt-get remove xubuntu-desktop will not work.

Also in Gnome I now have the option to open directories with the Xubuntu file manager.

---

