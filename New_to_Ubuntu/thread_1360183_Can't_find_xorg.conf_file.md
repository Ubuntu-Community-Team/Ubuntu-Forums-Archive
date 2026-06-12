---
title: "Can't find xorg.conf file"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by GTerrik on 2009-12-20
Hey guys,

I apologize for what I'm guessing is a very low level question here, I've had Ubuntu for a day...

I'm trying to get my scroll button to work (Thinkpad T43p) and found in some other threads to edit my xorg.conf file.  I went to filesystem\etc\X11 and there is no xorg.conf.  It's not in any of the subfolders either.

Where do I find the file?  Do I need to create one?  Do I need to upgrade xorg?

When I look up the version in terminal it tells me:
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu

Thanks!

---

### Post by halitech on 2009-12-20
Guessing that you are running 9.10? If so, there is no xorg.conf file. If you need to make one, run
```
sudo touch /etc/X11/xorg.conf
```
that will create the file and then you can edit it.

---

### Post by GTerrik on 2009-12-20
Ah.  Is there a better way to get my scroll button working then?  If i have to create it to edit it, it seems as if there should be a more direct method...

Thanks halitech

---

### Post by halitech on 2009-12-20
I'm not sure but you could check under System - Admin  and see if there is a mouse section that you can edit the options on.

---

### Post by GTerrik on 2009-12-20
Sigh, sorry, this is an even stupider question.  

I made the file, and added the text necessary, but how do I save as sudo?  It keeps telling me I don't have the permissions necessary to save the file.

---

### Post by GTerrik on 2009-12-20
Figured it out using sysfsutils, thanks for your help halitech.

---

### Post by m4tic on 2009-12-20
Next time you can run. sudo nautilus

---

### Post by halitech on 2009-12-20
would be better running graphical apps with gksudo, sudo and graphical apps run the risk of killing a system

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

