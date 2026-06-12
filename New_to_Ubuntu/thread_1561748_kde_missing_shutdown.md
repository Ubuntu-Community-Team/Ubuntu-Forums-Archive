---
title: "kde missing shutdown"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by tonsil on 2010-08-26
Hello everyone! I'm running Ubuntu 10.04 and I installed KDE the other day so I can switch back and forth between Gnome & KDE. It works perfectly fine. However when I'm in KDE I can't see the shutdown and restart options. When I choose "Leave" from Kickoff I have Logout, Lock, Switch User / Hibernate. What must I do to have shutdown and restart buttons appear in that menu? Thank you.

---

### Post by PPPilot on 2010-08-26
KDE does not have a shutdown option from the desktop as you stated. Go ahead and log out. When you get to the logout screen click on your name and some options will appear on the bottom panel (same place where you choose KDE or Gnome). Look at the far right end of the panel and you will see a little switch icon. Click it and it will show you the option to shut down etc....

---

### Post by tonsil on 2010-08-26
Thank you for your reply. I think I got confused because I have Kubuntu 10.04.1 installed on a separate drive and I have the shutdown & restart buttons just below the Hibernate option in the Leave menu.

This is so disappointing. Why can't I shutdown or restart without logging out first?

---

### Post by PPPilot on 2010-08-26
You can always open a terminal and type in:
```
sudo shutdown -h now
```

---

### Post by ankspo71 on 2010-08-26
Hi,
Can you confirm that "Offer Shutdown Options" is enabled in the Session Management options of the System Settings? If I disable that it will remove the shutdown and restart buttons from all of my menus. 

If you can't get the shutdown and reboot options to appear in your menus, it still should be possible to use the "Lock/Logout" widget which also provides shutdown and restart features. You can add it to your panel or as a widget on the desktop.
Hope this helps.

---

### Post by tonsil on 2010-08-26
@ankspo71 "Offer shutdown options" is enabled but I don't see those choices in the leave menu. I tried adding the widget as you suggested, but I guess I will have to modify "Default Leave Option" to make it work, because the logout button ...logs me out :)

If it's of any help, I'm running KDE 4.5.0.

---

### Post by ankspo71 on 2010-08-26
Hi,
Are you still using GDM? I am reading about how GDM prevents KDE's shutdown and reboot buttons from appearing in the menus. This thread says that plus  also mentions a kde shutdown utility called kshutdown. 
[http://ubuntuforums.org/showthread.php?t=1307800](http://ubuntuforums.org/showthread.php?t=1307800)

Here is how you can switch between GDM and KDM (if you have both installed).
[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)
Hope this helps.

---

### Post by tonsil on 2010-08-27
@ankspo71 Thanks for the link! I was using the gdm as you predicted and when I switched to kdm, shutdown and restart buttons appeared! Thank you :D

---

