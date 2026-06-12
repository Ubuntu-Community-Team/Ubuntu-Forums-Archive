---
title: "NFS / KDM problem"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by frantek on 2007-06-29
hi,
 
my setup looks like this:
 
 - server 6.10 LTS
 - 4 dapper clients
 - 2 edgy clients
 - AUTH by LDAP
 
there is one single NFS mount on each client called /space. this is done by a fstab entry at boote time like this:
 
 server:/space /space nfs defaults 0 0
 
homes are located at /space/home and NOT as usual at /home. so homes are located on the server not on the client. the dapper clients work as expectd but the edgy clients show a strange behaviour. after a fresh boot every thing works as expected. /space is mounted and the home's are accessible. users can login by KDM. as soon as a user loggs off /space gets umounted. without /space mounted no other user can login in due to missing home.

I've no idea by what this is caused. can some one help ? 
 
 TIA
 frantek

---

