---
title: "having some problems with my smb shares"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by onesojourner on 2006-10-29
I am having some problems with my smb shares. 

first drive 100 gigs
hda5 = ubuntu edgy install
hda7 = storage - used the gui to share 2 folders one works and one asks for a password and I created them at the same time in the same way both are ext3 ](*,) 

second drive 160 gigs
hdb1 (only one partition on this one) ntfs. trying to share 2 folders both say share unavailable. also created at the same time as the above 2 drives. ](*,) 

this set up worked great with breezy (never got it to work with dapper). edgy is getting me closer but still not working right. I just don't understand why only one of these folders is working when all four folders were shared the same way. I would greatly appreciate getting this salved this time around so any help you can give me would be great.

---

### Post by kidders on 2006-10-29
Hi there,

Could you post the relevant parts of your smb.conf, so we can take a look?

---

### Post by onesojourner on 2006-11-02
sorry it took me so long to get back to you on this. here is my smb.conf

this one works
[homemovies]
path = /media/storage/homemovies
available = yes
browsable = yes
public = yes
writable = no

says not avaible
[movies]
path = /media/bigdrive/media/movies
available = yes
browsable = yes
public = yes
writable = no

says not avaible
[MP3]
path = /media/bigdrive/media/MP3
available = yes
browsable = yes
public = yes
writable = no


asks for user name and password
[musacmp3]
path = /media/storage/musacmp3
available = yes
browsable = yes
public = yes
writable = no

---

### Post by kidders on 2006-11-02
That all seems okay. Have you checked to make sure the right users have access to the right files?

[LIST]
[*]For public shares, the user samba maps guests to must at least have read access to the data.
[*]For other shares, the user you authenticate as must at least have read access.
[/LIST]

Your samba logs may (or may not!) provide you with clues as to what's going on.

---

### Post by Iowan on 2006-11-02
You might check the permissions for those directories (and their parents).  Take special note of the differences between **/media/storage/homemovies** and **/media/storage/musacmp3** (since one works and the other somewhat works).

---

### Post by onesojourner on 2006-11-03
> **Iowan said:**
> You might check the permissions for those directories (and their parents).  Take special note of the differences between **/media/storage/homemovies** and **/media/storage/musacmp3** (since one works and the other somewhat works).

ok you got that one right. both shares on my storage drive are now working. looking at the file permissions on my ntfs drive (big drive) it says others folder access none, but it is greyed out so I can not change it. it says owner is root is there any way to sudo my way through and change the permissions?

---

### Post by Iowan on 2006-11-07
There's a How-To on mounting NTFS drives around here somewhere.
(BTW, I was born in Springfield and raised 50 miles ESE - about halfway to West Plains)

---

### Post by onesojourner on 2006-11-08
thanks I did some searching and figured it out.


wow thats awesome that you grew up around here, there are not many *nix people around.

---

