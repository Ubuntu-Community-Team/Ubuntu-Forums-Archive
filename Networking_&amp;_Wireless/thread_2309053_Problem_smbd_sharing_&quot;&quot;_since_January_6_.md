---
title: "Problem smbd sharing &quot;/&quot; since January 6 Updates [Server 12.04]"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by Ted_Friedl on 2016-01-07
I was sharing "/" without issue until recently where now smb clients (Windows 7 in this case) cannot descend into "/" subdirectories, e.g. "/tmp".

I robooted all machines involved which didn't help.

I suspect this update may responsible for the change:[INDENT]
[/INDENT]
[INDENT]Start-Date: 2016-01-06  07:51:03[/INDENT]
[INDENT]Upgrade: libsmbclient:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), libpam-winbind:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), smbclient:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), libwbclient0:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), libpam-smbpass:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), samba-common:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), samba-doc:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), samba:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), samba-common-bin:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13), winbind:amd64 (3.6.3-2ubuntu2.12, 3.6.3-2ubuntu2.13)[/INDENT]
[INDENT]End-Date: 2016-01-06  07:51:34[/INDENT]

My entry for "/" in smb.conf looks like this:
[INDENT][root][/INDENT]
[INDENT]        comment = root[/INDENT]
[INDENT]        path = /[/INDENT]
[INDENT]        writeable = yes[/INDENT]
[INDENT];       browseable = yes[/INDENT]
[INDENT]        valid users = friedl[/INDENT]

I can add subdirectories of "/" as shares and their subdirectories are "descendable", but my workflow depends on sharing "/".

Any suggestions?

tjf

---

### Post by Ted_Friedl on 2016-01-11
I think I found the bug.  I definitely found a workaround:

[https://bugzilla.samba.org/show_bug.cgi?id=11647#c7](https://bugzilla.samba.org/show_bug.cgi?id=11647#c7)  (See Comment 7)

tjf

---

