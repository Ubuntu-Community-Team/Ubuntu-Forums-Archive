---
title: "Samba - moving files, etc."
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2006-09-03
I have Samba installed on two of my Ubuntu Dapper workstations.

I can see all of the folders and files in the home folder from each machine to the other BUT I can not move/copy contents from one machine to the other.

Am I not supposed to be able to do this ?  Otherwise what good is it to just be able to view contents of one machine from another.

Is there some parameter here that I am missing ?

Thanks.

---

### Post by mssever on 2006-09-03
Please post the contents of /etc/samba/smb.conf, censored as necessary to protect private info.

---

### Post by Iowan on 2006-09-03
> **wpshooter said:**
> Am I not supposed to be able to do this ?  Otherwise what good is it to just be able to view contents of one machine from another.
I have Samba on a Ubuntu server and this Ubuntu workstation (and on another non-Ubuntu server).  I can move files around between them.

---

### Post by wpshooter on 2006-09-04
It turned out that **MY** solution was to add **WRITE** permissions to **GROUP** & **OTHER**.

And it seems that I have to give write permissions to **BOTH** of these because when I tried each one individually it would not allow me to move files/information.

Can someone tell me what **GROUP** & **OTHER** are exactly ?

Can enabling either or both of these cause any security issues ?

Seems like to me that there would be a better way of accomplishing this.  Seems like that there would just be a check box on the sharing setup diagonal that would grant you this ability or not.

Thanks.

---

### Post by rbprogrammer on 2006-09-04
when you say you want someone to tell you what GROUP and OTHERS are, i assume you already know what OWNER is.

OWNER - the owner is one user that owns the file

GROUP - a group is a group (or could just be one user is only one user is in a peticular group) that is associated with that file.

OTHERS - others is every body else that has no association with that file.

the GROUP and OTHERS options are useful when you want other users the ability to just read a file, write a file, or just execute a file.  or sometimes all of those or sometimes none of them or sometimes a combination.  all of these are made for permissions.

i think that is what you were asking.  if not, sorry to waste your time :-|

---

