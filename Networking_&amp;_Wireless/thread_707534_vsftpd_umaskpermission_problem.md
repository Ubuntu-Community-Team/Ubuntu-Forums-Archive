---
title: "vsftpd umask/permission problem"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by fornews on 2008-02-25
I've tried setting in vsftpd.conf

local_umask=022
anon_umask=022

and to other values 

followed with both

./init.d/vsftpd reload
./init.d/vsftpd restart

with out any luck. The files are always 600

I've read through a number of web pages here looking for an answer and
nothing I've found is helping.

Also, in case this matter....

drwxrwxrwx  2 nobody root
-rw-------  1 nobody nogroup

Could the directory and/or file ownership/group be part of the problem ?

I can tftp to the server but always the files are 600.

Any ideas ?
Should I use some other tftp daemon since vsftpd seems to have a problem ?

TIA

---

