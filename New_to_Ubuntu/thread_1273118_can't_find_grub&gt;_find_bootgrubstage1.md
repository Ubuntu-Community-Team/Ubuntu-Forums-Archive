---
title: "can't find grub&gt; find /boot/grub/stage1"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by navrajyadav on 2009-09-23
Dear Friends,
                    I am beginner of ubuntu. I never Use Linux(Ubuntu) before. But recently i install ubuntu 9.04 on my laptop, i already have windows xp pro on my c-drive everything is fine. both are working fine, but when i repair my xp due to some problem i cant able to boot ubuntu.

my important data is in the desktop of ubuntu, i really want that data. i tries some steps like
grub> find /boot/grub/stage1  
but it says can't find....

i am not familiar  with ubuntu i am windows user. how i get my data back fom the ubuntu desktop. 
i tried unetbootin-super grub disk rev120.exe program but can't find the file.

i only want my data from the desktop of ubuntu.

Thanks,

---

### Post by laffinet on 2009-09-23
If you only want to to get the data from the Ubuntu desktop you can use the liveCD.

Assuming that you have a normal Ubuntu Installation CD (for example downloaded from the internet), boot from that CD and select "Try Ubuntu without modifications to your computer".

This will take you to the liveCD envrionment, which should mount all your drives.

Open the main menu, go to places, navigate to /home/yourubuntuusername/Desktop/

You should see your files there. Copy them wherever is convenient (USB stick, windows drive). Done.

Different story if you want to fix your Ubuntu installation.

---

### Post by arrange on 2009-09-23
And when you're there, check also the contents of your */boot/grub* folder. *Stage 1* file is not that important, but you must have a *stage2* file there.

---

### Post by ranch hand on 2009-09-23
You ca nget to all your data, on all partitions from your LiveCD.

I assume you are using the LiveCD for your terminal work in grub.  I am also assuming that you are using "sudo grub" to start your grub session.

I would, as said by "arrange", check your /boot/grub file from your Live CD.  Stage 1 should be in there.

One way to check it is to;
```

jak@jak-desktop:~$ ls /boot/grub
default        installed-version  menu.lst.backup    stage1
device.map     jfs_stage1_5       minix_stage1_5     stage2
e2fs_stage1_5  menu.lst           reiserfs_stage1_5  xfs_stage1_5
fat_stage1_5   menu.lst~          splashimages

```

---

### Post by LewRockwell on 2009-09-24
> **navrajyadav said:**
> recently i install ubuntu 9.04 on my laptop, i already have windows xp pro on my c-drive everything is fine. both are working fine, but when i repair my xp due to some problem i cant able to boot ubuntu.

sounds like windows altered your Master Boot Record

use the LiveCD to fix your MBR and grub

here is one previous thread:

[http://ubuntuforums.org/showthread.php?t=1272323](http://ubuntuforums.org/showthread.php?t=1272323)

.

---

### Post by Darkwing-Duck on 2009-09-24
Here is a good guide to help you fix your MBR.
 
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)
 
Hope this helps you!

---

### Post by navrajyadav on 2009-09-24
thank you guys, for your quick reply and help.

i fix my grub using the live cd. first i try only save my data to other drive but it say access is denied. (read only) something  like that.

finally i get my data back.

 thanks again :)

---

