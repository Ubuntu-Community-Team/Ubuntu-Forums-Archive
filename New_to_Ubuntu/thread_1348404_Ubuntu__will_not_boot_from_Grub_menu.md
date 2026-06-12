---
title: "Ubuntu  will not boot from Grub menu"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by jebbushell on 2009-12-07
I have installed Jaunty via Wubi on XP. The grub boot menu shows XP above Ubuntu.
 
While I was distracted it autobooted XP. Then I instantly crashed the XP boot with the off button (ok, ok, I know, I know) and now Ubuntu wont boot from the grub menu.
 
Is there any way to rectify the situation? I expect this happens to a lot of people.
 
 
Regards,
 
Jebbushell at gmail dot com

---

### Post by dzon65 on 2009-12-07
If it's a wubi install,and it simply won't boot,I suggest you reinstall it (delete the previous one first)it'll take you like 30min (something).And...pretend the shutdown button isn't there;)

---

### Post by jebbushell on 2009-12-07
Thanks for your lightning response, but what about my apache and drupal installs? Are they toast?

---

### Post by MelDJ on 2009-12-07
you don't need to reinstall. 
i suppose it goes to a shell with 'initramfs' and 'busybox'?
this normally happens when windows is not shutdown properly
to rectify it, run a chkdsk /f from windows. then restart cleanly into ubuntu

---

### Post by jebbushell on 2009-12-07
Thanks for your reply.    My Wubi installation is perhaps unusual in that my linux stuff is on a Maxxtor USB external drive.  This appears to have been paralysed by my one-fingered salute (see above) and was just sitting there with its light on but not online.   I could not tell this from the Grub prompt.  I discovered it by booting up XP and checking Winfile and then DISKPART.  A cold restart sorted the Maxxtor and, lo and behold, my Ubuntu boots again!
 
Presumably the fact that ***grub> find ( <tab>*** only reported ***hd0 rd***, i.e my C drive, was Grub's way of telling me what was obvious from Winfile.
 
Thanks again to you both.
 
Jeb

---

