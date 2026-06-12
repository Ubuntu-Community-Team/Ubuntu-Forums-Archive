---
title: "format hard drive and scan for errors how is it done?"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by stinger30au on 2009-10-01
when ubuntu formats a hard drive does it check for errors and mark parts of the hdd as unuseable or not if not how is it done?

thanks

---

### Post by aesis05401 on 2009-10-01
There is a utility called 'badblocks' that is a part of the e2fsprogs package.  It should take care of you.  I don't know when Ubuntu may call this util, but you can run it whenever you want.

Edit: Huh - I read through the man material again and it indicates that 'e2fsck -c' should be used to invoke badblocks instead of doing it stand-alone.  Hope this helps.

---

### Post by juancarlospaco on 2009-10-02
[To format disk click here.]("apt:/gparted")

to force check of EXT4 partitions run:
**sudo touch /forcefsck && sudo reboot**

Ubuntu checks the partition when finished.

---

### Post by stinger30au on 2009-10-02
cool,
thanks for the replies

---

