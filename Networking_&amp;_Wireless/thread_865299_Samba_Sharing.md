---
title: "Samba Sharing"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2008-07-20
Hi there,

When I enable a share on my desktop pc - the share shows up on the XP machines, but upon trying to copy ANYTHING from the share I get an access denied error? When trying to copy folders, Windows creates the directory structure but no files are accessible and so not copied. 

When I manually set the file and folder permissions to be read/write/execute by anyone the problem goes away. 

Is there still no easy/noob friendly way to share folders on Ubuntu or am I screwing something up? All that I do is right-click on the folder -> sharing options and then I tick all the ticks?

Thanks for any replies or comments,

Rudolf

---

### Post by superprash2003 on 2008-07-20
you would have to uncheck "read only" to get write access

---

### Post by MrFSL on 2008-07-20
As far as newb friendly - I would not recommend Windows File Sharing (Samba). There are a great number of ways to share files and I don't think for a second that Samba makes my list.

What about ssh (sftp / scp)? In Windows I would use winscp.

---

### Post by RudolfMDLT on 2008-07-21
> **MrFSL said:**
> As far as newb friendly - I would not recommend Windows File Sharing (Samba). There are a great number of ways to share files and I don't think for a second that Samba makes my list.

What about ssh (sftp / scp)? In Windows I would use winscp.

LOL! Yeah - I use WinSCP to access my boxes remotely but it still sucks as far as Windows users are concerned!

Thanks for the feedback,

Cheers,

Rudolf

---

