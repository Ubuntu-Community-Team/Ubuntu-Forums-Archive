---
title: "lxde OB menu"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-23
Posted this in a previous thread ([http://ubuntuforums.org/showthread.php?t=1460754)but](http://ubuntuforums.org/showthread.php?t=1460754)but) marked it as solved.
Wanted to have a custom openbox menu in lxde.
So,I changed the openbox script in /etc/X11/openbox/menu.xml but the default one keeps running,as if it's hardcoded or something.Perhaps I have to edit another file as well?

---

### Post by Jon Monreal on 2010-04-25
This may sound like a silly question, but have you tried restarting?

---

### Post by dzon65 on 2010-04-25
> **Jon Monreal said:**
> This may sound like a silly question, but have you tried restarting?

Yes I did.Didn't work.I'm having a lot of probs with minimal/lxde,I mean a lot.So,kept the lxde core but switched to openbox.

---

### Post by Jon Monreal on 2010-04-25
Okay, try ~/.config/openbox/menu.xml for an individual's user menu or /etc/xdg/openbox/menu.xml to edit the menu for all users.

Take a look at [this page]("http://openbox.org/wiki/Help:Menus") for more information.

---

### Post by Jose Catre-Vandis on 2010-04-25
Have you installed obmenu, this will help you create a menu graphically, as opposed to working through the xml. Also, menumaker will create a menu of all your installed apps

---

### Post by dzon65 on 2010-04-25
For some reason lxde never worked as it is supposed to do in this minimal 9.10 install.Perhaps that it worked better in 9.04,don't know.I posted many of the issues on the forum such as 1)no way to set applications as default (the option simply wasn't there)2)no picture thumbnails3)transparency issues with the lxpanel (disformation)even with a sleep added to the start file.In order to work normally I had to install thunar.
I had some slitaz installs and the issues didn't occur there,on the contrary.Anyway,decided to do a minimal install and only use the OB session.I'm not the only one having experienced those probs with lxde,found a lot of people complaining about it.Perhaps the issues will be solved in 9.10 but to me,as far as my old low spec pc's go,lxde will only be installed as a base.That is,until there's dutch support in slitaz.As a base and running openbox session.Oh btw,everything works fine in OB.
Thanks for all replies.
Kind regards,J.

---

