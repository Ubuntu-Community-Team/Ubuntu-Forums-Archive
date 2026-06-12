---
title: "Where is my NetworkManager ?"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by borgena on 2007-01-15
Hi,

I've heard that the network manager is a great tool to easily switch between several wireless networks. I''ve added the added the network-manager and the network-manager-gnome package (version 0.6.3-2ubuntu6) but now what ?

How do I add the applet (no applet in the add to panel menu) and do i need to configure the network-manager in some way?

Dell M90 Ubuntu Edgy

Thanks
-=Børge

---

### Post by Mike_Longbow on 2007-01-15
If you can't find an application in the menu you can always fire up a run window (alt+F2) and execute it by its name (being "network-manager" in this case). Also, I'm not really sure if there's panel applet for this...

Altought I don't like much network manager for wireless connections...

You can also give a try to this new[wireless manager]("http://www.ubuntuforums.org/showthread.php?t=299462"), it's in current developement, but it seems to work fine, and has a lot features.

---

### Post by merry_meerkat on 2007-01-15
Hi,
normally it should just appear in the panel notification area after a **reboot**.

If it does not, try right-clicking on the panel, then choosing "add to panel" and find it in that list.

(make sure you have a "notification area" on the panel. If you don't then you can add it using the same procedure as just described above.)

Also, I'm not sure that you need to add both **network-manager** and **network-manager-gnome**. In my case **network-manager-gnome** only did the trick.

Hope this helps.


btw: once you get it running, there is some information about using networkmanager and wpa on a Dell M70 laptop here: [http://boff.wordpress.com/tag/wireless/](http://boff.wordpress.com/tag/wireless/)
(disclosure: it's my blog ;) )

---

### Post by borgena on 2007-01-15
Hi,

Nope it didn't apear after reboot and I can'tr find it in the add to panel window. I've tried to start NetworkManager (no error and no output) as root but nothing happens except that the NetworkManager process is running

Any idea ?

-=Børge

---

### Post by borgena on 2007-01-16
Found out of this.... (blush...) the notification area was not showing :-D

---

### Post by merry_meerkat on 2007-01-16
...that's what I meant by this:

> **merry_meerkat said:**
> Hi,
(make sure you have a "notification area" on the panel. If you don't then you can add it using the same procedure as just described above.)


Glad you solved it. :)

---

