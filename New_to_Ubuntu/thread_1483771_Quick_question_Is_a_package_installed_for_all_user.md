---
title: "Quick question: Is a package installed for all users?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Vostrocity on 2010-05-15
When you install a package, does the corresponding app become available for all users (and show up in the Ubuntu menu)?

---

### Post by Mitchell Hale on 2010-05-15
Yes. All users can access the app. Regardless as to if you use .deb files, synaptic, software center, etc.

---

### Post by Vostrocity on 2010-05-15
But they would be different instances of the same app? For example saved passwords in Firefox wouldn't be shared? I've been using Ubuntu for a while but I this is my first time installing it on a multi-user computer so I'm a bit of a noob.

---

### Post by Ozymandias_117 on 2010-05-15
Firefox will create a folder in your home folder called .mozilla and keep all your preferences, bookmarks, saved passwords etc. there.

---

### Post by BoneKracker on 2010-05-15
Depending on the desktop environment (gnome/kde) or window manager that you are using, there are ways of controlling what "shows up".

If you're using Gnome, for example, you can use an administrative application called Pessulus to "lock down" users (restricting what applications and what administrative options they have access to).

[http://www.linux.com/archive/feed/62060](http://www.linux.com/archive/feed/62060)

You can also manually edit an individual user's gconf settings (gnome's equivalent of a "registry") which is the mechnism used by such tools.

This may be more broadly applicable to both Gnome, KDE and Xfce, as a "freedesktop.org" standard, but I'm not sure.

(Of course, gnu/linux itself has user and group permissions which can also be used to control what users have access to, and there are more detailed tools as well (access control lists, role-based access control lists, context-based access control, etc.)

---

### Post by WinterRain on 2010-05-15
> **Vostrocity said:**
> For example saved passwords in Firefox wouldn't be shared? 

No, they won't be shared. Each user has it's own home folder, and that's where config files are kept.

---

### Post by Vostrocity on 2010-05-15
Thanks guys. I understand this now.

---

