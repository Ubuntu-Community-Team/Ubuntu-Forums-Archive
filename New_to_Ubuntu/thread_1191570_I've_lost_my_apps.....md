---
title: "I've lost my apps...."
date: 2009-06-19
forum: New to Ubuntu
---

### Post by 22david55 on 2009-06-19
[FONT=Arial Black][SIZE=4]**[COLOR=Blue]Lost Apps????[/COLOR]**[/SIZE][/FONT]

Help...I'm a newbie to Ubuntu but have used Linux in the past. I've used the package installer to install some 3rd party apps but they don't appear in my menu items. :sad:Where are they and how can I get them into my menus??

Someone please help...

:confused:

---

### Post by idef1x on 2009-06-19
Do you have an expample? What distribution do you use? Ubuntu or Kubuntu?
Some programs doesn't add the menu items and most likely that's the case with 3th party apps, so you have to add them manually in the menu.

---

### Post by nothingspecial on 2009-06-19
Which 3rd party apps?

---

### Post by tarps87 on 2009-06-19
If it is command line based it won't show in the apps menu. Try
```
whereis *AppName*
```
or just typing the apps name into the terminal.

If this works you can add a menu item (assuming you are using gnome) by right clicking the menu bar bit (in other word where it says applications) now edit and new item and fill in the boxes

Edit: Do not run the app with sudo unless you know what the app does and it is absolutely necessary

---

### Post by Chesamo on 2009-06-19
Go to System > Administraton > Software Sources.
Under "Third-Party Software", check the first box.

You should see your programs now.

EDIT: Sorry, I thought you meant you couldn't find them in the Add/Remove Programs applet. I should read posts more carefully.

System > Preferences > Main Menu is where you want to look.

---

### Post by gradinaruvasile on 2009-06-19
> **22david55 said:**
> [FONT=Arial Black][SIZE=4]**[COLOR=Blue]Lost Apps????[/COLOR]**[/SIZE][/FONT]

Help...I'm a newbie to Ubuntu but have used Linux in the past. I've used the package installer to install some 3rd party apps but they don't appear in my menu items. :sad:Where are they and how can I get them into my menus??

Someone please help...

:confused:

What packages did u install ? If the programs are command line ones, there will be no menu item. 
The same goes for most www apps (i mean those that use a web server).

Another thing that happened to me sometimes: i install something that should have a menu entry but it doesnt show up there. I opened the menu editor in a terminal:

```
alacarte
```

And i searched for the app on the menu list. I found their menu entries, unticked them and waited until the name becomes bold then ticked back again then closed the menu editor. Then i could use them. Maybe you should try it.

---

