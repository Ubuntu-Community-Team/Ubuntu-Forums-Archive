---
title: "Desktop getting it back"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Bikinguy on 2011-04-23
Hi All

So far really enjoying my 10.10 install. Created a panel along right margin and decided to delete it. After doing so noticed that it had my log in name twice at the far right top of screen. Deleted that and the top panel disappeared. Tried everything I can think of but can not get it back. 

How do i get the top panel back ? 

bikinguy

---

### Post by Bikinguy on 2011-04-23
Let me clarify a bit more..I am referring to the top of the desktop that has the time date launcher etc.

thanks

---

### Post by Bikinguy on 2011-04-23
Ok...found the way to fix it

---

### Post by mikey73000 on 2011-04-23
[COLOR=DarkOrchid]:D  To get top panel back type in Terminal          [/COLOR]
 gconftool --recursive-unset /apps/panel && killall gnome-panel

---

