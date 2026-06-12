---
title: "Right click &quot;set as desktop background&quot;"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-25
:guitar:How to bring that windows rt. click option in ubuntu? By default ubuntu requires one double click, then two more clicks to set a picture as background....thats not fair....;)

---

### Post by tajiknomi on 2010-11-25
[SIZE=2]Perhaps it may be in Mavrick by Default..what happens when you right-click on a desire picture to set as a desktop background....[/SIZE]

---

### Post by aeiah on 2010-11-25
use nautilus-actions to add any action to the right click menu in nautilus (assuming you're using the normal edition of ubuntu).

thunar (xubuntu) has custom actions as well, but that has the functionality you want out of the box anyway.

in nautilus actions, the command you want is
```

gconftool-2 -t str --set /desktop/gnome/background/picture_filename %M

```

the %M passes the selected file as an argument to the command. in this case, the picture you've selected. you can define when you want this menu entry to appear and stuff quite easily with nautilus-actions (ie, only appears if the selected file is an image)

---

### Post by dhiman33 on 2010-11-25
There's no such option and it's a real shame for ubuntu[-(.I've to open the picture in image viewer and then set it as background.:frown:

P.S.--that was tajiknomi's answer,o.k aeiah i'll try ur method....

---

### Post by dhiman33 on 2010-11-25
Nothing happens, aeiah----in the path I typed the line....still nothing happens.

---

### Post by aeiah on 2010-11-25
sorry, my fault. the command isnt 'conftool' its 'gconftool'. ive edited my above post now

---

### Post by yetiman64 on 2010-11-25
```
sudo apt-get install nautilus-wallpaper
```this puts the option in the right click menu as you want it. Enjoy your wallpaper just like in the other OS you mention :)

Edit: you will find it in the section just above Properties at the bottom of the context menu.

---

### Post by dhiman33 on 2010-11-26
:-PThnks for the replies,guys. I first tried aeiah's method-- went to nautilus actions, typed *.jpg for the condition, and in the path typed the line given. Now after restarting nautilus, when I rt. click a picture and select set as wallpaper... my background becomes black!!:shock: So I discarded that method...(do tell me aeiah if I had to put something in parameters or if u think I made some mistake.:oops:) Then I tried yetiman's method.... it was sure to work as the "nautilus-wallpaper" was already shown in the software center and yes it worked flawlessly:biggrin:... I just had to restart nautilus by "nautilus -q". So cheers:guitar:, Yetiman... and all who followed this thread:KS, I'm now marking this as solved...

---

