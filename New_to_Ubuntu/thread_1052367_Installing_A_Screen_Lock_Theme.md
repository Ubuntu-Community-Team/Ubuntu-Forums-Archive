---
title: "Installing A Screen Lock Theme"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-27
I just downloaded a Hack screen lock theme and I dont understand how to follow the directions can somebody help me with this?

Here are the directions:

1. Unpack 1 folder 2 files to /usr/share/gnome-screehackver/
* ( directory hack-images lock-dialog-hack.glade lock-dialog-hack.gtkrc

2. Open gconf-editor (Alt+F2, type 'gconf-editor' and press enter) change the entry apps/gnome-screensaver/lock_dialog_theme from 'default' to 'hack'

3. Enjoy!

---

### Post by lonewolf1222 on 2009-01-27
**Well first you-** Unpack 1 folder 2 files to /usr/share/gnome-screehackver/
* ( directory hack-images lock-dialog-hack.glade lock-dialog-hack.gtkrc
**Next**-Open gconf-editor (Alt+F2, type 'gconf-editor' and press enter) change the entry apps/gnome-screensaver/lock_dialog_theme from 'default' to 'hack'

Then you can enjoy it

---

### Post by Tmoney1309 on 2009-01-27
Can somebody be more specific?

---

### Post by piratemurray on 2010-01-05
:P Sorry you didn't get anywhere with the first reply.

If you haven't figured it out already then here is an explanation:

> 1. Unpack 1 folder 2 files to /usr/share/gnome-screehackver/
* ( directory hack-images lock-dialog-hack.glade lock-dialog-hack.gtkrc

Double click the download and open it with a compression utility (usually FileRoller by default on Ubuntu). Select the files and extract them to the directory specified

> 
2. Open gconf-editor (Alt+F2, type 'gconf-editor' and press enter) change the entry apps/gnome-screensaver/lock_dialog_theme from 'default' to 'hack'

Open GConf using the instructions. GConf is a graphical way to mess about with system variables such as the lock screen saver. Use the hints to navigate the folder tree to gnome-screensaver and change the key called lock_dialog_theme to the one specified.

> 3. Enjoy! 

Enjoy!

I'm trying to do something similar myself and realise how frustrating it can be when you receive replies like the one you did. Hope you're enjoying Ubuntu!

Let me know if you need any more help. You *may* need to have temporary admin privileges to do some of the steps. If so just shout back!:KS

---

### Post by mikel363 on 2010-01-12
Ok, Now maybe I'm retarded or I dont have somethin installed and or working right. I follow all the steps to install a new lock screen and for some it wouldnt work. After tinkering with it for a while, i renamed the .glade file to .ui and it works... almost... I got the theme to work but instead of it being a full screen theme it was just a box in the middle of my black background... Can anyone help me out with this? I really dont like ugly defalt lock screen... Runnin Ubuntu 9.10 and just updated it like 3 hours ago.:(

---

### Post by Cedric83 on 2010-04-30
I'm having the same problem.  It has to do with 9.10 using .ui instead of .glade.  No fix for this yet, i'm afraid :(.  But i've noticed that I get better results if instead of using the .glade file that was included with the custom theme, simply log in under root and make a copy of lock-dialog-default.ui (which should be found under usr/share/gnome-screensaver) and rename that copy to match the custom theme ( lock-dialog-[insert custom theme name here].ui  for example ). Then follow all the usual instructions. I've found that using this method, the theme shows in it's intended size, and you keep all the functionality of the default theme (like the message button).  The only downside is that it still has a big user icon that kind of get's in the way.  Hope this helps! :)

---

### Post by amillionsheep on 2010-05-03
Hm, you'd think who ever made most of the Screensavers on gnome-look would jump on this .ui change and update their Lock Dialogs accordingly.

---

