---
title: "GRUB error, can't boot live CD"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by fleurdesol on 2011-07-07
I tried to delete my ubunu partition to make more space on my harddrive for data in windows 7 as I wasn't using ubunu as much. After I deleted two partitions so I could turn the free space to unallocated space I extended the windows partition and everything worked fine. I shut down, and when I tried to reboot the next day I got a black screen that said error: no such partition grub rescue. I read some forums and tried booting with the ubuntu live CD. the first time I tried, I got a bunch of lines and the final one said panic occurred, switching back to text console. the second time I tried, I got only a few lines that said there was am input/output error can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I tried going through more forums and I'm sure this is just a stupid issue to fix but I am frustrated and don't know what else to try. If anyone can help me get my computer to boot the ubuntu live cd I would appreciate it. I have a few forums saved as what I should do next once I'm in ubuntu. as far as I know there is nothing else wrong with my computer except for the grub loader I stupidly messed up. thanks for any help!

also, if it helps, I am on a Dell Inspiron 1546 (not by choice).

---

### Post by seawolf167 on 2011-07-07
I'm assuming you only had one Ubuntu install, so when you deleted the partitions, GRUB in your MBR doesn't know what to do now. The solution is to insert your Windows 7 cd, boot off it, then select to enter the recovery console. Once there (a MS-DOS style prompt), type in the following commands

```
BootRec.exe /fixmbr
BootRec.exe /fixboot
```the *fixboot* line is most likely not needed, see if it works without it first, if you still cant boot, reboot into the cd and type the 2nd command (the fixboot one)

---

### Post by fleurdesol on 2011-07-07
my computer was recently replaced with a refurbished model that just came with windows 7 on it. I never got a CD. I'm going to my school's help desk to see if they have one I can use to see if my computer will boot. I'm thinking it might also be my cdrom so hopefully they'll have an external I can try. this is so exhausting. thanks for the help!

and I LOVE seawolf by the way, assuming your user name is referring to the band.

---

### Post by seawolf167 on 2011-07-07
I'm sure the help desk will have one - its a pretty easy fix. As for your cd/dvd drive, it could have simply been a corrupted live cd that was trying to boot (did you MD5SUM it?).

As for the name - I didn't even know there was a band called "Seawolf"! Lol

---

