---
title: "Error during Jaunty update"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-22
Hi,

I can't upload J. A Problem occurs at:

Setting new software channels, where I get "Error during Update" with these details:


W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, W:Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

, E:Some index files failed to download, they have been ignored, or old ones used instead.


What should I do next? I' m using Ibex

---

### Post by FredB on 2009-04-23
In synaptic, uncheck entries related to this CD.

Or press alt + F2
Enter : gksu gedit /etc/apt/sources/list

Add a # on line with [Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)] in it.

Close gedit and try again to upgrade.

---

### Post by nnjond on 2009-04-23
Thanks for your help

I can't find the entries related to this cd in symnaptic; not sure I know how to. This popped up somewhere Leading me to think it's not there:


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


gksu gedit /etc/apt/sources/list.  

Takes me to a blank page ???

---

### Post by Absolut Newbee on 2009-04-23
hej 
the list your have to edit is gksu gedit /etc/apt/sources.list

not gksu gedit /etc/apt/sources/list

try and se if that helps

---

### Post by FredB on 2009-04-23
Indeed. I made a mistake on my keyboard.

---

### Post by nnjond on 2009-04-23
Thank alot. Prob solved.

---

### Post by pbhj on 2009-04-24
I had this same [error whilst updating from intrepid to jaunty, the fix was to disable the partner repos]("http://alicious.com/2009/ubuntu-upgrade-intrepid-to-jaunty"). I'm on Kubuntu.

All working fine now.

---

