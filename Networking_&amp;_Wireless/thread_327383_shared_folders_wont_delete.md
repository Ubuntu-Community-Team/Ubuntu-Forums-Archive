---
title: "shared folders wont delete"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by Ethos on 2006-12-29
Hello i recently shared a folder with a windows machine and now when i go into system>Admin>Shared folders and delete that one, then return to the menu its still there? any ideas why i cant get rid of it? Thanks ethos

---

### Post by kidders on 2006-12-29
Hi there,

I would just delete the appropriate section from my /etc/samba/smb.conf, and restart samba. Quick and painless. :-)

---

### Post by Ethos on 2006-12-29
I looked throught the samba config file and those paths that it is specifying in system-administration-shared folders are not in the config? any ideas where that could be stored? there still there I cant get rid of them :(

---

### Post by kidders on 2006-12-29
Curious. If they're not in smb.conf, the shares shouldn't actually exist though (assuming you've restarted samba). I imagine the admin tool is just trying to be helpful, by caching recently used share details for you.

---

### Post by Ethos on 2006-12-29
is there a way to clear the cache? and when I go to the directory that folder is in there is still a hand denoting it to be a shared folder...I delete it in system then close the dialog box then reopen it a second later its back? its realyl getting annoying

---

### Post by Ethos on 2006-12-29
bump...sorry i Just feel this is a security issue...

---

### Post by kidders on 2006-12-30
I'm still not 100% certain what you're referring to exactly, but I imagine that what you're referring to is either part of your own profile, or root's ... so there shouldn't be a privacy issue.

---

### Post by gldvxx on 2007-03-07
Did you ever get this issue resolved?  I'm having the same problem.  When I go to Administration->Shared Folders I keep getting different shares relisted even after i delete them.  I've tried restarting to no avail.  I looked in the smb conf file and even disabled ntfs and samba under Administration->Services.  Which conf file should I be looking at, besides Samba?  What does "Shared Folders" read from?

FIXED!

sudo gedit /etc/exports

i deleted the line that was entered there and the share dealio didn't reload.  yay!

---

### Post by kidders on 2007-03-07
> **gldvxx said:**
> sudo gedit /etc/exportsThat file handles NFS shares, rather than Samba ones.

Glad you solved your problem. :-)

---

### Post by gldvxx on 2007-03-07
yah i knew where to edit the samba stuff, but i wasn't sure where to edit the nfs stuff AND  i thought maybe "Share Files" was reading from some OTHER conf file (can you tell i'm used to mac os x..!?).  once i knew what i was googling for i had a much easier time finding the solution!

---

