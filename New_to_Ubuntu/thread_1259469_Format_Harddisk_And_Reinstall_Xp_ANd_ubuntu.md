---
title: "Format Harddisk And Reinstall Xp ANd ubuntu"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Abhay Kant on 2009-09-06
Starting from the Beginning,
I have Laptop and installed Xp But 1 day i see Ubuntu and Find good so i installed it but i have not uninstall Xp i created Partion and installed ubuntu ,
But now due to virus Xp have stoped Working i want to format my Hard disk and Reinstall Xp and don't want to disturb My Ubuntu Partion Due to GRUB the Xp cd is not detected in bios.

---

### Post by mlentink on 2009-09-06
You don't format harddisks, but partitions. In this case you would want to format your XP-partition, which you can even do from within Ubuntu. 
Make sure you have unmounted the XP partition and go to System>Administration>Partition Editor
Select the XP partition and format it as NTFS..

Alternatively, to make your laptop start up with your XP-boot disk: at boot time press the button to switch boot-devices (on my HP it's F9) and select the cd-drive. Boot up as usual and let XP do its work.

You may have to reinstall GRUB afterwards. about which there's about 100.000 posts on this forum...

---

### Post by presence1960 on 2009-09-06
after you reinstall windows you will need to restore GRUB to MBR of your hard disk. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In # 6 use setup (hd0) if you only have 1 hard disk.
```

---

