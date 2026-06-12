---
title: "Cannot set samba access by group in 7.04"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by prawn on 2007-04-22
I have just upgraded from Dapper Drake to Feisty Fawn. An exact copy of my smb.conf no longer allowed me to access all shares. A bit of experimentation revealed that

valid users = @users

no longer provided access to users in the group users. Changing this to

valid users = fred joe jack

did work. A bit of googling revealed this [https://bugzilla.samba.org/show_bug.cgi?id=4145](https://bugzilla.samba.org/show_bug.cgi?id=4145) samba bugpost, but there was some implication that this was specific to a libc problem on Fedora Core. Anyone else seen this? Any suggested fixes?

---

### Post by prawn on 2007-04-22
I've rolled back to 6.10 and the problem has gone away. So either 6.10 is using a different version of samba without the problem, or there's a problem with feisty.

---

### Post by ThomasMarkas on 2007-04-22
I have just upgraded several computer in the house to Feisty from Edgy, including a machine I use as a file server. All the SAMBA shares no longer work. OK for a few days, but a work around for this would be welcome.

---

### Post by ThomasMarkas on 2007-04-22
This small nugget of information may help someone. Looking at the logs, from this morning a working entry looked like

desktop1 (192.168.0.170) connect to service hda4 initially as user mark (uid=1000, gid=1000) (pid 4636)

and now it looks like and fails.

desktop1  (192.168.0.170) connect to service hda4 initially as user nobody (uid=65534, gid=65534) (pid 6760)

---

