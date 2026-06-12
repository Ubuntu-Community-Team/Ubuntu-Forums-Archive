---
title: "Grub2 + Second hd problems"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by cdom on 2011-02-16
After a couple of installs I managed to have 10.10 running pretty much to my satisfaction, until one of the auto updates. I've tried a number of fixes but the problem only got worse.
   As clear and short as I can.
Installed Ubuntu on Sata hard drive. 2nd Pata drive was just there with photos.Showed up as external, but no big deal. Everything working OK.
   Was updating Alsa driver and for for whatever reason Ubuntu updated to v.11.04.(don't understand this).
   The weird part was that it somehow installed the boot to the 2nd Pata drive.
   Tried too may Grub fixes..apparently over my head.
   Disconnected Pata drive, reinstalled along side the corrupted version to see If I could fix it. Zero.
   The problem is is that now the OS   wants to boot off the 2nd hard drive,even though there is nothing there. Stuck at cursor. I disconnect and it boots fine. 
   I've scoured the forums and google and cannot find anything close to fixing this problem.  The bios boot order is set correctly.
   Thanks for any help .

---

### Post by cariboo on 2011-02-16
You need to install grub on the first hard drive in the system. Boot from the Live Cd and once at the desktop open a terminal and enter the following commands:

[LIST=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

dev/sdXx = the partition you have ubuntu installed on. Once you are at the root prompt, type the following command:

```
sudo grub-install /dev/sda
```

the above command will install grub to the mbr of the first hard drive. Once the above command is completed type:

```
update-grub
```

you should see a listing of the different operating systems you have on your system. Once that command is completed, press Ctrl-d twice, and reboot.

---

### Post by cdom on 2011-02-19
Sorry for the late reply. Was rudely interuppted from some some that had to to be done.....After a number of tries I am now booting off the first Sata drive. Thank you......

---

