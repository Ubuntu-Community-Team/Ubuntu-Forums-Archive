---
title: "Installing newer versions of software which aren't in the repos."
date: 2011-04-25
forum: New to Ubuntu
---

### Post by wolfmanmi on 2011-04-25
Hi all.  I currently have Texmaker v2.0 installed (from the standard repositories).  I would like to install v2.2 or higher since it has the ability to use synctex.

My question is: do I need to uninstall texmaker before installing the new version via a downloaded tarball?  Thanks.

---

### Post by kerry_s on 2011-04-25
in ubuntu you use ppa's to get the latest.
google textmaker ppa

---

### Post by Frogs Hair on 2011-04-25
Some software requires the removal of previous versions and some does not. If you are worried about it , remove the old version and reinstall if the new version does't work for some reason . There is the possibility of missing  dependencies  when upgrading from a website .

---

### Post by stoneage on 2011-04-25
Depends how it runs. If you have to compile and install, or if you install from a .deb, then yeah, the default installation will overwrite the one you have. 

If you build from source you can specify a custom location for it, so you can keep them both.

If you just extract and run, then you can save it pretty much anywhere, so you could safely run the portable and v2.0. 

Or you could build from source to a custom location.

---

### Post by Paqman on 2011-04-25
Texmaker has proper .deb packages available for Ubuntu, don't install a tarball, as it won't get updates and could break your currently installed version.

[Texmaker download page](http://www.xm1math.net/texmaker/download.html)

Tarballs are almost never a good way to install software IMO.

---

### Post by wolfmanmi on 2011-04-25
Thanks everyone.  I installed using .deb package from Texmaker's website.  The installation didn't work correctly with v2.0 installed.  After uninstalling v2.0, everything went through perfectly!

---

