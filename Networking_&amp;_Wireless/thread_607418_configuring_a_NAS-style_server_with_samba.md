---
title: "configuring a NAS-style server with samba"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by sdellysse on 2007-11-08
I am trying to set up a pair of samba shares with the following properties:

two shares: DATA, INCOMING

one user has full read write access on both

the rest of the users:
have read access on DATA
read access on INCOMING, write access on their own files only (ie, if user a uploads a file, user b cannot delete it) or to create new files

the server will be able to list the shares without having a user log in, but no one will have access to the actual shares without logging in.

on the actual disks. I have a RAID5 mounted on /mnt/serverStorage.
the subdir data will connect to the DATA share
and the subdir incoming will connect to INCOMING

will I have to change any ownership or permissions to make this work?

I am fairly new to linux networking and I am not sure where to go from here.

any help would be appreciated

thanks,
Shawn

---

### Post by mpierce on 2007-11-09
Get your shares working using samba; you can think fine tune who has what type of access by setting the permissions in the /etc/samb/smb.conf file. 

1) Set it up to work
2) Fine tune later

Do a search on my name, mpierce in networking as I've posted several examples of a working smb.conf file on a linux machine with win access and printer sharing. 

Hope this helps...

---

### Post by sdellysse on 2007-11-09
> **mpierce said:**
> Get your shares working using samba; you can think fine tune who has what type of access by setting the permissions in the /etc/samb/smb.conf file. 

1) Set it up to work
2) Fine tune later

Do a search on my name, mpierce in networking as I've posted several examples of a working smb.conf file on a linux machine with win access and printer sharing. 

Hope this helps...

no ****. the problem with setting up samba is fine tuning it requires the configuration to change. i can easily export a whole folder as everyone read/write everything but that ruins the point of having nas.

---

