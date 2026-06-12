---
title: "Unable to load dynamic library - extension directory not found"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by lesterp on 2011-08-31
Hi,
I'm running a php script from the cli and get the error messages that various dynamic library files aren't loaded due the extensions directory not found. However, the extension directory does exist with the *.so files and it is as specified in php.ini (both cli and apache versions). Even locate can find the files in said directory (20090626+lfs).

I was originally loading ffmpeg-php but things went wrong and had to re-load php.

I would be extremely grateful for some pointers.

Many thanks,

Lesterp

---

### Post by lesterp on 2011-08-31
Hi,
All sorted - had re-install ffmpeg-php**5** via apt
Thanks
Lesterp

---

