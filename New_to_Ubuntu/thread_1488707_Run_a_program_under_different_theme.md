---
title: "Run a program under different theme?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by df0xyd on 2010-05-20
Hey guys and gals!

This is probably a dumb question...

Anyways, I have installed [Wii-Black]("http://gnome-look.org/content/show.php/Wii-Black?content=45829") as my theme for Ubuntu.  It looks really neat for a lot of programs like Geany.  Unfortunately, for others like Open Office (PowerPoint), it turns all the slides gray, and when going to do a sideshow, it looks terrible.

Now, my question is:  Can I run a program under a different theme than what I have as my default?  Like forcing Open Office to run under human..?

Thanks!
-Frosty Fox  =^_^=

---

### Post by blazemore on 2010-05-21
You could set up a new user, set the theme for that user, and use the "su" command to run a program as that user.

---

### Post by df0xyd on 2010-05-22
> **blazemore said:**
> You could set up a new user, set the theme for that user, and use the "su" command to run a program as that user.

Thanks for the suggestion!

I did as you said and created a user, and left the default theme for them. Proceeded to use the su command and run a program, but I ran into a problem...


```
frosty@arctic:~$ su programmer
Password: 
programmer@arctic:/home/frosty$ geany 
No protocol specified
Geany: cannot open display
programmer@arctic:/home/frosty$ 
``````
frosty@arctic:~$ gksu -u programmer geany
No protocol specifiedGeany: cannot open display

frosty@arctic:~$ 
```
I think it's because su doesn't let the user use my X? I'm not sure... I'm not really a pro at ubuntu.. I can just get around...

---

### Post by sisco311 on 2010-05-22
In case of oo edit the /usr/bin/ooffice file:
```
gksu gedit /usr/bin/ooffice
```
to:
```
#!/bin/sh
[color=green]export SAL_USE_VCLPLUGIN=gen[/color]
/usr/lib/openoffice/program/soffice  "$@"
```

In case of other applications you can set the theme by changing the value of the  GTK2_RC_FILES variable, i.e.:
```
GTK2_RC_FILES="/usr/share/themes/Human/gtk-2.0/gtkrc" gedit
```

---

### Post by df0xyd on 2010-05-22
> **sisco311 said:**
> In case of oo edit the /usr/bin/ooffice file:
```
gksu gedit /usr/bin/ooffice
```to:
```
#!/bin/sh
[COLOR=green]export SAL_USE_VCLPLUGIN=gen[/COLOR]
/usr/lib/openoffice/program/soffice  "$@"
```In case of other applications you can set the theme by changing the value of the  GTK2_RC_FILES variable, i.e.:
```
GTK2_RC_FILES="/usr/share/themes/Human/gtk-2.0/gtkrc" gedit
```

That works out, super awesome! Thank you soo much! ^^

But! I have one last question! The GTK2_RC_FILES variable works awesome if I'm launching from a terminal. Unfortunately, that does not affect the Applications menu. Is there any way I can change that or should I just create a alias under .bashrc that just screens the program and ignore the applications menu?

---

### Post by sisco311 on 2010-05-22
> **df0xyd said:**
> That works out, super awesome! Thank you soo much! ^^

But! I have one last question! The GTK2_RC_FILES variable works awesome if I'm launching from a terminal. Unfortunately, that does not affect the Applications menu. Is there any way I can change that or should I just create a alias under .bashrc that just screens the program and ignore the applications menu?

You have to edit the command field of the launcher. Right click on the menu -> Edit Menus ->  Highlight the item -> Properties and edit the command field to something like:
```
bash -c "GTK2_RC_FILES="/usr/share/themes/**Theme**/gtk-2.0/gtkrc" **original-command**"
```

---

### Post by df0xyd on 2010-05-22
> **sisco311 said:**
> You have to edit the command field of the launcher. Right click on the menu -> Edit Menus ->  Highlight the item -> Properties and edit the command field to something like:
```
bash -c "GTK2_RC_FILES="/usr/share/themes/**Theme**/gtk-2.0/gtkrc" **original-command**"
```

Thank you very, very much sisco311!

Problem is [SOLVED]  =^_^=

---

### Post by Rendsvig on 2011-03-25
I too thank for the above solution. I used to change the colors in the Opera browser when using a dark theme -- with a white/light text color making a reply on a comment on facebook (etc.) would otherwise be unreadable.

---

### Post by sisco311 on 2011-03-25
You are welcome!

---

