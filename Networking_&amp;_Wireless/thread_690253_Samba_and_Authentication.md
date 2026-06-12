---
title: "Samba and Authentication"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by yubu on 2008-02-07
I was having a problem with username/pass requierments when I'd access the share from a Windows PC. So I've edited the smb.conf file... switched User with Share and the Guest account from Nobody to my Account. I can access the share now, but I'd actually like there to be some authentication. We have visitors on the network and I don't want them to have access to the Samba share. Any help would be appreciated.

---

### Post by freebeer on 2008-02-07
I guess the proper thing is to figure out why your were having problems logging in in the first place.  Did you add user and machine accounts on the Samba machine?

---

### Post by yubu on 2008-02-07
Yes I have added accounts under System > Administration > Users and Groups. Machine accounts?

---

### Post by Iowan on 2008-02-07
You'll also need to add them to Samba.

---

### Post by yubu on 2008-02-07
I have it all figured out... a little searching goes a long way :)

---

### Post by Iowan on 2008-02-07
GREAT!!! Tell us what you found and mark this one [SOLVED]!

---

### Post by EnsignR on 2008-02-09
> **yubu said:**
> I have it all figured out... a little searching goes a long way :)

and posting the solution, or even just a link to it, goes even further!

I have the same problem, know the solution, but can't remember the command to add a user to samba, and so far my searching isn't helping..

but using google with site:ubuntuforums.org found it straight away.. damned vBulletin search function

[http://ubuntuforums.org/showthread.php?t=406133](http://ubuntuforums.org/showthread.php?t=406133)

---

