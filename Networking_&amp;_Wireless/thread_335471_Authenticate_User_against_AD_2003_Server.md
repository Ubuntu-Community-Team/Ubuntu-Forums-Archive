---
title: "Authenticate User against AD 2003 Server"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by lwoodtri on 2007-01-10
Hello,

I have followed some of the articles on getting user accounts to authenticate against a Windows 2003 Server Domain.  I have gotten the authentication to work, the only problem I have is that the accounts are required to be in the passwd file.  That kind of defeats the purpose of Domain Authentication if I have to add each user to the local machine's password file before it will authenticate to the Windows Domain structure.

I have seen different scenarios and directions but not a solid howto to make this work.  Some have said to add the WSFU3.5 and others have said it is not necessary for Windows 2k3 server, that the schema is already compliant.  

I just need some direction on how to progress to make a linux server authenticate a user account without having to add it to each Ubuntu Server's local passwd file.

Thanks in advance.

---

### Post by guysmiley on 2007-01-16
We're looking to do the same and would love to see a solid "how to" on AD authentication.  Please post the resources you used to make this happen.

Of course, we too cannot be updating pwd files with all user IDs and pwds (we have over 3000 users).

Any direction is appreciated!

gs

---

