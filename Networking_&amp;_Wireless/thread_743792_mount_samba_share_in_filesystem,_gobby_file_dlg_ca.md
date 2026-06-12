---
title: "mount samba share in filesystem, gobby file dlg can't browse smb:// or desktop mount"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-04-03
My users are excited to try gobby-.4.5 on Ubuntu 7.10 Gutsy (and 8.04 Hardy in a few weeks).

The sobby server is running on host server1, and the files are available to the currently mixed network via SMB at \\server1\myfiles.

The Windows users map drive X: to \\server1\myfiles, and can open the documents in Gobby normally.

The Ubuntu user could not find a way to access the smb share in the Gobby file chooser dialog.

This share is easily available from nautlus, e.g. as a places | network | workgroup | server1 | myfiles share, via 'connect to server...' and generall as smb://server1/myfiles.

Any special way I can mount this semi-permanent share so that this variety of file dialog can access it?

Instead of a screenshot, I'll describe it:
"Open New Document"
page+pencil icon: Type A File Name | path component buttons
places | name
cancel | OK.

Seems pretty commonplace, and not unmodern. Is this solely a Gobby problem, that its not VFS enabled?

If so, back to the question, can I make some more explicit smb mount that will always provide access to the share?

Thanks,
Jeff

---

### Post by dmizer on 2008-04-03
see the second link in my sig. :)

---

