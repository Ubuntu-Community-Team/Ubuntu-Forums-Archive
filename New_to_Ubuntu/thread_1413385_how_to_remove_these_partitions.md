---
title: "how to remove these partitions"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by DarkestStar on 2010-02-22
Hello forum
had installed 9.10 netbook edition on samsung NC10 son formatted HDD then had problem where GRUB couldnt load. Installed 9.10 desktop via USB mem stick which worked very well. The thing now is the GRUB menu, there seem to be several partitions with Ubuntu on:
[ATTACH]147901[/ATTACH]

Have downloaded and ran gparted and have this:
[ATTACH]147902[/ATTACH]

Is it possible to tidy this HDD up?
Is this done with gparted?
Is there a how to?

thanks

---

### Post by stoogiebuncho on 2010-02-22
Yes, it looks like you have Ubuntu installed twice, and yes, you can clean things up with gparted.  Do you know which Ubuntu you want to keep? (sda7 or sda5?)

---

### Post by DarkestStar on 2010-02-22
Looks like it is 7

---

### Post by stoogiebuncho on 2010-02-22
Then you should be able to just delete sda5 and sda6 and then expand sda7 to take up the extra space (You will have to boot from the USB you used to install Ubuntu in order to do this).  I believe if you right-click on the partition it will give you options to delete or whatever else you may want to do.

As always, backup all your personal data first.  There's always a chance of something going wrong.

After you have made these changes, you will probably need to boot into Ubuntu again, open a terminal, and enter ```
sudo update-grub
``` to remove the extra Ubuntu menu items from Grub.

---

### Post by DarkestStar on 2010-02-22
Thanks for the replies, just need to get the live ubuntu back on the mem stick as son formatted it for college this morning :( but its easy enough to do. Should have put the ISO on mine.

---

