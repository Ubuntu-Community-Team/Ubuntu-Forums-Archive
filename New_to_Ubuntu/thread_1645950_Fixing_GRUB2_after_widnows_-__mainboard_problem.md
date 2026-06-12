---
title: "Fixing GRUB2 after widnows -  mainboard problem"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Medivh90 on 2010-12-15
Hi, 
i followed the tuturials on forums, they are great, but i have some big problems, they are maybe here beacose my mainboard is to old(my friend saying) maybe not, i for sure wanna ask professionals.
 
I'm on ubuntu for a some time, and with 10.04 i have installed GRUB 2. Few weaks ago i was updated system to 10.10. Now i must install Windows just to finish some work (with c# XNA), so i have installed windows XP SP3. 
 
I followed instructions for dual booting and re installing
(With 10.04 install disk)
First thing when i type 'sudo grub' result is 'grub command not found' so i used google and saw that i must re-install it, i followed next instructions:
 
sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdc
 
and reboot, after reboot notnig happens i should run update grub - command not found, i tried lots of things always the same file not found or command not found. i do not have file menu.lst.
(After trying to reinstall, i cannot boot win XP too, so i must fix with fixboot and fixmbr)
(The terminal output says instalacion successful..)
My friend saying that my mainboard is too old and it does not support booting from hd space that is larger than 7.5 GB (The board is MSI KT4A-V AMD).
 
So is this true reason or it is something else, what should i do, win XP is not important to me, just to restore ubuntu somehow. 
 
Thanks in advance.

---

### Post by Medivh90 on 2010-12-15
Hi, 
i followed the tuturials on forums, they are great, but i have some big problems, they are maybe here beacose my mainboard is to old(my friend saying) maybe not, i for sure wanna ask professionals.

I'm on ubuntu for a some time, and with 10.04 i have installed GRUB 2. Few weaks ago i was updated system to 10.10. Now i must install Windows just to finish some work (with c# XNA), so i have installed windows XP SP3. 

I followed instructions for dual booting and re installing
(With 10.04 install disk)
First thing when i type 'sudo grub' result is 'grub command not found' so i used google and saw that i must re-install it, i followed next instructions:

sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdc

and reboot, after reboot notnig happens i should run update grub - command not found, i tried lots of things always the same file not found or command not found. i do not have file menu.lst.
(After trying to reinstall, i cannot boot win XP too, so i must fix with fixboot and fixmbr)
(The terminal output says instalacion successful..)

My friend saying that my mainboard is too old and it does not support booting from hd space that is larger than 7.5 GB (The board is MSI KT4A-V AMD).

So is this true reason or it is something else, what should i do, win XP is not important to me, just to restore ubuntu somehow?

Thanks in advance.

---

### Post by kansasnoob on 2010-12-15
Please use a Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by ajgreeny on 2010-12-15
When you carried out the commands you show
```
sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdc
```
is that exactly what you typed?  If so nothing would be expected to work.

The /dev/sdXY should have been the partition of your ubuntu install, eg /dev/sda2 or wherever ubuntu is installed, and the /dev/sdc at the end should be the root of the disk to which you boot, which if you have only one disk is /dev/sda.

If you were aware of this already, and did use the appropriate dev names, my apologies, but people have used such incorrect commands in the past and wondered why they don't work.

---

### Post by Medivh90 on 2010-12-15
Thx for fast help. 
Here is results.txt

---

### Post by Medivh90 on 2010-12-15
i was aware of that already, i was typing sda4 the partition with ubuntu, and results is Installation successfully, after reboot nothing happens.

---

### Post by kansasnoob on 2010-12-15
Please copy-n-paste the following commands using the Live CD:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

If that returns any errors also run:

```
grub-install --recheck /dev/sda
```

Then run:

```
update-grub
```

Wait for it to say "done" and then run:

```
exit
```

And:

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot and hopefully you'll be in business.

---

### Post by Medivh90 on 2010-12-15
I am back on ubuntu now, thank you for fast and excellent help, thank you very much.

---

### Post by kansasnoob on 2010-12-15
It's good to know I did at least one thing right today ;)

---

