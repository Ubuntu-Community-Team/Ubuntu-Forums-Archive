---
title: "&quot;/etc/modles&quot; problem"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by x__dark on 2005-11-05
I'm trying to get my wlan0 to configure on boot. I followed the guide to use ndiswrapper and the wifi howto in the ubuntu wiki, but when i go to add ndiswrapper to the modules list, it will not allow me to edit the file. 

I'll post the error message if needed, but i'm using windows at the moment.:confused:

---

### Post by riggsd on 2005-11-05
```
sudo gedit /etc/modules
```

You must use **sudo** to have the permissions to modify a file under /etc, or anywhere outside your home directory for that matter. This is very basic to doing any system configuration on Ubuntu.

---

### Post by x__dark on 2005-11-06
Weird, I was going to reply and give you the error message i was getting when attempting exactly what you just told me to do, but it worked. :) Thanks anyways

---

