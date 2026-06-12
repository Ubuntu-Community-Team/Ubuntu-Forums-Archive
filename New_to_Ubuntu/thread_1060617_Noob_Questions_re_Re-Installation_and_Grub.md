---
title: "Noob Questions re Re-Installation and Grub"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by cyan on 2009-02-04
I have installed two different flavors of Ubuntu (along with Windows) and have everything showing up nicely in grub when I first boot up.

For various reasons, I want to get rid of one flavor of Ubuntu and re-install the second flavor.

For the flavor I want to get rid of, do I just reformat that partion?  Will it disappear in grub or do I have to edit that manually?

And for the flavor I want to re-install, do I just run the install CD again?  Will grub adjust accordingly?

I just don't want to finish everything and find that I can't boot into anything because grub is frakked.

Thanks to anyone that can help a brother out!

---

### Post by cjv8888 on 2009-02-04
Just reformat the partition and reinstall the other one.  I think grub will renew itself to what is existing on the system.

---

### Post by cyan on 2009-02-04
Thanks, cjv, that's what I needed to know.

---

### Post by DariusS on 2009-02-04
> **cyan said:**
> I have installed two different flavors of Ubuntu (along with Windows) and have everything showing up nicely in grub when I first boot up.

For various reasons, I want to get rid of one flavor of Ubuntu and re-install the second flavor.

For the flavor I want to get rid of, do I just reformat that partion?  Will it disappear in grub or do I have to edit that manually?

And for the flavor I want to re-install, do I just run the install CD again?  Will grub adjust accordingly?

I just don't want to finish everything and find that I can't boot into anything because grub is frakked.

Thanks to anyone that can help a brother out!

If I understand things right, installing any flavor of Ubuntu will re-install grub, thusly re-scanning all the partitions for operating systems. Therefore, no need to concern yourself about manual edits. Like the guy above me said, just format and reinstall (with caution, always with caution).

---

### Post by hRob on 2009-02-05
from ur post i understand that u want to get rid of one version of ubuntu and install another version.. this is as good as installing a new version of ubuntu.. just format the two partitions and install the new one.. while isntalling the new version grub will automatically be configured.. you dont have to worry about that.. but if u do want to edit the grub u can as well do it.. nota problem at all.. its just a piece of cake editing the grub menu.. but by all means tread carefully!

---

### Post by travmon69 on 2009-02-05
For noobs with grub errors who don't want to mess with grub try:


  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)   

 ver  0.9770  worked for me on both jaunty and intrepid.

---

