---
title: "Is there a way to receive a file with 755 already set?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by adit on 2009-10-06
I want to send a script to somebody by email.  Before sending it has permissions set as 755.
After the recipient has downloaded the script to his computer, its permissions are automatically changed to 644..  So the recipient needs to type "chmod +x" before executing the script.
Where exactly the change of permissions from 755 to 644 is accomplished? (in sender's computer? in the mailservers? or in the recipient's computer?)
Is there a way to receive the script with 755 permissions already set?

---

### Post by freak42 on 2009-10-06
I *think* that permissions are a feature of the OS/Filesystem and not of the file itself, therefore it is not really sendable to someone (maybe there is an archive type that also saves the permission, however I don't know of one that does this for sure)

hth

---

### Post by alphaniner on 2009-10-06
The permissions he is seeing are due to the umask, I think.  A 7zip archive should work, it saves permissions but not user/group ownership.

---

### Post by Sarmacid on 2009-10-06
Compressing it as .tar.gz should preserve the permissions.

---

### Post by alphaniner on 2009-10-06
But it will also preserve ownership, no?

---

### Post by Sarmacid on 2009-10-06
Actually I'm not so sure how that will work, and I almost didn't post because of that. But reading [http://en.wikipedia.org/wiki/Tar_(file_format)#File_header](http://en.wikipedia.org/wiki/Tar_(file_format)#File_header) it seems the the owner would be the one with the same user ID in the new system.

---

