---
title: "CUPS printing error"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by GoCool on 2008-12-20
Hi All,
I am trying to configure my Konica Minolta BizHub C250 printer. But its giving me the following error. 

> "Unable to start filter "femperonpsc250mu.pl" - No such file or directory."

Any help on this would be highly appreciated.

:confused:

---

### Post by cmnorton on 2008-12-20
Here is a link:

[http://ubuntuforums.org/showthread.php?t=169172&highlight=samsung+scx-4100](http://ubuntuforums.org/showthread.php?t=169172&highlight=samsung+scx-4100)

---

### Post by yeKcim on 2009-02-05
Did you succeed? I've got same problem with Konica Minolta BizHub C353 printer

---

### Post by yeKcim on 2009-02-05
I have found.

sudo cp where/is/thefile/femperonpsc250mu.pl /usr/lib/cups/filter/femperonpsc250mu.pl

Restart, retry to install.

---

### Post by GoCool on 2010-10-04
thank you that worked.

---

