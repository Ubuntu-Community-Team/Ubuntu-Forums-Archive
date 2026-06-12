---
title: "Automount nfs space for users?"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by Greslore on 2008-01-29
I have a machine set up for LDAP Authentication.  I am using pam_mkhome to automagically create a local home directory for when users (there are over 1000 users) log in.  No problems here.  

Now, every user has NFS space that I would like to mount upon them logging in.  I dont want it mounted as their home, just to something like /data/username.  Any thoughts on how to do this?

---

### Post by mpokrywka on 2008-01-30
pam_mount looks like your solution, unfortunately documentation is lacking... but reading through config file reveals all options

---

