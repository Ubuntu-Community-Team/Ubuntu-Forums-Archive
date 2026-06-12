---
title: "Messed up External harddrive with gparted! HELP!"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by kramer65 on 2008-12-08
Hello,

I needed more space on one of the partitions on my external harddrive. I used Gparted to resize one partition and move and enlarge another one.

After this I wanted to browse around one of the partitions but the rights seemed to be weird. So I did a "chmod -R 777 media/MULTIMEDIA" (one of the partitions). This worked for quite a while after which it somehow stopped in the middle of it.

I restarted twice but the whole external harddrive doesn't seem to mount anymore! None of the partitions works anymore! There is really important stuff on there and unfortunately I didn't do a backup (stupid stupid I know!)!

Can anybody help me to get out of this crisis??

---

### Post by malathion on 2008-12-08
If your data was accessible after the resize, then this most likely is not an error with gparted. You may be looking at a disk that is physically failing. Disconnect the disk right away until you are able to run a Disk Fitness Test on it (available on Hiren's BootCd and in other places, google around for it). If the DFT passes, then you are looking at a good disk with data corruption and you will need a data recovery tool. If DFT fails, then you must immediately disconnect it again and get it to a data recovery professional.

---

### Post by kramer65 on 2008-12-08
Thanks malathion. You seem to know what you're talking about. I just disconnected the whole thing, but it did run for at least an hour or so..

So I need to do a Disk Fitness Test? How do I do that? Got any tips on that?

[edit]
Alright, I am downloading the Hirens BOOTCD now. It will take another hour or so. Do you have any idea to how to use the DFT? I guess I need commands for it or so? I can't really find anything about it..

---

