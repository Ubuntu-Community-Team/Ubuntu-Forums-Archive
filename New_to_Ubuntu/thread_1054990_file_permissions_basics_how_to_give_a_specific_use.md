---
title: "file permissions basics: how to give a specific user permission to a file?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by lumix on 2009-01-30
I asked this before, but I'm pretty sure the way I asked it had confused folks. How is the following situation typically handled:

The Accounting department (or some member thereof) has created a file called Foo.txt.   All members of the accounting group have been given rw permissions, (say, chmod 660).  Fine, but now Bob from HR, and Alice the president need rw permissions too, but neither of them should be added to the accounting group, of course (who says they should have access to *all* accounting files?).

The two options I can think of are

1) ACL's  -- but this appears to be *a*-typical from what I've read and not at all common-practice in IT depts. around the globe.  Either way, is it the *most* common practice?

2) Make a separate group for the file and enjoin the necessary members -- this seems wildly impractical given the necessary time and effort to manage a group for each and every file, and the confusion that it would create when viewing a user's profile (being potentially member to dozens of groups).

Another way to put this:

 in Windows you simply add a user and specify their permissions--whether through CACLS or via the gui tabs.  How do I "add a user" to a file and specify their rights in  Linux?

---

### Post by Gulyan on 2009-01-30
Most of the Unix like systems have support for user/group access rights.
The NTFS has ACL.

To solve your problem, you should chose option 2 (add them to another group)

---

### Post by handydan918 on 2009-01-30
In the alternative, you could modify the file, such that your wanna-bees are either the owner of the file, or the file is owned by their group. Sometime a file owned by "root" fools people into thinking it has to stay that way for root to access it.

---

### Post by lumix on 2009-02-01
But all too often the requirements for user access tend to be a bit more elaborate than my example.  Accounting's foo.txt may require that Joe and Fred also have access, even though they aren't members of the accounting group--and shouldn't be, since they don't need access to any other files owned by accounting.

Another way I to put this: a file may need access from 3 different groups and, say, two users who aren't members of any groups.  Do folks really create new groups--specific to such a file (of which there are many in practice)--for each file that has multiple group access requirements?

Am I just asking this wrong?

In any case, I appreciate the responses.

---

