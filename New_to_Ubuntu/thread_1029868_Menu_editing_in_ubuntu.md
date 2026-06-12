---
title: "Menu editing in ubuntu"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Dravenm4 on 2009-01-03
Hello and happy new years all!!!

Hello I am a noob to linux and I am trying to figure out how to add app's to the applications menu. Well really I know somewhat ow to add them by edit menu opt. but I don't know how to use the launcher?

Any and all help will be appreciated..

Draven :D

---

### Post by adult swim on 2009-01-03
to use the launcher, you have to make a new one.  say you wanted to make one for a terminal.  for the box Name: you could write in terminal (really you can write in anything you want here.)  for the command box youll need to write the command that is responsible for launching a terminal, gnome-terminal (this step has to be exact, you can also browse to the executable file with the box to the right.)  finally for commment you can write in whatever you want.

---

### Post by Darkade on 2009-01-03
Ok you should have a window like this (Check attachment) First of all you have

Type:
>Application: It's an app, say firefox, pidgin, a game
>Application in terminal: It's a script that runs in terminal. Like a bash or python script
>Location: it's a dir in your computer

Name: is what will show up in the menu

Command: you can write a command here. e.g. ```
 gedit /etc/X11/xor.conf
``` (this command will show you yor xorg config file. You shouldn't open it as admin, here it's ok because you're opening it as an user, and even if you modify it you won't be able to save it)
you can also browse for an app, most of them are in /usr/bin and for games in /usr/games

Comment is just a wider description you can add

You can choose an icon for the launcher by clicking in the left button. However if you choose a "known" command an icon will probably be selected for you

---

### Post by Dravenm4 on 2009-01-04
Thank you guys very much

---

