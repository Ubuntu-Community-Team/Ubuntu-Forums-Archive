---
title: "killed trash can icon"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-26
ok playing with my theme to death i changed my trash can icon on desktop and now it does not fill, and i don't know how to get the original back????? 
some times it fun to customize but not sure the frustration is worth it any body know how to get the original icon back???

---

### Post by DarinB on 2009-05-26
going around in circles,,,,i logged out trying to restore my trash can,,,added the icon in config editor and deleted and added it then tried to find the icon again ended up with a revert button somewhere and got back the original icon,,, to bad i have no idea what i did oh well thats the fun of a pliable OS you can find endless hours of jun messing with it.'

thanks

---

### Post by RealPSL on 2009-05-26
DarinB,

Where are you changing this? One option is to create a new user and login as that user and compare the difference between working and broken in the gconf-editor. I only see 2 entries relating to Trash:

/apps/panel/default_setup/applets/trashapplet/bonobo_iid
/apps/panel/applets/trashapplet_screen0/bonobo_iid

---

### Post by Markfwb on 2009-05-26
Hey buddy no problem.

Do this step by step:
 
1.  HIt alt and F2 .  This will bring up The Run application text box
2.  Type in gconf-editor
3.  click on apps 
4.  click on nautilus
5.  click on desktop
6.  put a check mark in trash_icon_visable
7.  x out of configeration editor and look at your desktop with a recycle bin :)

Let me know if this works

---

### Post by DarinB on 2009-05-27
thanks i like that method of the gconfig editor but the problem i had was i changed the icon and couldn't get the revert button to become enabled it finally did. so i was able to revert to the old icon. that happened after i logged out and when back in.

---

### Post by reg4c on 2009-05-27
Select a different theme in the "Change desktop background" dialog.

:D

This will not actually solve the problem but it should be fixed.

---

