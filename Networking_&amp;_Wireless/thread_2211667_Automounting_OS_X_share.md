---
title: "Automounting OS X share"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by guy9 on 2014-03-17
title mostly sums it up.  I don't care if its the AFP share or the SAMBA share from my mac mini, whichever is the most reliable on ubuntu.

currently, i've tried variations of this in the fstab.

> //guys-mac-mini.local /media/Storage cifs username=myOSXusername,password=myOSXpw,iocharset=utf8,sec=ntlm 0 0

prior to editing the fstab i ran
> sudo apt-get install cifs-utils

then created my mount point
> sudo mkdir /media/Storage

as of now, after running 
> sudo mount -a

i get this
> mount error(22) invalid argument

what am i doing wrong or missing?  i feel like this should be much easier than it has been thus far.

---

### Post by guy9 on 2014-03-17
Anyone have any ideas?  I'd be happy to use a AFP client for ubuntu if a reliable one exist.

---

