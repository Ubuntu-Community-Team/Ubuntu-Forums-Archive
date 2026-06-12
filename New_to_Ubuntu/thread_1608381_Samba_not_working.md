---
title: "Samba not working"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by I8NY on 2010-10-29
Okay i'm setting up a Ubuntu server with Samba file sharing to host backups and other misc. files.  I have samba4 because that is what the server uses but when i try to use the network in nautilus i get the common failed to mount error.  Now i can get samba to work if i type "smb://iptoconnect" in firefox.  I followed many Samba guides so i think i have all the settings down but it only works in firefox.  What did i forget do? :(  Thanks for your time.

---

### Post by I8NY on 2010-11-20
I figured it out. I had to change &#8220;;   name resolve order = lmhosts host wins bcast&#8221; to &#8220;name resolve order = lmhosts wins bcast[COLOR=Black]host&#8221; in the smb.conf.  Then had to edit the /etc/hosts file to correct the IP for my network local host.  This fixed the problem.  I hope this helps some one down the road.[/COLOR]

---

