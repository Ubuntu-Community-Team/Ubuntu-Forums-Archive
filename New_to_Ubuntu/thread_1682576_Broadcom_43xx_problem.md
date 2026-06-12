---
title: "Broadcom 43xx problem"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by esotericmartyr on 2011-02-06
I'm running Ubuntu 10.10 x64 on my Dell Studio 1537. I'm new to Linux, and I'm enjoying running Ubuntu very much, but I can't get wifi working. When Ubuntu launches, and GUI appears, I get "Restricted Drivers Available" popup. When I click "activate" it tries to download or install something, but it fails. I tried to follow some guide about ripping firmware from Windows driver, but I got stuck either.
I'm running Ubuntu from USB drive (just to make sure it will work before I install it on my hard drive) and I'm currently connected to the internet using cellular data via Bluetooth.
Thanks.

---

### Post by TeoBigusGeekus on 2011-02-06
> **esotericmartyr said:**
> I tried to follow some guide about ripping firmware from Windows driver, but I got stuck either.

Have you followed [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") guide?

---

### Post by coffeecat on 2011-02-06
Have a look at this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If your current internet access is failing to download the restricted driver, you can add a live CD as a package source. Instructions are in that link.

**EDIT**: sorry, just noticed you are running from a live USB. If you were to burn a CD from the ISO, I guess you could access the packages from the CD while running the live USB session.

---

### Post by esotericmartyr on 2011-02-06
It was a different guide, I've googled it:
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Thanks for help. I'll try to follow the guide you've mentioned and tell if it help.

By the way, when I booted up a distro from my friend (Knoppix) on my laptop, wifi worked out of the box. :(

---

### Post by coffeecat on 2011-02-06
> **esotericmartyr said:**
> 
By the way, when I booted up a distro from my friend (Knoppix) on my laptop, wifi worked out of the box. :(

It's a licensing issue. When Ubuntu 10.10 was released, they were not permitted to include the Broadcom proprietary driver in a default install. Irritating - yes, but that was the situation. Just recently Broadcom have decided to open source their drivers so future releases of Ubuntu will, hopefully, not have this problem. And perhaps your version of Knoppix was released more recently than Ubuntu 10.10. Or perhaps Knoppix take a more - ahem - robust view of licensing matters. :) I really don't know.

---

### Post by esotericmartyr on 2011-02-09
Thanks guys for help.
I have managed to make my wifi working simply by enabling additional repositories in packages manager. -.-

---

