---
title: "Virtualbox issue"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Rocky-bb on 2010-01-19
Hello fellas, I'm having a problem with my virtualbox guest OS which is Win-XP (host OS is ubuntu 8.10 [as usual :D]), the problem is that im not able to use the usb devices on it,even it is not in the VB machine settings window :( (screen shot is added). I have followed the steps mentioned on [this ]("https://help.ubuntu.com/community/VirtualBox/USB")page, but still no luck. So I need your help to solve this issue.

Thanks.  :)

**[COLOR=Red]*Screen shot*[/COLOR]**
[[IMG]http://img17.imageshack.us/img17/1582/figure3l.jpg[/IMG]]("http://img17.imageshack.us/i/figure3l.jpg/")

---

### Post by inobe on 2010-01-19
that's virtualbox ose, it does not have usb support.

you can uninstall it and download it from here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

the proprietary version has usb support...........

once you install' you should be able to start the same guest os, you shouldn't need to reinstall the guest.

---

### Post by Rocky-bb on 2010-01-19
> **inobe said:**
> that's virtualbox ose, it does not have usb support.

you can uninstall it and download it from here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

the proprietary version has usb support...........

once you install' you should be able to start the same guest os, you shouldn't need to reinstall the guest.

Hmmm so that's the issue thanks, and are you sure that I don't need to re-install the guest OS (because I got some critical data on it).

---

### Post by howefield on 2010-01-19
> **Rocky-bb said:**
> Hmmm so that's the issue thanks, and are you sure that I don't need to re-install the guest OS (because I got some critical data on it).

Also looks like an old version, it is now Sun who have Virtualbox, not innoTek.

Your virtual machine will be stored in .virtualbox folder in your /home.

It won't be removed when you uninstall/reinstall Virtualbox. (you really don't need to, but if you feel safer, then copy it elsewhere)

---

### Post by inobe on 2010-01-19
> **Rocky-bb said:**
> Hmmm so that's the issue thanks, and are you sure that I don't need to re-install the guest OS (because I got some critical data on it).

it's always a good thing to backup critical data, anything can go wrong.


from my experience' i never needed to reinstall the guest os.


btw the documentation site you followed is pretty outdated material and i don't know what will happen due to those changes you've made.

---

### Post by howefield on 2010-01-19
> **inobe said:**
> btw the documentation site you followed is pretty outdated material..

VirtualBox/USB (last edited 2009-12-26 16:08:43 by Jeff Hoogland)

---

### Post by Rocky-bb on 2010-01-19
Thank you so much for your valuable contribution.

Thanks. :)

---

### Post by inobe on 2010-01-19
> **howefield said:**
> VirtualBox/USB (last edited 2009-12-26 16:08:43 by Jeff Hoogland)

good catch, i'm not too sharp this morning.


your welcome rocky

---

