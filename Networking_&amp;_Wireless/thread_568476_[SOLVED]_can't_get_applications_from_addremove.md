---
title: "[SOLVED] can't get applications from add/remove"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by tyggna1 on 2007-10-05
I recently got my wireless card working!

Unfortunately, now add/remove always gives a pop-up that says "This application is supported by the Ubuntu community, do you want to install?"   
Then I click install, but it pops up again and says, "you need a valid internet connection" and I click okay and then it says, "make sure this software is for x86" --blah blah blah. 

I tried:  dpkg-reconfigure gnome-app-install, but it still does the same thing.

How to I get app-install to see my network connection?

BTW: so far, it's only done this when connected wired, I haven't tested the wireless yet.

---

### Post by tyggna1 on 2007-10-05
tried it wirelessly, same thing.

---

### Post by tyggna1 on 2007-10-05
Any ideas, anyone?

---

### Post by tyggna1 on 2007-10-05
<whistling>, bump!

---

### Post by rsambuca on 2007-10-05
Three bumps in an hour?? :confused:

---

### Post by tyggna1 on 2007-10-05
well, it is a bit urgent--also, the first one wasn't a bump, just more info.

---

### Post by tyggna1 on 2007-10-05
So, I've spent the past two hours trying to fix this, only to find out that I can't get anything from synaptic, aptitude, or add/remove.   Synaptic only shows installed packages.   When I go to software sources, and try to click the options listed (Ubuntu server, restricted proprietary, ect), I get nothing.   They won't check.   I click refresh on close, and it still won't take any of them.

Could I be missing a config file somewhere, or what files would be involved with this sort of problem?

---

### Post by rsambuca on 2007-10-05
Post your /etc/apt/sources.list

---

### Post by tyggna1 on 2007-10-05
interesting, I have no apt directory.  That could do it.  Any ideas how to get that back?

---

### Post by tyggna1 on 2007-10-06
I just manually added the directory and file with the name sources.list, and bam! it worked again.  Is there anything else in that directory that I'll need?


Oh, and on the updates, it says that it cannot verify any public keys given.

---

