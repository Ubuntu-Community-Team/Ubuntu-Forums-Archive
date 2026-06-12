---
title: "Login window manager (GDM) missing in menu"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by longaster on 2011-01-09
Hello, I'm new to here,

I would like to login as root, but not from terminal(not by sudo...).

On other threads they said that this can be done by going to System>Administration>Login window manager, but I can't find it there- there's only Login screen, but when I open it, it looks differently from how the users described it.

I use Ubuntu 10.10.

Thanks for help.

---

### Post by Rex Bouwense on 2011-01-09
May I ask why you want to log in as root?  You can have root privileges by using sudo.

---

### Post by RJ12 on 2011-01-09
I think the last version to have those options was 9.04, and I don't think you could enable root from there.

---

### Post by longaster on 2011-01-09
Because I can't access some folders and file from Nautilus and other software and I don't want to open some applications with root privilegies and some not- it would be confusing with many opened apps.

---

### Post by QLee on 2011-01-09
[QUOTE=longaster]...
I would like to login as root, but not from terminal(not by sudo...).

On other threads they said that this can be done by going to System>Administration>Login window manager, but I can't find it there- there's only Login screen, but when I open it, it looks differently from how the users described it.
...[/QUOTE]

Not threads on this forum, Ubuntu doesn't allow you to login as root. Where did you see it?

---

### Post by nick_goodfate on 2011-01-09
> **longaster said:**
> Because I can't access some folders and file from Nautilus and other software and I don't want to open some applications with root privilegies and some not- it would be confusing with many opened apps.

if you open for example nautilus with root privileges you can seperate it from regular nautilus by its deferent gtk theme. the root one uses an ugly gray theme.

---

### Post by amsterdamharu on 2011-01-09
It goes against forum policy to explain how to do this so if you need to do this than this is not the place to ask.

Why would you log in as root? If you want to start nautilus or some graphic program as root you can use gksu. For example: press alt + F2 and type
```
gksu nautilus
```You are now running nautilus as root without corrupting your home directory (likely when you use sudo for graphic programs)

If you'd like to start it by the click of a button then add an item on the desktop with gksu yourprogram. 

If you don't like it to ask for a password every time then you could check out a command named visudo (in the terminal) to edit your sudoers file and have it not ask for passwords when starting certain programs.

---

### Post by longaster on 2011-01-09
to QLee: I saw it here: <snip>

---

### Post by longaster on 2011-01-09
Thanks, it's solved now:D.

---

### Post by theozzlives on 2011-01-09
I've been using Ubuntu since Oct. 2007 and never had a reason to login as root.

---

### Post by QLee on 2011-01-09
[QUOTE=longaster]to QLee: I saw it here...[/QUOTE]

That's not this forum and we would appreciate it if you did not post links like that here. It is bad advice for beginners.

---

### Post by Elfy on 2011-01-09
> **longaster said:**
> to QLee: I saw it here: <snip>

[http://ubuntuforums.org/showpost.php?p=9315838&postcount=1](http://ubuntuforums.org/showpost.php?p=9315838&postcount=1)

Forum's policy on root logins.

Specifically

> Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.

Link has been removed. Please do not post it on this forum.

As the thread is solved I have also closed it.

---

