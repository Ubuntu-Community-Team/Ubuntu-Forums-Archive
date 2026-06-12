---
title: "Can't rightclick my desktop"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Dockland on 2011-06-22
Howcome I cant right click on my desktop. Nothing happens at all.

---

### Post by dFlyer on 2011-06-22
You should be able to right click the desktop. Are you on a laptop or desktop computer? If on a laptop have you tried plugging in a usb mouse? If on a desktop have you tried a different mouse? Sometimes they go bad.

---

### Post by Dockland on 2011-06-22
I'm on a desktop. Since a couple of weeks I haven't got any rightclick at all. Nothing happens. Everything else is all right in the system. Just rightklicking on desktop that doesn't work. Strange

---

### Post by dcsoldschool53 on 2011-06-22
System > Preferences > mouse Under General, what is the mouse orientation. Is it right click or left click. If it is left-handed, make it right-handed.

---

### Post by jerrrys on 2011-06-22
i had this same problem, which i blamed on alpha release.  however i tried it again after reading your post and it now works.  so maybe a update fixed it in my case.  are you updated?

---

### Post by Dockland on 2011-06-22
Everything is updated and the mouse works allright i every other application. Strange.

---

### Post by Perfect Storm on 2011-06-22
Have you messing with gconf-editor?

---

### Post by Dockland on 2011-06-22
> **Artificial Intelligence said:**
> Have you messing with gconf-editor?

Not at all.

---

### Post by Perfect Storm on 2011-06-22
> **Dockland said:**
> Not at all.

May be Ubuntu Tweak?
Try see if right click is disable in gconf somehow on Desktop.

<alt>+<F2>
```
gconf-editor
```

apps ==> nautilus ==> preferences


Should look like this for right click on Desktop:
show_desktop [x]
desktop_is_home_dir [_]

---

