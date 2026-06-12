---
title: "simple desktop customization question"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by baxna on 2009-04-26
Hello,

I just have a very simple customization question. I just upgrade to 9.04 yesterday and am very pleased with it, except that whenever I want to see my Home folder I have to click into a menu. Is there a way to place a shortcut on the desktop? I tried dragging the menu icon to the desktop and it started copying everything over, so I cancelled that. Thanks!

Mike

---

### Post by Saint_ on 2009-04-26
Yo, I'm not sure if this is what you're talking about but you can right click the desktop folder and go to Folder View Settings. From here you can set your desktop to be your /home folder, so your /home directory is displayed on the desktop.

---

### Post by Elfy on 2009-04-26
Do alt+F2 - then run gconf-editor

Navigate to /apps/nautilus/desktop

In the right hand pane tick home icon visible

---

### Post by baxna on 2009-04-26
Well, close. I don't want to change the Home folder's location, just place a shortcut to it on the desktop.

---

### Post by wsonar on 2009-04-26
open a terminal

type gconf-editor

go to

apps/nautilus/desktop

see screen shot

check home folder




I usually use this to remove all the icons from my desktop :)



Forestpixie beat me too it I was tring to get a screenshot :)

---

### Post by Sealbhach on 2009-04-26
easier way above.
.

---

### Post by baxna on 2009-04-26
> **forestpixie said:**
> Do alt+F2 - then run gconf-editor

Navigate to /apps/nautilus/desktop

In the right hand pane tick home icon visible

Thanks! That's a pretty obscure/unknown thing, I had no idea that would have been the steps to take.

---

### Post by Spiritous on 2009-04-26
Right click somewhere free on the desktop... Now go into "Create Launcher"... You have a new window, In this change the TYPE: In the dropdown from Application to >>> Location. In Name just type "home"... for the location put Home/Username.

---

### Post by wizard10000 on 2009-04-26
> **baxna said:**
> Well, close. I don't want to change the Home folder's location, just place a shortcut to it on the desktop.

Easy.

Right-click your desktop and select "Create Launcher".

In the "Name" block, put whatever you want to call the icon.

In the "Command" block, put

nautilus /home/*username*

where *username* is your logon name.

Click OK and you're done  ;)

---

### Post by Sealbhach on 2009-04-26
For any other location, right-click on the desktop and choose "creare launcher" but make the launcher type "Location" and just put in the location in the command part. You can change the icon too, by clicking on the picture.


.

---

### Post by baxna on 2009-04-26
Thanks all for the tips about launchers too! That answers another question I had.

---

