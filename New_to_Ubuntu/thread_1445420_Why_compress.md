---
title: "Why compress?"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by da burger on 2010-04-02
What's the point with compression? I've been testing out gzip and bzip2 with a tar archive of jpegs I have and it reduces the file size by about 1%. So why bother? Have I just got unlucky and have hard to compress files. Thanks in advance.
Angus

---

### Post by srs5694 on 2010-04-02
JPEGs are already compressed, so you'll get little or no compression on top of that by using gzip or bzip2, as you've discovered. Other compressed file formats include .deb package files, OpenOffice.org data files, MP3 music files, and most AV file formats (.nuv, .mp4, .mpg, etc.). If you try compression on most other files (plain-text files, program files that aren't packaged, MS Word .doc files, etc.), compression will reduce the file size by a substantial amount -- usually around 50%, but details vary depending on the file type and compression method.

---

### Post by da burger on 2010-04-02
Ah, thank you. I thought it might be something like that but wanted to check. Thanks again.
Angus

---

