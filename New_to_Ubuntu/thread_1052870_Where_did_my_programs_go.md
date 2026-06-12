---
title: "Where did my programs go?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by AllRadioisDead on 2009-01-28
Hi, I'm fairly new to linux, but I've used ubuntu a few times before. However, I'm still not familiar with a few things. I downloaded a few apps via the synaptic package manager, a few installed and I'm not sure what happened to two of them. They didn't appear anywhere on my menu and I don't know where they would be. The two I'm having trouble with is "drapes" and "conky". Thanks!

---

### Post by skymera on 2009-01-28
Run them from the terminal, as far as i know, they don't make entries in the menus

---

### Post by Sealbhach on 2009-01-28
Hi, some apps don't add themselves to your menu when you isntall them.

You can run Conky by opening a terminal and typing

```
conky
```

and press enter. In order for Conky to look really good, you will need a conkyrc file (it's a text file with various display and content settings). I can send you mine if you want but they're easy enough to get.

Conky would be a program you want to start when you log in, so you would add it to your Startup sessions, there's a how-to about how to do all that here:

[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

-----
In general, if you download an app, you can create an entry for it in your menus using the "Main Menu" feature in Preferences.

If you can't find it then install 

```
sudo apt-get install alacarte
```

This will show up in your menu as System/Preferences/Main Menu and you can use this to edit your menus and add shortcuts for apps which don't show up otherwise.


.

---

### Post by GepettoBR on 2009-01-28
> **ihermit said:**
> Hi, I'm fairly new to linux, but I've used ubuntu a few times before. However, I'm still not familiar with a few things. I downloaded a few apps via the synaptic package manager, a few installed and I'm not sure what happened to two of them. They didn't appear anywhere on my menu and I don't know where they would be. The two I'm having trouble with is "drapes" and "conky". Thanks!

Conky is in Applications>System Tools>Conky. I don't use drapes, but the package information says it's a panel applet, so you can add an icon by right-clicking your panel and choosing "Add to panel". Drapes should be in the list.

Like skymera said, you can also run them from the terminal, or by pressing ALT+F2, typing the program name, then hitting Enter.

---

### Post by AllRadioisDead on 2009-01-28
Thanks everyone, this helps a lot. The main menu tool was especially helpfull, and I was able to run my not-so-missing programs. I'm in the process of configuring conky now.

---

