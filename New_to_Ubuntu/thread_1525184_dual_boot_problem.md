---
title: "dual boot problem"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by rohit247 on 2010-07-06
i have installed windows xp and ubuntu
after partitioning my windows partition using partition manager
i am getting error:unknown filesystem boot rescue> error

please help 

here is the output of  boot_info_script*.sh


edit:the problem was solved by reinstalling grub2

---

### Post by mikewhatever on 2010-07-06
The problem is that after creating more partitions the numberring of your existing extended partitions had changed. That in turn, resulted in grub not finding the partition to boot from (it's looking for /dev/sda5, but Ubuntu is now on /dev/sda7). Reinstalling grub while running from USB should fix it.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
As said, the partition to use in place of /dev/sdXY would be /dev/sda7 in your case.

---

### Post by rohit247 on 2010-07-06
thanks mikewhatever

---

