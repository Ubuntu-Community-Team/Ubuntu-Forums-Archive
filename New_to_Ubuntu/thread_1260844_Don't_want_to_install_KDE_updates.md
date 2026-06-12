---
title: "Don't want to install KDE updates"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Wtwine on 2009-09-08
Hi

I am using Ubuntu Jaunty.  The update manager is popping up with some KDE updates e.g. kdelib-bin.  I use gnome, so I don't need kde updates.   I uncheck the boxes next to all kde updates in update manager when it pops up.  However, whenever update manager pops up again with other new updates, it includes the kde ones, which I keep having to uncheck. 

Could some  of my applets are KDE, which might explain why it is trying to update kde?

How do I stop it wantiongto update kde??

Thanks

W

---

### Post by GiantSpider on 2009-09-08
I'm used to Windows but whenever there is an update I just update it. Its easier that way. Besides there might be some security threat if I don't update months from now when I decide to use the application or whatever was updated. You don't have to know what's on your computer to use it. I've had a virus on my computer in the past for weeks before I dealt with it.

---

### Post by earthpigg on 2009-09-08
> **Wtwine said:**
> 
Could some  of my applets are KDE, which might explain why it is trying to update kde?

that is exactly correct. when you installed that KDE app, Ubuntu automatically recognized that it was missing some KDE "*depencancies*" and installed them along with the app.

very few people have systems that are *just* GNOME or *just* KDE.

if you want your KDE apps to remain reliable & functional, you may want to consider letting the KDE stuff that they depend on update :D

it doesn't mean you have *all* of kde, just the bare minimum bits and pieces that your KDE app needs to function.

---

### Post by Cheezespread on 2009-09-08
> **Wtwine said:**
> Hi

I am using Ubuntu Jaunty.  The update manager is popping up with some KDE updates e.g. kdelib-bin.  I use gnome, so I don't need kde updates.   I uncheck the boxes next to all kde updates in update manager when it pops up.  However, whenever update manager pops up again with other new updates, it includes the kde ones, which I keep having to uncheck. 
Could some  of my applets are KDE, which might explain why it is trying to update kde?
How do I stop it wantiongto update kde??
Thanks
W

Actually i have had the same questions a bit back. Have you installed any apps like k3b (the disc burner ) or Amarok ( Aint it KDE , too ?) ?.

If you have the exact name of the update , you can check the details of the same in [here]("http://packages.ubuntu.com/") .It will give you an idea of which apps are dependent on the update. See if you have any of them installed.

---

### Post by Jimmyfj on 2009-09-08
Hi

I'm not sure about this, but refusing to install updates on your GNOME-desktop just because they are KDE-files is a poor choice. The developers sends you the updates for a reason, this reason probably being GTK+ libs all around, and some programs  will expect those KDE-libs to be there in order to function correctly.

---

### Post by Wtwine on 2009-09-08
Ok folks, I got the info I needed.  I will install the KDE updates.

Thanks for quick response!

Cheers

W

---

