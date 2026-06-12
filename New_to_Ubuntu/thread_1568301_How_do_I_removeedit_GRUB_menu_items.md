---
title: "How do I remove/edit GRUB menu items??"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Mik3NC on 2010-09-05
Hi, this is basically what I am wanting to do:

[IMG]http://i52.tinypic.com/iqk3u8.png[/IMG]

The things I'm wanting to remove, I have other ways to access them, so I don't have to worry about them not being on the list.

If someone reading this could please give me simple instructions on how to do this, that is specific to what I'm wanting to remove, I would really appreciate it. This is something I'm dying to do. Thanks.

---

### Post by jtarin on 2010-09-05
What exactly did you want to remove? There are several ways to approach this.

---

### Post by Mik3NC on 2010-09-05
Thanks for responding, jtarin. I'm wanting to remove memtest86+ & memtest86+ (serial console), and Windows Vista (loader).

---

### Post by uncleV on 2010-09-05
These things are stored in the file /boot/grub/grub.cfg.

Make a copy for backup and edit this file with administrator privileges.
You'll find there the sections which are to be deleted or re-ordered. Be careful.
After saving the file restart...
Cross fingers... ;)

If things going good do the following:
[http://ubuntuforums.org/showthread.php?t=1547193](http://ubuntuforums.org/showthread.php?t=1547193)
Reply #6.

If things going bad rename (booting from LiveCD) the backuped file to grub.cfg back and come here again ;)

---

### Post by Elfy on 2010-09-05
To stop memtest entries

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

To remove the vista/win7 recovery entry - look here [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) for section 4

To use win7 as the default you can use GRUB_DEFAULT or GRUB_SAVEDEFAULT - [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Edit - when you edit any grub files you must run ```
sudo update-grub
```

---

### Post by jtarin on 2010-09-05
Open a terminal and make you way to the /boot directory
```
cd /boot
```Once there issue the command ```
ls
```this will list all the files in that directory.
In the terminal issue the command ```
sudo chmod -x 20_memtest86+
```
It will no longer be executable and won't be read into the grub.cfg file the next time you update GRUB.

So then we update Grub2
```
update-grub
```you should not see it on next boot.



Edit:It can be done in either location, but for best practices edit the file in /etc/grub.d

---

### Post by krimzonstarr on 2010-09-05
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
Grub 2 Basics thread, very well written and exactly what you are looking for.

---

### Post by amol_free on 2012-01-03
First type Sudo nautilus in the terminal.
A window will open the goto /boot/grub/grub.cfg.
There you will find all the menu list just change the order or delete it from grub.cfg.
And you are done

---

### Post by anewguy on 2012-01-04
It also depends on the release of ubuntu you are running - so, what version is your netwook remix?

Older versions of ubuntu that don't use grub2 are easily done - for newer releases that use grub2 the procedure is COMPLETELY different.  So, find your ubuntu release version and post back.

---

### Post by nothingspecial on 2012-01-04
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

