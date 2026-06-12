---
title: "Windows XP computer does not access Ubuntu computer"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by Eiríkr on 2008-04-07
Your post is a bit confusing, but I think what you want is this:
[list][*]Printer attached to XP, usable from Linux
[*]Files located on Linux, accessible from XP[/list]

Is this correct?  if not, could you elucidate?

Samba should be able to help you do both, though there are two sides to this equation.  On one side, Linux is acting as a client to the printer share provided by Windows.  I'm not savvy on printer sharing, so someone else may need to pitch in.  Your smb.conf file is mostly irrelevant to this.  

On the other side, Linux is acting as the server with Win XP as the client to files shared from your Linux machine.  This I can help with, and your smb.conf file is exactly what we'll need to take a look at.  Please open a terminal on your Ubuntu machine, type in the following, then copy and paste your smb.conf file into a post here in this thread.  (Please enclose the smb.conf file contents in [noparse]```

```[/noparse] tags.)
```
less /etc/samba/smb.conf
```

Cheers,

Eiríkr

---

