---
title: "Helpl with changing files on Shared Folders"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by BioChick87 on 2007-02-10
Ok, so I figured out how to put things in Shared Folders so I can see them with Windows computers, and I did "smbpasswd -a username" so they can login to view the files, and it works!  But they can't change my files it says "Access is denied".  How do I make it so I can change files or move them?

---

### Post by meng on 2007-02-10
What are the permissions on these files? If "others" don't have write access, then you can't write changes.

---

### Post by BioChick87 on 2007-02-10
> **meng said:**
> What are the permissions on these files? If "others" don't have write access, then you can't write changes.

I'm not sure what you mean.  If I am on the actual computer that has the files I can edit them and create new files, but if I am on another computer looking at them through the network I cannot.  I can just view them.  It says Access is denied if I try to change anything.

---

### Post by meng on 2007-02-10
Every file on a Linx system has read-write-execute permissions for the owner-group-other users. If you connect from another computer, you're recognized as an other user, not as the owner. A google for "linux file permissions" should help you out.

---

### Post by BioChick87 on 2007-02-10
> **meng said:**
> Every file on a Linx system has read-write-execute permissions for the owner-group-other users. If you connect from another computer, you're recognized as an other user, not as the owner. A google for "linux file permissions" should help you out.

I'm logging in as the same username and password, though.  Shouldn't it be the same?

---

### Post by meng on 2007-02-10
I do the same and it doesn't work for me unless I change permissions. However, there may be another solution to the problem

---

### Post by BioChick87 on 2007-02-14
Oh, duh.  Under System-->Administration-->Shared folders it shows all shared folders.  If you click on one and click the Properties button, there is a check box for "read only".  If you unclick it and then reboot, you can change things again.

But why does it say "Do you want to open this file?" when I try to open things?  It is the same window that it shows for Internet Explorer.  How do I turn that off?

---

