---
title: "Duel boot first preference win xp"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-08
Hi ,
 
My system duel boot (ubuntu and Xp) while turn on the cpu power by defult lts loading ubuntu if we want to choose xp we should select the xp(by using arrow keys with in time peroid) which is in the last option,
 
I would like to set windows xp as defult operating system to avoid confusion to family members.
 
 
Pls advise.............

---

### Post by freak42 on 2010-06-08
edit the grub menu settings
by hitting

alt-f2 and enter:
gksudo gedit /boot/grub/menu.lst



modify the 'default' setting to match your xp entry:
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved

---

### Post by nhasian on 2010-06-08
you can also use [URL="apt:startupmanager"]startupmanager
[/URL]
```
sudo apt-get install startupmanager
```

---

### Post by wilee-nilee on 2010-06-08
> **nhasian said:**
> you can also use [URL="apt:startupmanager"]startupmanager
[/URL]
```
sudo apt-get install startupmanager
```

I would use this, without knowing if the user is using grub-legacy or grub2 grub/menu.list=legacy that makes no sense.

---

### Post by nhasian on 2010-06-08
it works with grub2 as well.

> **wilee-nilee said:**
> I would use this, without knowing if the user is using grub-legacy or grub2 grub/menu.list=legacy that makes no sense.

---

### Post by wilee-nilee on 2010-06-08
> **nhasian said:**
> it works with grub2 as well.
 I was agreeing with you I think you miss read my post the grub.list is only applicable to grub-legacy. Hey I miss read posts all the time.;)

---

### Post by maestrobwh1 on 2010-06-08
You could also do

```

sudo mv /etc/grub.d/30_os-prober /etc/grub.d/07_os-prober
sudo update-grub

```

This just moves and runs the os-prober that finds Windows and puts the entry BEFORE the linux kernels are found and placed in your list and pretty much leaves your system intact.  You can always move it back to "30" if you change your mind.

---

### Post by karthick87 on 2010-06-08
StartupManager works fine in grub2

---

### Post by wilee-nilee on 2010-06-08
> **getyourkarthick said:**
> StartupManager works fine in grub2

It is what I use.

---

