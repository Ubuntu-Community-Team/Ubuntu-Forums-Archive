---
title: "Security check positive?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jorge ortega on 2009-01-14
I ran Tiger as a security check and this is what I got:

"08:18> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'fuse.gvfs-fuse-daemon' used by 'gvfs-fuse-daemon' is not recognised as a local filesystem"

On the other hand when i try to read the HTML report produced the browser shows it blank
Could anyone help please?

---

### Post by perlluver on 2009-01-15
> **jorge ortega said:**
> I ran Tiger as a security check and this is what I got:

"08:18> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'fuse.gvfs-fuse-daemon' used by 'gvfs-fuse-daemon' is not recognised as a local filesystem"

On the other hand when i try to read the HTML report produced the browser shows it blank
Could anyone help please?

Those are both part of the Gnome/Linux filesystem.  They are not a security problem.  Not sure why a FreeBSD clone would find them as a security problem.

---

### Post by jorge ortega on 2009-01-16
Thanks perluver, you gave me peace of mind

---

