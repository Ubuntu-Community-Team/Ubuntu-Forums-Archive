---
title: "Are apps tied to their GUI engine?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by fotonix on 2009-02-25
To provide the OS with a GUI there are Gnome, KDE, XFCE, etc. Let's say I chose Gnome. Can I install and run digiKam which on their webpage seem to only talk about KDE?

Where I'm going: I need a photo app smart enough to rename photos based on their EXIF data. Original on camera: IMG_8945.JPG, my naming convention: 20090225-092314_8945.JPG. Under "that other OS" I was using 'cam2pc' which could do this easily. Anything Gnomish out there?

---

### Post by jakupl on 2009-02-25
> **fotonix said:**
> To provide the OS with a GUI there are Gnome, KDE, XFCE, etc. Let's say I chose Gnome. Can I install and run digiKam which on their webpage seem to only talk about KDE?

Where I'm going: I need a photo app smart enough to rename photos based on their EXIF data. Original on camera: IMG_8945.JPG, my naming convention: 20090225-092314_8945.JPG. Under "that other OS" I was using 'cam2pc' which could do this easily. Anything Gnomish out there?

You can install anything *buntu. There is theoretically a very minor performance decrease if you use kde apps in gnome, but I have never noticed it.

---

### Post by OffAxis on 2009-02-25
yes, the apps can peacefully co-exist on each other's desktop (it's the library dependencies from the other desktop that will have to be downloaded.)

There's also exif-sorter that can do what you want.

[http://www.amok.am/en/freeware/amok_exif_sorter/](http://www.amok.am/en/freeware/amok_exif_sorter/)

---

### Post by Temposs on 2009-02-25
But to answer your question directly...yes, applications are tied to their GUI environment...luckily, installing a KDE program in GNOME will just install the necessary KDE components...so you can run a KDE program in GNOME.

---

### Post by fotonix on 2009-02-25
Fantastic. Thanks!

I was worried that Gnome and KDE were so different as to be completely two camps.  Ah, sweet relief!  And thanks for the link, will definitely check it out.

This forum is SO different to others - quick, friendly answers.

---

### Post by HermanAB on 2009-02-25
Linux is standards based and all window managers adhere to the same standard.  So you can run KDE applications on kdm, or gdm or IceWM or whatever.

For example, the Mandriva Linux distribution offers many desktop systems, Gnome, KDE, IceWM, XFCE and so forth which you can select at start-up and they all use Gnome gdm as the window manager.

Cheers,

Herman

---

