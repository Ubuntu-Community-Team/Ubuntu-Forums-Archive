---
title: "NIS problem"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by fouadk on 2008-02-19
hi everyone...

i have followed the following steps in order to configure ubuntu to login via NIS:
the steps are the following:


adding the following line to /etc/passwd, /etc/group and /etc/shadow :
+::::::
I have also changed the /etc/nsswitch.conf :
passwd: files nis 
shadow: files nis 
group: files nis 

but i am still having a problem with NIS....it simply does not bind with the server....

other machines running fedora core bind successfully....

please help

thanks in advance

---

### Post by rome-NY on 2008-02-20
I too can't login via my nis server with kubuntu. I can with other suse clients but not kubuntu. I can ypcat the files and see them but no login works.

---

