---
title: "How to enable nouveau 3d support?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by eragon100 on 2010-04-30
Hello!

I know that nouveau Nvidia drivers have experimental 3d support, and that you can enable this support on ubuntu 10.04 by installing a couple of packages. But how do you do it, exactly? ;)

---

### Post by ibuclaw on 2010-04-30
See here: [https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

Try at your own free will. And do note that it isn't officially supported. :)

Regards
Iain

---

### Post by eragon100 on 2010-04-30
> **ibuclaw said:**
> See here: [https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

Try at your own free will. And do note that it isn't officially supported. :)

Regards
Iain

It works fine, but that is software rendering. I want to know how to enable the gallium 3d drivers :)

---

### Post by ibuclaw on 2010-04-30
> **eragon100 said:**
> It works fine, but that is software rendering. I want to know how to enable the gallium 3d drivers :)

that *is* gallium, and 3D should start just fine :)

Nouveau is not capable of hardware acceleration ... yet.

---

### Post by eragon100 on 2010-04-30
> **ibuclaw said:**
> that *is* gallium, and 3D should start just fine :)

Nouveau is not capable of hardware acceleration ... yet.

Yes it is, read this news piece from the 17th of Februari: [http://www.phoronix.com/scan.php?page=article&item=nouveau_gallium3d_first&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_gallium3d_first&num=1)

---

### Post by jd65pl on 2010-04-30
From the nouveau page on freedesktop.org

[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

> Any 3-D functionality that might exist is still unsupported. Do not ask for instructions to try it. But you can read GalliumHowto in case you are brave enough

If you want hardware 3D acceleration use the prop drivers for the time being

---

### Post by undoIT on 2010-06-04
I tried adding the ppa, but there were no new packages to install. Is there something else that needs to be done? Also, is it possible to enable desktop effects with the nouveau experimental drivers? I tried this in Fedora 13 recently and it worked pretty well, but I'd rather use Ubuntu.

---

