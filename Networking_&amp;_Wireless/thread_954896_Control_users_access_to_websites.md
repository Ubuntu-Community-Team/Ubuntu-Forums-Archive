---
title: "Control users access to websites"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by //yardo on 2008-10-21
Hello all! Couple things here.

I need to control what websites a user can access. I would like them to only be allowed to a certain list of websites.

I would also like to block this user from being able to access my network; SAMBA shares etc.

---

### Post by cariboo on 2008-10-21
Install squid to block access to websites, there is a howto here:

[http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733)

To block the user form connecting to network shares, if the user is on the same computer  go to System-->Administration-->Users and Groups unlock the app, select the user, then click properties then go to User Privileges and uncheck **Share files with the local network**

Jim

---

