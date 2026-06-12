---
title: "xubuntu and network servers and network drive"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by krisalis on 2009-02-14
Hi,
am presently using ubuntu 8.04.  I added a network drive to my network and ubuntu picked it up straight away via "network servers".

Have been experimenting with xubuntu.  It does not seem to have "network servers" and does not automatically find the network drive.  I do not know how to find the network drive, or any other computers on my network, with xubuntu.

I have had a look at the thread: "How to: Xubuntu - Thunar Native Windows Network Browsing".

Can someone confirm that my issue relates to this thread, or is my issue different?

Am interested in looking at xubuntu as my computer struggles with ubuntu- it is 4 years old and I would like to avoid buying more memory (692mb at present).

Cheers,
krisalis

---

### Post by gn2 on 2009-02-14
Xubuntu's default file manager, Thunar does not include network file browsing by default.

This can be configured manually, there's a how-to link in my sig which works perfectly, it's the one you mentioned, and yes, it is the cure to your problem.

---

### Post by sylvainrb on 2009-02-14
I have a temporary solution for this (I have 8.10 but it should work for you):

Alt+F2 then enter nautilus and hit return key

The problem is that it will change to your gnome desktop within the xubuntu environment. To change it back to normal, go to Applications->Settings->Setting Manager->Desktop and check the Allow Xfce to manage the desktop.

I haven't found out how to get it another way yet but it works for me when I sometimes need to get on the network drive. Or you could use the same background for ubuntu and xubuntu (it might have other non apparent changes though).

Hope this helps a little...

---

### Post by gn2 on 2009-02-14
Or use Dolphin....?

---

### Post by Denestria on 2009-02-14
> **sylvainrb said:**
> 
Alt+F2 then enter nautilus and hit return key

The problem is that it will change to your gnome desktop within the xubuntu environment. To change it back to normal, go to Applications->Settings->Setting Manager->Desktop and check the Allow Xfce to manage the desktop.


```
nautilus --no-desktop
```
will keep Nautilus from taking over your desktop.

---

### Post by sylvainrb on 2009-02-15
Cool thanks!

Lol I don't know why but I never bothered looking at the manual. The answer is right there.

---

### Post by krisalis on 2009-02-18
Thanks gn2,
I followed instructions at "How to: Xubuntu - Thunar Native Windows Network Browsing" and it works great!

Thanks also to sylvainrb and Denestria for your replies.

Cheers,
Krisalis

---

