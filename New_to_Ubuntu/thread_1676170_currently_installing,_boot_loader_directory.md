---
title: "currently installing, boot loader directory"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by mspoden on 2011-01-26
Hey guys,

So i am intalling for about the 8th time this week. After several screw ups with mint and ubuntu studio, i am putting on ubuntu 10.10. I went to manual setup the partitions because i have two separate hard drives that i am using. 

It is asking me where to put the bootloader and I really don't want to screw this up so I was hoping you guys could tell me:

/dev/sbd ATA WDC...
/dev/sda1 Windows 7 (loader) [Windows 7  OS]
/dev/sda5 [Windows 7 Data]
/dev/sda6 [Windows 7 Apps]
/dev/sdb ATA ST.....
/dev/sdb1 [Ubuntu /root]
/dev/sdb6 [Ubuntu /home]

I am guessing it is either sda1 or sdb1 but i was hoping i could get some advice on it.

Thanks.

---

### Post by mikewhatever on 2011-01-26
Definitely not sda1 cause that's the W7 boot partition according to your list. sdb1 is a viable option, but not ideal, since you can't boot from a partition. The MBR of the second hdd, sdb, is probably the safest choice. The W7 installation will stay untouched, and Ubuntu will load if you boot from the second hdd.

---

