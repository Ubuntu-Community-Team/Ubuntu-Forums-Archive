---
title: "Why eth changes it's number every time?How can I prevent that?"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by rootware on 2007-12-24
My eth for my wired network changes every time on reboot, so I have to setup the wired network every time. How can I prevent that? Why is that happening? :confused:

Thanks a lot!

---

### Post by kevdog on 2007-12-24
Are you using gutsy or feisty?? The methods are different.

---

### Post by rootware on 2007-12-24
> **kevdog said:**
> Are you using gutsy or feisty?? The methods are different.

Thanks for your reply, kevdog.

I use Ubuntu  7.10.

---

### Post by kevdog on 2007-12-24
I cant remember the link but you want to do a search for the following:
/etc/udev/rules.d/70-persistent-net.rules

This is the file that sets the persistent naming rules.  (iftab was used in Feisty -- it was easier).  There was a post by noob12 that was discussing this file.  It was pretty informative.  Sorry I dont remember the exact link.

---

