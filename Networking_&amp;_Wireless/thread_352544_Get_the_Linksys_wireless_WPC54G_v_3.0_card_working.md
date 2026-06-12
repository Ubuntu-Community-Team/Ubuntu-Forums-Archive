---
title: "Get the Linksys wireless WPC54G v 3.0 card working in Dapper"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by chipyoung on 2007-02-03
Hip Hip Hooray.  I finally got the Linksys wireless card (WPC54G v 3.0) working.  I have been working on this for about 3 days.  It turned out to be a driver problem.  I finally used the Window drivers along with ndiswrapper to get this card working.  Contrary to what many posts said, I ended up using the following two files which were included in the box cd using the nt folder version.  

LSBCMNDS.inf
bcmwl5.sys

Many posts suggested using the bcmwl5.inf file, but that did not work.
I also used the post from [_**piracyrocks thread**_ ]("http://www.ubuntuforums.org/showthread.php?t=190177&highlight=bcm4318")  to blacklist the bcmxx driver, install ndiswrapper and then loaded the new driver.

If you have been trying many scenarios (like I had) then you also might want to get back to square one.

sudo modprobe -r bcmwl5
sudo modprobe -r ndiswrapper
sudo apt_get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

It sure feels goooood.
Goodluck,
Chip

---

