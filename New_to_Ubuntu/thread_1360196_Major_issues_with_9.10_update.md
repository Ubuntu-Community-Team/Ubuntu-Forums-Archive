---
title: "Major issues with 9.10 update"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by thegrubixcube on 2009-12-20
Hi all,

I just tried to install the 9.10 update from Jaunty. Right after it finished downloading the updates, my computer froze and I was forced to restart. When I did, it seemed that 9.10 had loaded, but not completely. I got error messages about not having the correct nvidia drivers. 
I finally loaded in low graphics mode and got the system to boot, but my trackpad on my laptop did not work. Also gnome-do was not responsive. A wireless mouse does work though. Also my wireless internet did not work. Right now I am on Vista because Ubuntu is currently unusable.
I tried to boot the previous version in the grub menu, but that just gave me a bunch of errors.
Is there any way I could do a fresh reinstall? I have no clue what to do at this point.

Thanks

---

### Post by UnknownFear on 2009-12-20
I'd recommend you install via Wubi if you want a fresh install. As for updating, not sure. I normally just do a fresh install once a new flavor is out.

---

### Post by thegrubixcube on 2009-12-20
I already have a separate partition dedicated for ubuntu so I don't think I want to use wubi. Do you know how I could do a fresh install without a usable version of ubuntu?

---

### Post by TBABill on 2009-12-24
Are you able to download the .iso again for Ubuntu and create a LiveCD (or LiveUSB)? You can reinstall via that method.
 
One note. Many have found in Ubuntu, as I did in Mandriva 2010, that  you may need to connect to your router or modem by wire when you first install if your wireless does not come up or does not fully function. The reason for this is that you may have a driver incompatibility that may or may not be solved after you run the update feature in Ubuntu. Once the system fully updates you can then unplug the ethernet cord, reboot and try your features (including video, sound, wireless, etc) again to see if they function properly.
 
I couldn't get Mandriva running on one of my laptops and this was the fix for it. Once it updated all wireless features worked perfectly. At first I could see my wireless router and attempt to connect to it, but I got a "connection failed" response every time. I hope this all works for your problem as well.

---

