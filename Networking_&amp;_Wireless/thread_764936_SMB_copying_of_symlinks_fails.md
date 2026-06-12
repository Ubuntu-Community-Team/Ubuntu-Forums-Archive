---
title: "SMB: copying of symlinks fails"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by MacUntu on 2008-04-24
I want to copy /etc from a Hardy machine to a sambashare on another Hardy machine (via Nautilus).

As soon as there is a symbolic link file, I get this error:

"Symlinks not supported by backend."

Hm? Symlinks not supported by GVFS? What do I need to do to simply copy the whole thing (with broken links, I don't care).

---

### Post by kidders on 2008-04-25
Hi there,

Microsoft's networking protocols have no concept of a symbolic link, so there's not much point in trying to use Samba to copy them. I would suggest:[LIST]
[*]not using Samba to share files between two Linux boxes, or
[*]tarballing your /etc and copying the tarball.
[/LIST]

---

