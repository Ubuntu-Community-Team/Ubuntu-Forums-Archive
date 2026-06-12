---
title: "rEFIT Boots Linux instead of Win7, Grub in MBR"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Awalker47 on 2010-07-04
Hello, I've got MacOSX, Win7, and Ubuntu 10.04 installed on my MacBook Pro using rEFIT to boot between the three. After installing Win7 I no longer got the Linux option on my rEFIT boot menu so I  reinstalled GRUB2 from the liveCD. Now it appears I've installed GRUB into my MBR and selecting windows from the boot menu brings me into Ubuntu. Can anyone help walk me through a fix? Booting to MacOS or Ubuntu works just fine.

Thanks in advance!

---

### Post by yetiman64 on 2010-07-04
As a starter, and in case you haven't already seen this, please check this [--LINK--]("http://refit.sourceforge.net/help/windows_boots_linux.html"). May be important info for your situation.

I'm not familiar enough with your setup to walk you through the whole process (others here will be of more help), but I can say from experience that grub2 _does not_ like being installed to a partitions boot records (as suggested in the link) and caused me severe problems until put in the MBR. However LILO may be a possible substitute for you (not 100% sure though).

Good luck.

---

### Post by Awalker47 on 2010-07-05
Thanks, that's actually the link that brought me here seeking more help. I'm not too clear on how to remove GRUB from the MBR and reinstall in the boot sector of my linux partition. Its been suggested I just wipe the windows partition and reinstall. Then go back to the linux side and reinstall GRUB2 in the correct location. Thoughts?

---

