---
title: "Switching from Linux Mint to Ubuntu"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by eb7star on 2010-12-16
I'm a computer illiterate, but curious person who decided that it'd be cool to partition her hard drive and install linux mint. It worked, and it was fine, but now I want to change that partition from Mint to Ubuntu, and I have no idea how to go about that. Any suggestions?

---

### Post by matt_symes on 2010-12-16
Hi

Just install Ubuntu over the top. On the partition page of the Ubuntu installer, select the manual partition option and select the partition to install it in. Also, select the option to format the partition. I prefer ext4 but you can select what you want.

Remember to set the mount point on the partition and you are good to go

BTW: backup first

Kind regards

---

### Post by sandyd on 2010-12-16
The easiest way is to format the partition using Gparted. You can find gparted if you boot up the Ubuntu Livecd, and go to System ->Administration.

Format it to ext4.

Start the Ubuntu installer.
When it gets to the partitioning section, choose "custom" or "manual" (i don't remember the wording, but its something like that).

Select the partition you just formated, and set that as root ("/") (without the brackets and the quotes).

Everything else should come along nicely.

---

### Post by eb7star on 2010-12-16
oh, cool, easier than I thought, thanks!

---

### Post by KL_72_TR on 2010-12-16
No you're not “Illiterate”, it is not a good definition. I think you must try to install Ubuntu form the scratch on that partition, if you have a copy of Ubuntu.

---

### Post by jackfruit123 on 2010-12-16
> **matt_symes said:**
> Hi

Just install Ubuntu over the top. On the partition page of the Ubuntu installer, select the manual partition option and select the partition to install it in. Also, select the option to format the partition. I prefer ext4 but you can select what you want.

Remember to set the mount point on the partition and you are good to go

BTW: backup first

Kind regards
i agree with you, the easiest way to install is just put your new ubuntu installation over your mint partition..

---

