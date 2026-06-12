---
title: "Login menu not appearing"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-14
hi,
 
i use ubuntu 10.04 on a dell studio 14 laptop. everything had been working fine for about a month. today, when i switched on my machine, only the purple background of ubuntu is appearing, i.e. no menu where i can type in my password. 
 
i saw a few posts dated a few months back with people having similar problems, but none of them were marked solved, and so i am creating a new post. can someone please help.
 
the only thing i had tried earlier was to download and try and install some gtk+ packages.
 
i tried ctrl + alt+F1 and startx, but that gave a fatal error. 
 
thanks

---

### Post by LittleGyko on 2010-07-14
I even tried :
 
sudo dpkg-reconfigure gdm and then startx brought me to the same purple screen, again without the login menu. 
 
sudo /etc/init.d/gdm restart
sudo /etc/init.d/gdm stop and sudo /etc/init.d/gdm start 
 
but none of the above helped.

further, some time back i saw the following post
> **Saser said:**
> Now my Ubuntu works perfectly. It seems that I get  this problem when I compile and install a few packages from their  sources, like libpng and zlib.

and it turns out that i too had installed zlib today. i got the impression that it was required for GTK.

is there some way to uninstall zlib or uninstall the packages i installed today??

thanks

---

