---
title: "Upgrade to 10.10 Gnome-do won't start"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by DeputyClicks on 2010-10-28
I just upgraded to 10.10. After the upgrade Gnome Do no longer starts. When I open it in a terminal this line is repeated over and over again:

>   at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
What other information should I provide? What went wrong?

---

### Post by directhex on 2010-10-28
Try erasing the .do folder, ~/.local/share/gnome-do/

---

### Post by DeputyClicks on 2010-10-28
That worked. Thanks directhex.

---

