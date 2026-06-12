---
title: "install wireless driver in 8.10"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by bschultzjames on 2008-11-08
I have recently installed ubuntuStudio 8.1 and cannot figure out for the life of me how to get wireless working...


I cannot even locate any wireless settings in system>preferences or system>administration.


I know i need to install a linux-driver for my Intel PRO/Wireless 2200BG, but I cannot find where to download a file that will install.


Any help would be....help...ful!

---

### Post by alwayshere on 2008-11-08
in terminal put 

sudo apt-get install linux-ubuntu-modules-2.6.24-21-generic 

then 

sudo apt-get update

see how that goes

---

