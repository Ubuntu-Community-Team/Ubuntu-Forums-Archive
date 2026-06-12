---
title: "User Settings are Messed Up"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Martega on 2010-09-09
Hello,  I previously had a problem where my mouse did not work after I logged in.  A person at my school looked at my system and we were able to determine that one of my user configuration files had been changed and was causing my mouse to not respond.  To fix the problem he made a separate temporary user and then deleted the configuration files for my user so that when the system would be rebooted new configuration files would be made.

This solved the mouse problem however I now have a few new problems.  In my main user account (not the temporary one) I cannot set the visual effects setting to extra.  When I try it says that it could not be enabled.  When I log into the temporary account that was just created I CAN change the visual effects settings.  

Also in my main account there were two icons in the top right of the screen for networking and one for bluetooth.  The networking icon told me whether I was connected to ethernet or wireless and it let me connect to wireless networks.  The bluetooth icon turned on when I enabled it.  Now in my main account these icons are not there however when I log into the temporary account they are there. 

Can somebody explain why this might've occured and what I can do to fix it?

---

### Post by Martega on 2010-09-10
Please help, this is very frustrating.

---

### Post by Peter09 on 2010-09-10
The network icons are apart of the notifications applet which you can install by right clicking on the panel and installing the applet.
 
As to not be able to start network effects for your account (only), it sounds like the video driver does not like something about your settings. It may be the theme that you are using, as a simple start try changing your theme and then try and enable effects again.
 
I believe if you do this
 
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
 
in a terminal it will reset your account to standard (first login) settings.
 
I should try this as a last resort.

---

