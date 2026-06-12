---
title: "Remove drive icons on my desktop"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by syntr on 2010-11-06
Okay, I just installed Ubuntu through Wubi on an HP Mini 110-3030NR.

And I get these icons on my desktop:
[http://img179.imageshack.us/img179/2631/screenshotyr.png](http://img179.imageshack.us/img179/2631/screenshotyr.png)

I'm afraid to unmount them, because I don't really know what they are. Also, I don't want to unmount them every time.

I just don't want the icons showing up on my desktop.

Help? :)

---

### Post by tajiknomi on 2010-11-06
[SIZE=2]When drives are mounted, these will let icons on Desktop & don't afraid of **unmounting** them,
just right click on them and select unmount option..

Ubuntu by **default shows mount-drives** on Desktop (e.g, HD,Usb Ex-hdd etc)
[/SIZE]

---

### Post by 4ll41 on 2010-11-06
Most possibly they are partitions on hard drive.

Try this one:

Hit  ALT+F2 and type gconf-editor

Then open apps-->nautilus-->desktop and uncheck the volumes_visible sentence. Is it ok?

---

### Post by syntr on 2010-11-06
> **tajiknomi said:**
> [SIZE=2]When drives are mounted, these will let icons on Desktop & don't afraid of **unmounting** them,
just right click on them and select unmount option..

Ubuntu by **default shows mount-drives** on Desktop (e.g, HD,Usb Ex-hdd etc)
[/SIZE]

How do I make it so that I don't have to do this every time that I boot Ubuntu?

---

### Post by syntr on 2010-11-06
> **4ll41 said:**
> Most possibly they are partitions on hard drive.

Try this one:

Hit  ALT+F2 and type gconf-editor

Then open apps-->nautilus-->desktop and uncheck the volumes_visible sentence. Is it ok?

Awesome. Thanks :D

---

### Post by 4ll41 on 2010-11-06
U r welcome! However, let me tell you that with this option nautilus does not show any icon on the desktop of any volume of the pc.






P.S. Edit your thread as "solved" if you found what you was looking for

---

### Post by patrickscott on 2010-11-14
Thanks! Your instructions removed the New Volumes from my desktop!

---

### Post by Dalle85 on 2010-11-25
*** edit ***

Never mind - please delete me

---

