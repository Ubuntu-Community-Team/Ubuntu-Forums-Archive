---
title: "No &quot;Add Application to Panel&quot; option"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Jamppi on 2010-05-22
Hi!

I'm using Ubuntu 10.04. After I had trouble with Compiz making my window decorations disappear and getting them back, I now I can't add any links to the desktop by dragging from Applications menu nor can I add any applications to the top panel. 

Tried everything I could think of, which is not much.

Screenshots:

[IMG]http://i783.photobucket.com/albums/yy119/evore1911/MyScreenshot3.jpg[/IMG]

---

### Post by ipatfrmww on 2010-05-22
Its cause your panels are in lock down, i.e. you cant edit them.
To edit them again you have to untick the setting in configuration editor.

Run gconf-editor in the terminal(or wherever), then go to the key, /apps/panel/global/locked_down. Then untick it. Problem solved.

I have no idea how you got it like that, there is probably a setting in the menus somewhere for it, dont know where. You might have ticked it by accident:confused:.

---

### Post by ipatfrmww on 2010-05-22
Oh I see, there is a setting in Ubuntu tweak for it under gnome settings, panel settings.

---

### Post by Jamppi on 2010-05-22
Thanks! This worked, I'm able to modify my desktop and panel again....

Can't thank enough...

PS. Ubuntu ROCKS!

---

### Post by Johann-1.0 on 2010-08-21
It already appears unchecked, but the behavior is the same. It simply doesn't let me add apps to panel . May you help me, please?
Thank you in advance
Using Ubuntu 10.04

---

### Post by ipatfrmww on 2010-09-14
Explain the differences between the 2 cases for me.  That's probably something different.

---

### Post by Johann-1.0 on 2010-09-14
I mean, when it is checked it behaves in the same way as it hasn't checked: "Add to panel" appears in gray (not able to use it).

---

### Post by ipatfrmww on 2010-09-21
Did you try Ubuntu tweak way aswell?
It seems to be good at fixing that sort of config stuff.

If you don't have Ubuntu tweak you need to add a new ppa for it I think
sudo gedit /etc/apt/sources.list

add this line:
deb **[http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu)** lucid main #Ubuntu Tweak

---

