---
title: "Automount specific dir for each user on logon?"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by Elijah on 2005-10-13
Kinda like roaming profiles or something ... I've never done this before .. 

I've successfully setup LDAP and added entries through LAM, I could authenticate users via ldap but my main task should be auto-mounting a specific directory for each user (e.g. /home/username/) 

Can use something like an app that automounts an nfs share?

localuser@localhost$ su ldapuser
Password: ******
(client automatically gets a mounted /home/ldapuser nfs share from the server)
(#mount -t nfs server02://home/$username /home/$username)
ldapuser@localhost:$ cd ~/
ldapuser@localhost:$ pwd
/home/ldapuser/ 

what else can I use?

---

