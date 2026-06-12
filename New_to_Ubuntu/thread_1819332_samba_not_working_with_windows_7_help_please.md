---
title: "samba not working with windows 7 help please"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-08-05
have samba set up as pdc and was working tell windows said it could not talk to domain controler

did a look and found

e:~$ sudo service smbd status
smbd stop/waitingn

e:~$ sudo service smbd start
smbd start/running, process 2193

e:~$ sudo service nmbd status
nmbd stop/waiting

e:~$ sudo service nmbd start
start: Job failed to start


no samba log folder in /var/log

used synaptic to reinstall samba and all its parts
used Users and Groups to remove machine MOMHP$ account but saved the files just in case
sudo service smbd restart
sudo service nmbd restart

now can to readd windows 7 to samba pdc keeps saying bad user name or passwd. Have used sudo smbpasswd -a user to make shure i was using the correct passwd.

have user set up to add windows machines to domain

log files are in logs.zip attached

---

### Post by lance bermudez on 2011-08-08
changed win7 computer name and was able to join the domain. Now have problem with users logging in attach is the pic and samba logs.

---

### Post by lance bermudez on 2012-02-05
I was hopping that someone would have said something by now. Any one have any ideas?

---

### Post by mastablasta on 2012-02-06
probably because not many people have it and those that do have it don't really visit this forum (or at leats not the absolute beginners part of forum). Have you tried posting in server section of the forums?
 
seems complicated...
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)
 
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)

---

