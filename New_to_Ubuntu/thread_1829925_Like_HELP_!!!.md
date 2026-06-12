---
title: "Like HELP !!!"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by blade4 on 2011-08-21
Okay , so here's the thing : My filesystem refuses to mount . And I'm pretty sure of the cause too - a short while ago I had the brilliant idea of adding data=writeback to my fstab file without considering the repercussions of it clashing with the other tweaks already in there . The end result : my system won't boot . I tried to remount the disk as rw 

mount -n -o remount,rw / 

but that doesn't work either 

Here's a paste out of my fstab : 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    discard,data=writeback,loop,errors=remount-ro,noatime,nodiratime 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0


I'm using Ubuntu 10.04 LTS . Please help me out on this guys .....

---

### Post by Wim Sturkenboom on 2011-08-21
Use a liveCD or liveUSB, mount your internal HD and fix the fstab on the internal HD

PS A title like 'I scr.w.d up my fstab' is more useful ;)

---

### Post by blade4 on 2011-08-21
Thanks for the tip Wim , this was actually my first thought too .  Only problem is that I have actually installed ubuntu on winxp as a software , not as a separate OS . So even the live USB doesn't show the root partition . Any help here ?

---

### Post by Wim Sturkenboom on 2011-08-21
I found [How can I access my Wubi install and repair my install if it won't boot?](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F) by googling for 'wubi fix fstab'

Hope it helps

---

### Post by blade4 on 2011-08-21
Thanks for the tip Wim , this was actually my first thought too .  Only problem is that I have actually installed ubuntu on winxp as a software , not as a separate OS . So even the live USB doesn't show the root partition . Any help here ?

---

### Post by mikewhatever on 2011-08-21
'Like HELP !!!'?
What's wrong with descriptive titles?:icon_frown:

---

### Post by Wim Sturkenboom on 2011-08-21
> **mikewhatever said:**
> 'Like HELP !!!'?
What's wrong with descriptive titles?:icon_frown:Maybe you should read the replies ;) Was already mentioned :guitar:

---

### Post by blade4 on 2011-08-21
Hey Wim , thanks for all the help ... unfortunately your link didn't solve my problem . Oh well , time for a fresh installation I guess...maybe this time I'll give Natty a try .  Cheers :)

---

