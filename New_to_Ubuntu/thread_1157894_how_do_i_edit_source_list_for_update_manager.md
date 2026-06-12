---
title: "how do i edit source list for update manager?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Matt26 on 2009-05-13
i am getting the attached error message when i go into update manager now in ubuntu 9.04 and i'm guessing i should just go ahead and remove these, assuming they are no longer needed?

where do i find the sources file for these repositories so i can remove them from the list?

thanks.

---

### Post by kerry_s on 2009-05-13
press **alt+f2**
type: **gksudo gedit /etc/apt/sources.list**

---

### Post by drs305 on 2009-05-13
You can also open Synaptic, then Settings > Repositories and untick the CD entry and ppa listings. The CDRom could be enabled on the Ubuntu Software tab, or it and the ppa listing could both be listed in the Third Party Software tab.

I'd opt for editing sources.list with the previously given command, but this is another way to do it for those that don't want to manually edit the file.

---

### Post by Paqman on 2009-05-13
System > Admin > Software Sources will also take you to the same place.

Before removing something due to a 404 you might want to try switching to a different server, too.

---

