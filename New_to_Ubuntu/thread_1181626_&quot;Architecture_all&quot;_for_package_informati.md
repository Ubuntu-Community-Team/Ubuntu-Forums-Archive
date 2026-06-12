---
title: "&quot;Architecture: all&quot; for package information ?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by PGScooter on 2009-06-08
Hi, what does "Architecture: all" mean? Does it mean that it's the same deb for both 32 and 64-bit Ubuntus? If so, then does that mean that the software does not take advantage of the 64-bit processor, or not necessarily? Thanks

---

### Post by ad_267 on 2009-06-08
Usually it means the package doesn't contain any compiled binary files so it is suitable for all platforms. For example it may contain a python script or graphics.

---

### Post by PGScooter on 2009-06-08
when I type in ```
apt-cache show xpdf
```, it shows this message, so that means that xpdf was made with bash and/or python scripts?

---

### Post by 3rdalbum on 2009-06-08
> **PGScooter said:**
> Hi, what does "Architecture: all" mean? Does it mean that it's the same deb for both 32 and 64-bit Ubuntus?

Think bigger. Ubuntu runs on ARM; the package will install and work on ARM. There are community versions of Ubuntu for SPARC, Itanium, and PowerPC (and probably others). The package will work on these. If Ubuntu was ported to some other sort of processor, the package will work on that too.

You're right that the program won't be optimized for 64-bit, but the program inside the package is probably written in an interpreted language, so it wouldn't have been optimised for anything anyway.

---

### Post by ad_267 on 2009-06-08
> **PGScooter said:**
> when I type in apt-cache show xpdf, it shows this message, so that means that xpdf was made with bash and/or python scripts?

I don't think xpdf actually contains anything. It just depends on other packages.

> Depends: xpdf-reader, xpdf-utils, xpdf-common
> This package is intended for compatibility with previous versions of
 this package only. You can safely remove it from your system.

---

### Post by PGScooter on 2009-06-09
great, thanks for the info

---

