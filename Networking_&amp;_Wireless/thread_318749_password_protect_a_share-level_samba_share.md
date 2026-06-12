---
title: "password protect a share-level samba share"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by nyktovus on 2006-12-14
So i'm posting this here because the samba mailing list was completely useles, i received only one reply to my post basically telling me that i'm a noob and i should read the manual and not bother them.. wow.

So anyway.. here's the scoop:

i have a samba server, running ubuntu. its securty is Share-level.. due to certain reasons on my network, user-level is not an option :) 

i have 2 shares :

[mine]
   path = /data
    guest ok = no
    force user = nykto
    writable = yes
    username = nykto

[data]
    read only = no
    force user = loser
    guest ok = yes
    path = /data/public

=======================

ok that said.. the "data" share works flawlessly.. no password.. no hesitation.. bam, lets everyone in as the "loser" user.. with his rights. 

BUT! i want the "mine" share to have a password.. so i can gain admin rights on the directory.. and the one above it.. 

no matter what password i type in.. (nykto password, admin password..etc) no dice. it wont me in.. 

GAh! any help would be groovy.

Nyktovus.

---

### Post by dann0 on 2006-12-14
Have you tried setting nykto as owner, and group of /data ? (chmod, chgrp)
perhaps you should have two different folders (/data and /public)
then you can mount /data/public to /public (mount &#8211;bind /data/public /public)

---

### Post by nyktovus on 2006-12-14
regaurdless of the ownership i should still get in right? nonetheless nykto is the owner and belongs to the group owned by those files.

--nykto.

---

