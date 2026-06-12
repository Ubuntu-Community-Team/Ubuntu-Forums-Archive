---
title: "Adding a new user"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-06
I just installed Ubuntu 11.04 on my new computer. I've been getting things set up for a few days, and now I want to add a new user account. However, when I go to System Settings, there is no "Users and Groups" icon anywhere. 

I did some research and I know there is a command line way to add new users, but I prefer the GUI way, and I figure I should fix this anyway. I checked in Ubuntu Software Center, and the package containing the command "adduser" is installed so I don't know why the icon is missing in System Settings. How do I add things to System Settings?

---

### Post by pytheas22 on 2011-08-06
If you open a terminal and type:
```

users-admin
```

does the GUI for controlling accounts open?  If so, it means the application is installed but there is simply not a launcher for it in your menu.  I can help you add a launcher if that is the case, but first let me know whether you're using Unity (the new Ubuntu interface with a dock-like menu on the left side of the screen) or traditional GNOME (a.k.a. "Ubuntu Classic," with no dock and with an Applications menu in the upper-left corner of the screen).

If you get a command-not-found error, then the application is not installed, and you should make sure the package "gnome-system-tools," which provides the users-admin program, among others, is installed on your system.  (It should be by default).

---

### Post by peterson43 on 2011-08-06
Thanks pytheas22. The command users-admin didn't work because the gnome-system-tools package wasn't loaded (I've been messing around with things the past week and I must have deleted it somehow). I loaded that package and then the icon was back in my System Settings. I figured it would be an easy fix, I just didn't know where to look. Thanks.

---

