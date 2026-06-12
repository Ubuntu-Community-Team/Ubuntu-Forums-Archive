---
title: "Weird Sharing Issue"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by Fangknot on 2006-09-12
Before I installed Ubuntu on my main computer, I could read/write on my shared drives in my spare computer and my roommates. Both the spare and roommate are using WinXP.

After Ubuntu install, I can only read/write to my roommates drive. I can see  the spare listed in Network Servers. When I try to access the spare machine I get.

Sorry, couldn't display all the contents of "Windows Network: storm".

Any ideas?

---

### Post by tbonius on 2006-09-12
Read Samba Docs.  Make sure the entire Samba and SMBclient packages are installed.  Configure smb.conf accordingly.  Also try direct connection to SMB computer name.  Connect to remote server:

smb://computername

T

---

### Post by Christopher Cook on 2006-09-13
I've had that issue. After a reload on the page it was fixed.

---

