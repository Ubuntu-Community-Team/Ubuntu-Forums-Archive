---
title: "removing windows xp from dual boot?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by aint_no_einstein on 2009-12-02
Is there any way of dual booting Ubuntu with Windows XP and then removing XP entirely, so that Ubuntu is my only OS?

---

### Post by halj32 on 2009-12-02
the easy way is to install a grub editor, then remove XP from the list. remember to make a backup first incase you want to restore

---

### Post by aint_no_einstein on 2009-12-02
thank you for the quick reply. 
Will that work if I used wubi to install Ubuntu?

---

### Post by QIII on 2009-12-02
If you used Wubi, read here:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I cannot vouch for it, since I have never done it.

However, this has been recommended by others.

The other option is to do a complete install from the LiveCD.  Save all of your important data first!

---

### Post by presence1960 on 2009-12-02
> **aint_no_einstein said:**
> thank you for the quick reply. 
Will that work if I used wubi to install Ubuntu?

that will not work because when you install via wubi the Ubuntu entry is added to windows xp boot.ini or another file in Vista. So when you get the menu to choose windows or Ubuntu that is a windows file not GRUB. If you want Ubuntu as your sole OS do what QIII said to do!

---

### Post by aint_no_einstein on 2009-12-02
Could I download Ubuntu onto the computer using an external hard drive instead of a cd and then be able to remove windows?

---

### Post by QIII on 2009-12-02
As I understand it, Wubi installs Ubuntu in it's own folder (with virtual partitions) and runs in what is known as a "loop device".  That allows it to be mounted as if it were really on its own device (with certain provisos and caveats).

If you were to simply "uninstall" Windows right now, you'd blow away that folder and take out your Wubi-installed Ubuntu.

As I said above, you should either use the instructions at the site I provided or install Ubuntu as a stand-alone system.

If you want to install it as a stand-alone system, save all your important files.  The easiest path from there would be to download the .iso from Ubuntu,  burn the .iso to CD and use the LiveCD to do a clean installation.

---

