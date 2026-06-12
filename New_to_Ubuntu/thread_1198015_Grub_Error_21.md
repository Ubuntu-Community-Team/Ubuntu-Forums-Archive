---
title: "Grub Error 21"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by life_in_oh on 2009-06-26
Hi,
I have never really tried Ubuntu before but decided to try to install it as a dual boot system after I read about it.  I have a Compaq with an AMD 64 processor.  My computer is running XP.  I installed Ubuntu 9.04 following the instructions.  I restarted my computer and it seem to work.  After turning it off and restarting it again, I get a Grub Error 21 code. I can't get to either OP sysems.  The only way to get acces is to boot from the Ubuntu Boot disk I downloaded and used to install Ubuntu.

How do I fix this problem?

I am a real newbie to Ubuntu (4 hrs) who doesn't understand the Ubuntu jargon.

---

### Post by Locutus_of_Borg on 2009-06-26
boot from the livecd
click on Applications
then click on Accessories and open Terminal
Inside terminal enter the following text: sudo su
the prompt should change to say root@ubuntu
now enter the following: fdisk -l
(note that that is a lowercase L)

copy and paste the output from that last command here, and i will help you get everything working properly

---

### Post by life_in_oh on 2009-06-26
Hi,
here it is
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisl-l
bash: fdisl-l: command not found
root@ubuntu:/home/ubuntu# fdisk-l
bash: fdisk-l: command not found
root@ubuntu:/home/ubuntu# fdisl -l
bash: fdisl: command not found
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00160015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9446    75874963+   c  W95 FAT32 (LBA)
/dev/sda2   *        9447       17550    65095380    7  HPFS/NTFS
/dev/sda3           17551       19457    15317977+   f  W95 Ext'd (LBA)
/dev/sda5           17551       19457    15317946    7  HPFS/NTFS
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu#

---

### Post by Locutus_of_Borg on 2009-06-26
Okay, somehow you seem to have managed to erase and format your Ubuntu installation.

You can try to re-install it again, or you can boot from your Windows XP installation disk, and navigate to the Recovery Console (just follow the on-screen prompts to get there), and re-install your Windows boot loader by entering into the Recovery Console: fixmbr

then reboot without the disk inserted and you will boot back into XP.


I recommend you re-install Ubuntu

---

### Post by life_in_oh on 2009-06-26
Thanks,

I will let you know how it goes.

Kind Regards

---

### Post by life_in_oh on 2009-06-26
Hi,

I reloaded Ubuntu.  I can get into Ubuntu, but can't get into XP.  The XP window logo opens, but reboots and goes back to the Grub.  Here is what I have now.

Kind Regards

root@tony-desktop:/home/tony# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00160015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9446    75874963+   c  W95 FAT32 (LBA)
/dev/sda2   *        9447       17224    62476785    7  HPFS/NTFS
/dev/sda3           17225       19457    17936572+   f  W95 Ext'd (LBA)
/dev/sda5           17551       19457    15317946    7  HPFS/NTFS
/dev/sda6           17225       17528     2441817   83  Linux
/dev/sda7           17529       17550      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@tony-desktop:/home/tony#

---

### Post by Locutus_of_Borg on 2009-06-27
please post the contents of /boot/grub/menu.lst

---

