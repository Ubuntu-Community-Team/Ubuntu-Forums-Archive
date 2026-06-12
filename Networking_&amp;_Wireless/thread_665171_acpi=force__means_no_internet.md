---
title: "acpi=force  means no internet"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Lord Banshee on 2008-01-12
I had internet problems today (could not connect to the internet)  and i figure out it was due to i had acpi=force so ubuntu will automatically turn off my old P3 machine i am using it on.

Using 7.10, any help to solve both problem at once?

---

### Post by jimrz on 2008-01-12
Not sure what machine you have, but my old ThinkPad 600x (PIII 500) has to use "acpi=force". However, that killed function of my pcmia slots (wifi card or nic, etc) which I corrected by also adding "pci=noacpi", also, to the boot parameters. Hope it helps.

---

### Post by Lord Banshee on 2008-01-12
thanks,

I actually found that in another thread before i read your response. But i do think it indeed fixed my problems... only time will tell.

Thanks,
Chris

---

