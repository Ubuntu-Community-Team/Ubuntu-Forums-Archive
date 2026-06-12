---
title: "Unable map smb drive"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by avyaktha on 2008-09-09
I have a smb share running in redhat linux 4 and am trying to mount it in ubuntu 8.04 LTS

sudo mount.cifs -v //10.72.40.216/root /media/umesh -o user=root,pass=password,domain=mygroup

I get an error 

Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found


sudo mount.cifs //10.72.40.216/root /media/umesh -o user=root,pass=password,domain=mygroup

gives me a 

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


I have searched the forum enough none of the suggestions seems to alleviate this issue

please help

---

