---
title: "Totally confused about how to start"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by GarnetWizard on 2009-10-20
I just downloaded and installed ubuntu.  When I restarted my computer, if offered me the choice: Windows or ubuntu.  I selected ubuntu and my computer when through a brief installation procedure.  Then it asked me for my user name and password.  I never was asked for either a user name or password when I downloaded.  I've tried entering every user name and password I've ever used on this computer, but nothing works (and I have been careful to use the proper case on my old passwords).  I've even tried leaving the user name and password fields blank, thinking this might be some kind of formality.  Nothing works.  Help.  (and thanks).

---

### Post by martrn on 2009-10-20
[COLOR="Black"]Boot your computer as normal then type [COLOR="SlateGray"]*<Escape>*[/COLOR] at the grub prompt.

At this point type *[COLOR="SlateGray"][e][/COLOR]* for edit.  Find the line that begins kernel ubuntu 8.888    and type *[COLOR="SlateGray"][e][/COLOR]*.  Here find the very end of the line and add     **[COLOR="Red"]rw init=/bin/bash[/COLOR]**  type *[COLOR="SlateGray"]<Enter> [/COLOR]*, then press *[COLOR="SlateGray"][b][/COLOR]* to boot your system.

Your system will boot up to a root shell, with no password required.

Type :  [COLOR="SlateGray"]passwd username[/COLOR]

Set your password.

Type in : [COLOR="SlateGray"]reboot[/COLOR][/COLOR]

---

### Post by Nesaskewatch on 2009-10-20
Someone helped so I removed my post.

Have fun!

---

### Post by GarnetWizard on 2009-10-20
Thanks.  I'll try that.

---

### Post by GarnetWizard on 2009-10-20
Thanks to Martrn for your advice.  I carefully followed your instructions, but sadly it did not work.  I tried a couple of variations, but I suspect something went wrong with the download.  Since I'm at the very start of this transition, I think I'll just uninstall and start over.  Thanks for your help, it's good to know that someone out there is keeping an an eye out for us beginners. :)

---

