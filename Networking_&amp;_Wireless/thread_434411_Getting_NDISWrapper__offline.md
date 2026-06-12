---
title: "Getting NDISWrapper  offline"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-05-05
Hi, I am going to have to ndiswrapper to get wireless to work. Is there a way I can just throw the deb on a usb stick? Where I just download the deb, I am not going to be able to download it from a repository.

---

### Post by wtruong on 2007-05-06
download the source here [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=504757](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=504757)

and compile it

---

### Post by chili555 on 2007-05-06
I believe it's on your install CD. Please try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```Of course, it will complain mightily when it can't reach the on-line repositories, but you can safely ignore it.

---

