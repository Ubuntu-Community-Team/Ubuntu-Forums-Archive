---
title: "SMB Share via Nautilus"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Greslore on 2008-11-07
I am trying to connect to a Windows server on a Windows network but am having some difficulty.  The Windows server is set up so that there is a parent directory I do not have access to (blah$) and mydata is a directory under this that my username has full access to.  I've gotten it to work before, so I am guessing its just semantics at this point.  

In Nautilus, I do:
smb://server/blah$/mydata

I also tried using under PLACES > CONNECT TO SERVER > WINDOWS SHARE:
Server: servername
Share: blah$
Folder: mydata
User Name: myusername
Domain Name: mydomainname

But to no avail.  Any thoughts or ideas?  I also am not the not sys admin for this Windows server, so I can't change anything Windows serverside.

---

### Post by bab1 on 2008-11-07
> In Nautilus, I do:
smb://server/blah$/mydata

Try this --  
```
smb://server/mydata
```

---

### Post by Greslore on 2008-11-07
Tried it.. no go :(

---

