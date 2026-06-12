---
title: "Text files when building a package"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by with23nails on 2011-02-14
Source code usually comes with various text files (README, INSTALL et al). What should I do with those? Include all the information from them in relevant files in [FONT=Courier New]debian/[/FONT] (after issuing [FONT=Courier New]dh_make[/FONT]) and delete the original files? Or should I include all the information but leave original files where they are?
I tried to find the answer in [Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide") but it appears that this issue is omitted there...

---

