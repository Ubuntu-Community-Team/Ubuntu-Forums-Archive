---
title: "Mounted drive icons on desktop"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by ozmart2010 on 2010-10-30
Two icons suddenly appeared on the Ubuntu 10.10 desktop (not sure how I did it), one for the Linux partition and one for the Windows partition.I don't really want them there or need them but its not at all obvious how to get rid of them - at least not to me, without inadvertently doing something terrible by mistake.

This probably seems so basic but as a usual Windows user, I'm not sure what I am doing with Ubuntu. Thks.

---

### Post by bioterror on 2010-10-30
> **ozmart2010 said:**
> Two icons suddenly appeared on the Ubuntu 10.10 desktop (not sure how I did it), one for the Linux partition and one for the Windows partition.I don't really want them there or need them but its not at all obvious how to get rid of them - at least not to me, without inadvertently doing something terrible by mistake.

This probably seems so basic but as a usual Windows user, I'm not sure what I am doing with Ubuntu. Thks.

with application gconf-editor.
If you dont have it.. sudo apt-get install gconf-editor 
Then navigate to apps ->nautilus ->desktop
And uncheck what you want.

---

### Post by Quackers on 2010-10-30
To take them off the desktop right-click on them and select unmount.

---

### Post by ozmart2010 on 2010-10-30
Thks. wasn't sure if the 'unmount' thing would do something bad. 

BTW I don't seem to have apps ->nautilus ->desktop. The editor is installed but I cannot see any way of accessing it thru the menu system.

---

### Post by Quackers on 2010-10-30
press Alt and F2 and a box will appear. type in 
```
gconf-editor
```
and click on run

---

### Post by Verbeck on 2010-10-30
you could also try ubuntu-tweak. its easier for new users.
 [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

