---
title: "SSHMenu installed, not an option to add to panel though"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by InkyDinky on 2009-05-14
I installed SSHMenu and was planning on adding it to my deskbar panel however it doesn't show up as an option in the "add to panel" popup list! I can run sshmenu from the command line and it pops up in its own window with no problems.  So how do I add it to the panel? I tried adding it as a "custom application launcher" but that runs it separately like the command line.


Is there any reason why installing it wouldn't add it to the "Add to panel" menu? I've tried removing and reinstalling to no avail.

I did upgrade from Hardy to Jaunty FWIW.
I know I've gotten it running on another (x64) upgraded to Jaunty box.  Just curious why it is misbehaving on this machine (old PIII 750).

---

### Post by cariboo on 2009-05-14
From what I can tell, Sshmenu is a panel applet, so you can just right-click on the top or bottom panel and select Add to Panel, then select sshmenu and add it to the panel.

---

### Post by InkyDinky on 2009-05-14
Right, that is what I did on the x64 machine.  On this machine there is no entry for SSHMenu in the Add to Panel menu however even though it is installed and runs fine from the command line.

---

### Post by spiderbatdad on 2009-05-14
Perhaps check through the Main Menu items including those listed under sytem tools. System > Preferences > Main Menu. Also, The nautilus side bar of your file browser can bookmark ssh connections made through the Places > Connect To Server Tool.

---

### Post by spiderbatdad on 2009-05-14
The applet part of ssh menu actually appears to be sshmenu-gnome
```
sudo apt-get install sshmenu-gnome
```Then it will appear in the add to panel menu. The icon is fairly un-spectacular...of course you can change it.

---

### Post by InkyDinky on 2009-05-14
Yes spiderbatdad you are correct!
Apparently in my haste I had performed thusly 
```
sudo apt-get install sshmenu
```
when I needed to perform thusly
```
sudo apt-get install sshmenu sshmenu-gnome
```
I must've installed using synaptic instead of the command line on the x64 machine and it took care of installing both!

---

