---
title: "Ubuntu menu bar not very responsive?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-22
some time i have to click it mutiple time to get it to open and when i go to slecte or highlight, say office bar it will get stuck on the internet bar

i do have just the ubuntu icon not the the three names  like when you do a fresh inslal of ubuntu 

i am useing compiz effects on the  menu bar and i do think that may be slowing it down

any thoughts?
THANKS!

---

### Post by LewRockwell on 2009-10-22
we turn all that fancy stuff off...

less suffering for everyone...

.

---

### Post by doomsword2001 on 2009-10-22
happened to me aswell (i had to click 3 times on applications to open), i rebooted the pc and it was fixed.

---

### Post by philinux on 2009-10-22
They seem to have fixed this in Karmic but for jaunty users see below.

From here.
[http://www.goitexpert.com/general/ubuntuguide/](http://www.goitexpert.com/general/ubuntuguide/)

Faster Gnome/UBUNTU Menus

I&#8217;ve noticed that sub-menus tend to be a little &#8220;sticky&#8221;. It seems there is a 1/4s delay in usability. 

Click "Places", "Home Folder". Now, we need to create a file called .gtkrc-2.0. To do this we right-click on any white space and move our mouse over "Create Document" and click "Empty File". We now rename this file to .gtkrc-2.0.

We will now double-click the ".gtkrc-2.0" file you just created and add the following line to it;

gtk-menu-popup-delay=0

Click Save and close the window.  You will have to log back in to see the results.

If you feel your Ubuntu menus open too fast now and would like to make them slower, the suggested optimal speed is:

gtk-menu-popup-delay=100

---

### Post by R3fr4cti0n on 2009-10-22
It always amazes me the pursuit of perfection that the community holds, i thought to my self this is a little thing that really bothers me but no one probly even notices, i take a chance at asking and i get a solution wow. THANKS

---

### Post by R3fr4cti0n on 2009-10-22
> **LewRockwell said:**
> we turn all that fancy stuff off...

less suffering for everyone...

.

  i know that you are trolling but i will bit out of curiosity.. who is "we"

---

