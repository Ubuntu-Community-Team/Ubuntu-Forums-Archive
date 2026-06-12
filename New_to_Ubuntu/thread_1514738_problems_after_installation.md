---
title: "problems after installation"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by ueber3ber on 2010-06-21
Hi,

my computer was fresh installed a few days ago and I experience a few problems...sure, I can reinstall it but I want to have a closer look, at least to learn something.

1) gnome panel is not starting after boot, I have to do so manually with "sudo debconf gome-panel" but then the user "root" is shown in the panel, although "whoami" shows "my" user

2) each installation comes up with the error that something like "man-db" cannot be installed and/or forund

3) firefox shows "(firefox-bin:1838): Gdk-WARNING **: XID collision, trouble ahead" in the terminal while running (that seems to be a firefox bug)

What would you suggest to do? I dont need detailed step-by-step help but a few sources/links would be helpful!

Thanks a lot...

---

### Post by mbzn on 2010-06-21
> **ueber3ber said:**
> Hi,

my computer was fresh installed a few days ago and I experience a few problems...sure, I can reinstall it but I want to have a closer look, at least to learn something.

1) gnome panel is not starting after boot, I have to do so manually with "sudo debconf gome-panel" but then the user "root" is shown in the panel, although "whoami" shows "my" user
[INDENT]Try entering the command without sudo, if that works then just add that same command under startup applications[/INDENT]

2) each installation comes up with the error that something like "man-db" cannot be installed and/or forund
[INDENT]This could be an error on the cd you install from, it might have a read error on the man files, try writing the cd at slower speed[/INDENT]

3) firefox shows "(firefox-bin:1838): Gdk-WARNING **: XID collision, trouble ahead" in the terminal while running (that seems to be a firefox bug)
[INDENT]For this i can only suggest updating or reinstalling firefox[/INDENT]

What would you suggest to do? I dont need detailed step-by-step help but a few sources/links would be helpful!

Thanks a lot...

Hope it'll help

---

### Post by ueber3ber on 2010-06-21
Hi,

you made my day with your quick reply, quite boring today ;-)

1) I tried so, it cames up with a couple of denied permissions but I will give permissions manually

2) I checked the CD with the MD5 and this looked good, I could imagine that the it was not read properly

3) Will do so, sounds sensful....

Thanks a lot...

---

### Post by sandyd on 2010-06-21
3. the problem is fixed in firefox 3.6.4+
oh, and -> [http://ubuntuforums.org/showthread.php?p=7506398](http://ubuntuforums.org/showthread.php?p=7506398)

---

### Post by lkjoel on 2010-06-21
For gnome panel not working, just try this command in a Terminal window (Applications->Accessories->Terminal)
```
sudo ln /usr/bin/gnome-panel /boot/gnome-panel
sudo ln /usr/bin/gnome-panel /etc/init.d/gnome-panel
```
That should do it for Gnome-Panel.

---

### Post by ueber3ber on 2010-06-21
anscheißen! its working! :D

---

### Post by ueber3ber on 2010-06-24
Ok,

my gnome -panel is still not working probably

```
bgi@bgi:~$ debconf gnome-panel
Cannot register the panel shell: there is already one running.
```

Any suggestions?

Thanks guys...

---

### Post by lkjoel on 2010-06-27
If you want to stop the gnome panel, do this
```
killall gnome-panel
sudo killall gnome-panel
```

---

