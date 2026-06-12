---
title: "[SOLVED] edit rclick desktop menu"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Ben Page on 2008-12-30
Hey!

Don't know where to post this, but since im a beginner the absolute beginner thread seemed right to me.

I would like to change the right click (on) desktop menu. I would like to add a terminal icon (shortcut) to the menu, mint or suse style, so I can open terminal via right click in any folder (and terminal path would be in that folder).
Also, I would like to add delete option in menu, not just move to garbage, but real delete function (without garbage bin). In Windows I dont even have recycle bin, so now this mooving and then deleting thwice is just annoing...:mad:

Also, how to put the home folder on the desktop? When I try dragging and droping it tries to copy the whole folder, I want a shortcut of home folder on my desktop..how to do this? Mint had that app witch edited this, but ubuntu doesent :(

---

### Post by wizard10000 on 2008-12-30
> **Ben Page said:**
> Hey!

Don't know where to post this, but since im a beginner the absolute beginner thread seemed right to me.

I would like to change the right click (on) desktop menu. I would like to add a terminal icon (shortcut) to the menu, mint or suse style, so I can open terminal via right click in any folder (and terminal path would be in that folder).
Also, I would like to add delete option in menu, not just move to garbage, but real delete function (without garbage bin). In Windows I dont even have recycle bin, so now this mooving and then deleting thwice is just annoing...:mad:

Also, how to put the home folder on the desktop? When I try dragging and droping it tries to copy the whole folder, I want a shortcut of home folder on my desktop..how to do this? Mint had that app witch edited this, but ubuntu doesent :(

Here's how to make the right-click terminal thingie -

[http://ubuntuforums.org/showthread.php?t=104408](http://ubuntuforums.org/showthread.php?t=104408)

Nautilus already has an option to bypass the trash - if you look at Edit --> Options you'll see it.

On the home folder on the desktop?  Easiest of all - nautilus defaults to your home folder so just create a launcher that calls nautilus - no other command line options needed.

Good luck -

---

### Post by Ben Page on 2008-12-30
Thnx for fast reply, I get the first two, but I cant seem to find nautilus :oops:
Where is it installed, or what command do I need to write in the launcher?

---

### Post by rbc on 2008-12-30
Just right-click on the desktop, choose Create Launcher. The kind of launcher will be defaulted to Application. Leave it as it is. Name it whatever you want. For the command, simply type “nautilus” (without the quotes). You don’t need to enter anything in the Comment field. Click on the Close button. An icon should appear on the Desktop. Click on it and it should open your Home directory.

---

### Post by Ben Page on 2008-12-30
Everything is the way I want it now! :D

Thnx guys!

Don't want to open a new thread just for this...I would like to know is it posible to make a shortcut, windows stile, on the desktop? I managed to drag and drop shortcuts of my host folders etc. on the taskbar, but is it posible to make a classic shortcut, and also, I would like to apply custom icons for those...any clues?

---

### Post by wizard10000 on 2008-12-30
> **Ben Page said:**
> Everything is the way I want it now! :D

Thnx guys!

Don't want to open a new thread just for this...I would like to know is it posible to make a shortcut, windows stile, on the desktop? I managed to drag and drop shortcuts of my host folders etc. on the taskbar, but is it posible to make a classic shortcut, and also, I would like to apply custom icons for those...any clues?

Same way you created the launcher for nautilus  :)

When you create the launcher you'll see a little icon with a spring on it - if you click on that you'll get a picker to select different icons.

---

### Post by Ben Page on 2008-12-30
Every launcher I create says that there is no file or directory that im looking for, inspite of me typing the correct path in the launcher.

But never mind I found another way! Just right click on the file or directory and choose "link", and then move link to desktop!

And I did not realize that superubuntu has installed "ubuntu tweak app by default, almost everything I need is there...

Nevertheless Thnx for the replies!

---

### Post by xjcannonx on 2008-12-30
you can also add a home icon to your desktop by opening gconf-editor and navigate to apps-->nautilus--> and somewhere in there(sorry im not at my machine and its a lil foggy right now...anyway it will say something like "show home icon on desktop" you won't have a 'shortcut' emblem on your home icon this way

---

