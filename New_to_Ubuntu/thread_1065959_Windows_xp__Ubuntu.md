---
title: "Windows xp / Ubuntu"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by kcr-By-Tor on 2009-02-10
New to ubuntu.  I installed ubuntu eliminating windows last week and like it so far.  I now need to install a cabinet design program that will only run on windows.  Can I do a dual boot installation with windows and ubuntu if ubuntu is my primary OS?

---

### Post by Michael.Godawski on 2009-02-10
hi, 

you can dual boot with windows, have a look here:

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[/LIST]
Just choose your installation type.

Or you can try to run the Windows Application with Wine.


[LIST]
[*][http://www.winehq.org/](http://www.winehq.org/)
[/LIST]

---

### Post by bruce2000 on 2009-02-10
> **Michael.Godawski said:**
> hi, 

Or you can try to run the Windows Application with Wine.


[LIST]
[*][http://www.winehq.org/](http://www.winehq.org/)
[/LIST]

Alternatively it can be installed from the repos, open a terminal and type:

```

sudo apt-get install wine

```

---

### Post by OffAxis on 2009-02-10
Here's another dual boot resource page, only it chronicles both windows-then-linux and linux-then-windows.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

although for my two cents, I'd just do the windows install and then recover grub with Super Grub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by kcr-By-Tor on 2009-02-10
Thanks Michael.Godawski:guitar:, I went to the link you mentioned.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") The instructions were clear and I was able to reboot with both windows and ubuntu without losing any of my ubuntu settings or data.  I was also able to install the design software onto windows sucessfully.  This particular software program does not do well with "wine".  Thanks for your help.

---

