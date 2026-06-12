---
title: "Hardy file sharing info?"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by twgray on 2008-08-16
Where does Hardy store its file sharing info?  I would have thought it would save it in the smb.conf file but it is not there.  That is, I have shared a file but it is not referenced in smb.conf.

---

### Post by Naatan on 2008-08-16
Depends on your setup, try 

$ sudo updatedb
$ locate samba | grep conf

then look through the results for the file that might hold your shares.. possibly you have multiple smb.conf files and you are checking the wrong one.

---

