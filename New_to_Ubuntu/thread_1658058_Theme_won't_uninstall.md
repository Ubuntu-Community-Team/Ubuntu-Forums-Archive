---
title: "Theme won't uninstall"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by jermza on 2011-01-02
I must be doing something wrong.  

**Firstly**, I am really struggling to install themes properly.  I drag and drop the files (when they work) into the Appearance window and they kind of install, but give me messages about icon packs not being installed. I have googled for hours and can not seem to install icons - nothing works.  Please explain to me, in simple terms, how to install icon packs.

Secondly, how do I uninstall the theme in the attached image?  (And why doesn't it allow me to uninstall it?)

---

### Post by Elfy on 2011-01-02
Searching for Faenza icon theme on gnome-look eventually leads to [http://tiheum.deviantart.com/art/Faenza-Icons-173323228](http://tiheum.deviantart.com/art/Faenza-Icons-173323228)

There are installation instructions on the page.

Deleting themes

[http://ubuntuforums.org/showthread.php?t=453879](http://ubuntuforums.org/showthread.php?t=453879)

or if they are not in your home look in /usr/share/themes

---

### Post by jermza on 2011-01-02
> **forestpiskie said:**
> Searching for Faenza icon theme on gnome-look eventually leads to [http://tiheum.deviantart.com/art/Faenza-Icons-173323228](http://tiheum.deviantart.com/art/Faenza-Icons-173323228)

There are installation instructions on the page.

Deleting themes

[http://ubuntuforums.org/showthread.php?t=453879](http://ubuntuforums.org/showthread.php?t=453879)

or if they are not in your home look in /usr/share/themes

Thanks, but I'm not really having much luck.  Is there a way to revert my Appearance to Ubuntu's default (and removing all the installed themes, etc)?

---

### Post by Elfy on 2011-01-02
Do you not see them in either your home or in /usr ?
```

ls /usr/share/themes/
ls .themes
```

As far as I know to reset you remove the extras.

Did you try [http://ubuntuforums.org/showpost.php?p=8177955&postcount=10](http://ubuntuforums.org/showpost.php?p=8177955&postcount=10) ?

---

### Post by jermza on 2011-01-02
> **forestpiskie said:**
> Do you not see them in either your home or in /usr ?
```

ls /usr/share/themes/
ls .themes
```As far as I know to reset you remove the extras.

Did you try [http://ubuntuforums.org/showpost.php?p=8177955&postcount=10](http://ubuntuforums.org/showpost.php?p=8177955&postcount=10) ?

My theme is the Ubuntu default now, but I want to remove all the extras (that I downloaded and installed etc), but don't know how.  How do I do that?

---

### Post by Elfy on 2011-01-02
Have you even looked in /usr/share/themes?

Are they there?

---

### Post by jermza on 2011-01-02
> **forestpiskie said:**
> Have you even looked in /usr/share/themes?

Are they there?
Yes, but I can't delete it.  Won't let me.

---

### Post by Elfy on 2011-01-02
```
gksudo nautilus /usr/share/themes
```

delete the themes you want to remove as root 

should be gone then.

Be careful while in the root nautilus.

As a sidenote - you can only work in the system as root.

Edit - also once you are sure it's worked ok - open nautilus as root again and empty it's trash if you want - things deleted by root will not be in your normal trash.

---

### Post by jermza on 2011-01-02
> **forestpiskie said:**
> ```
gksudo nautilus /usr/share/themes
```delete the themes you want to remove as root 

should be gone then.

Be careful while in the root nautilus.

As a sidenote - you can only work in the system as root.

Edit - also once you are sure it's worked ok - open nautilus as root again and empty it's trash if you want - things deleted by root will not be in your normal trash.

Thank you very much.  I removed the extra themes.  Excuse my ignorance, but, how do I remove the icon sets?  I looked in the icon folder and didn't see them.

Also, what is "nautilus"?

---

### Post by Elfy on 2011-01-02
> **jermza said:**
> Thank you very much.  I removed the extra themes.  Excuse my ignorance, but, how do I remove the icon sets?  I looked in the icon folder and didn't see them.

Also, what is "nautilus"?

No real idea I'm afraid without searching for it - you could do the same I suspect ;)

Nautilus is the file manager. [http://live.gnome.org/Nautilus](http://live.gnome.org/Nautilus)

---

