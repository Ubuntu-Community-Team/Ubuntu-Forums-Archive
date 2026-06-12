---
title: "ndiswrapper"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by patsfan on 2007-05-31
how do you install ndiswrapper if you burnt it on cd?:([http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

### Post by spd106 on 2007-06-01
Which version do you mean?

If it's the debs from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all") 

Then just double-click on them and gdebi should do the rest. Do ndiswrapper-common first, then ndiswrapper-utils. You probably won't need the source package.

If you've downloaded from [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=93482"), then you will also need the build-essential and kernel headers packages and their dependencies.

---

