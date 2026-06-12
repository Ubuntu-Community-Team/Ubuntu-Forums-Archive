---
title: "ubuntu 10.10 boot but give error"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by hirensos on 2010-10-20
Dear Friends,

 I was windows user before 7 days i migrate to linux ubuntu  for that i allocate one more hdd for that and install lunux ubuntu 10.10 on it. it was worked great. today i found that .....it asking me.....GNU GRUB VERSION 1.98+201008045UBUNTU3 menu having four seleciton......1, ubuntu with linux 2.6.35-22-generic
                   2,ubuntu , with linux 2.6.35-22-generic...(recovery mode)
                   3,memory test (memtest86+)
                   4,memory test (memtest86+,serial console 115200)

  now if i select any of first two option it give me........like..
  .......mount:mounting /dev on /root/dev failed :no such file or directory
   ......mount:mounting/sys on /root/sys failed: no such file or dir
.........mount:mounting/proc on /root/proc failed:no such file or dir
..........target filesys doesnt have requested /sbin/init.
......no init found. tyr passing init = bootarg.

 busybox v1.15.3 build in shell (ash)
enter help for a list of comm
(initramfs)

...let me clear that i m new to linux...
...second thing is it possible to get data back or repair OS.

---

### Post by louieb on 2010-10-20
You get the **busy box **shell when the kernel is able to load but can't find / allocate other programs / files needed. That could be due to a hardware or a mis-configured setup file. - hard to tell.

You will need a live cd. It would be of great help if you get, run and put the output of   [Boot Info Script: SourceForge.net: ]("http://bootinfoscript.sourceforge.net/") in your next post.

---

