---
title: "Clock Panel App Pop-out Problem"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by dmaxel on 2010-11-06
Hello everyone,

I have a strange problem that I hope will have an easy fix. So, if you look at the attached screenshot, you should probably spot the problem. It would be helpful if I could change it where the pop-out goes right over the panel applet itself, just as it usually would if the panel were at the top (which works when it's at the top, by the way). I'd just prefer it more if I kept the panel on the bottom instead of the top.

Thanks!

(Yes, I'm running Ubuntu 10.10, I just have the Fedora wallpaper because I like it. :P)

---

### Post by dmaxel on 2010-11-07
Can anyone help me out with this? :)

---

### Post by SuaSwe on 2010-11-08
Does this thread help at all: [http://www.uluga.ubuntuforums.org/showthread.php?t=1609332](http://www.uluga.ubuntuforums.org/showthread.php?t=1609332) ?

---

### Post by dmaxel on 2010-11-08
Hmmm, the problem could possibly be because of Compiz...though the thread doesn't specifically specify as to what the fix is, other than changing some setting in Compiz. :/

---

### Post by SuaSwe on 2010-11-08
From [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/631664:](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/631664:)

> 
Enough of that, here's a temporary workaround: Go to the "Place Windows" plugin of ccsm and under the tab "Fixed Window Placement" find the box "Windows with fixed positions" and click "new". Select the + icon and under "Type" choose "window title". click your calendar applet, then the "grab"-button and then click your open calendar. the resulting value should be something like "title=Calendar" or whatever it is in your language. Click add and under x and y positions choose the farthest settings to the right. Finally check "Keep in workarea" and you should be good to go.
-Either that or disable compiz and hope for another fix.


Does that work for you?

---

### Post by tom957 on 2010-11-14
Works for me. Thanks a bunch!

---

### Post by pbvijay on 2010-12-16
Its worked for me. (Ubuntu 10.10)
Thank you

---

### Post by dmaxel on 2010-12-16
Ah yes, forgot to post in here, sorry lol. That definitely worked. Thank you! (marking as solved)

---

### Post by joneez on 2010-12-19
I love Ubuntu forums! Thank you!

---

