---
title: "autofs permissions"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by TJCIB on 2008-08-03
I am using autofs to mount the /home directory when a user logs in through NIS.

Right now, when the /home partition mounts, the user can SEE and READ all other files in other users' /home directories.  They can open text documents, etc.  They cannot CHANGE those files (make changes to the text document then save the changes).

While changing other people's files is the biggest concern, it is still preferable that they cannot even see the files of others.

Any suggestions on how to do this?  I checked out the man pages for autofs, automount, and auto.master, and either I'm confused, missing something, or those aren't helpful for this (most likely confused and missing something).

I appreciate any help.

---

### Post by TJCIB on 2008-08-04
Basically, are the mount options the same as when mounting NFS or any other file system?

What option is it to check directories against user IDs?

---

### Post by TJCIB on 2008-08-18
I hope a week-long bump is ok

---

### Post by mjbauer95 on 2009-10-11
Same problem here.

---

