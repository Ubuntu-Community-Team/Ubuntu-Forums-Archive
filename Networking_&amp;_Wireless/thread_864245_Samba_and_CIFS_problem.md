---
title: "Samba and CIFS problem"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Solomoriah on 2008-07-19
I have just set up a new system with Ubuntu 8.04 in my home.  My home and office are wired together, and I replaced a Windows machine with the new Ubuntu system.  In my office I have a Fedora Core 4 system with Samba on it, from which I share files.

If I open a share on the office machine using Nautilus, it works fine; but if I smbmount a share I can browse directories, but every file access gives "Permission denied."  My local messages file (on the Ubuntu system) says:

Jul 19 10:37:19 home kernel: [14156.249172] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED

every time I try to copy or cat a file from the mounted share.  At debug level 2, the Fedora system's Samba logfile for this computer says:

[2008/07/19 10:39:09, 2] smbd/open.c:open_file(352)
  chrisg opened file fonts.tar.gz read=Yes write=No (numopen=1)
[2008/07/19 10:39:09, 2] smbd/close.c:close_normal_file(344)
  chrisg closed file fonts.tar.gz (numopen=0) 

In other words, the Fedora system says the file was opened, then closed just fine; but the Ubuntu system claims it's getting an error return.

These shares worked fine with the Windows 98 computer I just threw out.

---

