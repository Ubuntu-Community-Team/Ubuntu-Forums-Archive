---
title: "How can I repair my xorg.conf?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by henriquelm on 2010-01-31
Can you guys tell me how can I repair the xorg.conf file?

The installation of the ATI driver messed up my xorg.conf. So since I didn't have a backup copy of xorg.conf anyway, I decided to delete my xorg.conf and type "sudo dpkg-reconfigure xserver-xorg" to see if it would create a new xorg.conf, but nothing happened.

What should I do?

---

### Post by audiomick on 2010-01-31
I've read about people booting into the live CD, copying the xorg.conf from the live environment and pasting it into the install.
I don't really know if it works, but it sounds like it should.

---

### Post by Ocxic on 2010-02-01
could just delete it. xorg.conf isn't really used since 9.04

---

### Post by audiomick on 2010-02-01
> **Ocxic said:**
> could just delete it. xorg.conf isn't really used since 9.04

Not quite true. The file is not present and not needed on many 9.10 installs, but if present, it will be used. The nVidia setup tool writes one, if not always, then often, and it is used.

---

### Post by HiImTye on 2010-02-01
[LIST=1]
[*]delete it (done)
[*]open up your video configuration tool (nvidia/ati/whatever)
[*]choose to save to file or w/e
[*]viola
[/LIST]

---

### Post by henriquelm on 2010-02-01
> **HiImTye said:**
> [LIST=1]
[*]delete it (done)
[*]open up your video configuration tool (nvidia/ati/whatever)
[*]choose to save to file or w/e
[*]viola
[/LIST]

Thanks Tye, it solved the problem. Well at least I have my xorg.conf back.

Also thanks to audiomick and Ocxic.

:D

---

