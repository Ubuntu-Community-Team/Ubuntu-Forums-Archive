---
title: "How to access shared drives from guest without admin passward?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by jibuntuu on 2011-05-06
Hi,
I have been using Ubuntu since Jan-2011 and I am a gr8 admirer of the os. I have created 3 different drives to store my data and every time someone access the drives from the guest account he/she needs my admin password to access. Is there any way out so that they can access some of my drives without the admin passward...

kindly reply..
Jibuntuu:confused:

---

### Post by Jonny87 on 2011-05-06
I'm not 100% sure as I have never had this situation but try the following.

Got to "Users and Groups"

Then select the user in question, then click "Advanced Settings".

There you should see a "User Privileges" tab. Check the setting there.

All the best.

---

### Post by adit on 2011-05-06
Which version of ubuntu you are using?  Is it ubuntu 11.04 (latest version)?
Don't login through guest session provided with the default installation of ubuntu 11.04.  Create a new user and follow the steps in post#2.

---

### Post by An Sanct on 2011-05-06
Since he mentioned January 2011, I would guess it is 10.10 Maverick Meerkat.

---

### Post by adit on 2011-05-06
> Since he mentioned January 2011, I would guess it is 10.10 Maverick Meerkat.
He is just using ubuntu from that time.  Now he may upgraded his ubuntu

---

### Post by Morbius1 on 2011-05-06
> I have created 3 different drives to store my dataHow are they formatted: NTFS, FAT32, EXT3, ....
How are they mounted: Through nautilus, in fstab, ....
Are the drives internal or external ?
> every time someone access the drives from the guest account he/she needs my admin password to access.Define access please.

The ability to read any file in those partitions?
The ability to add to and delete any file?
The ability to add to, delete, and edit any file?

This could get complicated ;)

---

