---
title: "How do I change the order of the icons in the Favorites Menu?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Trying to switch on 2010-05-05
Clean freak much? Yes, I know.

[IMG]https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png[/IMG]

---

### Post by applehead on 2010-05-08
There's no way that I know of but it probably is possible.

I think you should ask yourself if it is worth spending lots of your time only to have slightly different menus.

---

### Post by nlvivar on 2010-06-05
I would like to know this too. I have been using the Netbook Edition for since it first came out, and I must say that this has been on my mind for quite some time now.

---

### Post by bone2006 on 2010-08-15
gconf-editor in the terminal, then edit from the menu and select find. Type in favorite

It will take you to /apps/netbook-launcher/favorites

right click on the favorites on the right side and edit key. Here you can rearrange the order. You have to reboot for it to work though after you finish editing.

To add or remove items you can just right click on them while using the environment

---

### Post by kerry_s on 2010-08-15
> **bone2006 said:**
> gconf-editor in the terminal, then edit from the menu and select find. Type in favorite

It will take you to /apps/netbook-launcher/favorites

right click on the favorites on the right side and edit key. Here you can rearrange the order. You have to reboot for it to work though after you finish editing.

To add or remove items you can just right click on them while using the environment

you don't need to reboot, just run "killall netbook-launcher".

---

### Post by Sir William Bailey on 2010-08-15
What about drag and drop process to change into your favorite style.:KS

---

### Post by kerry_s on 2010-08-15
> **Sir William Bailey said:**
> What about drag and drop process to change into your favorite style.:KS

you can have that in netbook remix 10.10 :D

---

