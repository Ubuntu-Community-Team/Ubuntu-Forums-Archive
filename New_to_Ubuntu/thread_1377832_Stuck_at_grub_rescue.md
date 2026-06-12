---
title: "Stuck at grub rescue"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Zindiq on 2010-01-10
I am working on a Acer laptop Extensa4420, with Ubuntu installed on a partition. When this was installed, the Win platform went haywire, finally managed to get in and delete the Ubuntu partition and Win returned to normal - but now I cannot boot to either.

When I start the system, it says:

GRUB Loading.
error: no such partition
grub rescue>


I have been through the various forums and most of the commands suggested the computer does not recognize.

It does recognize insmod, but no boot path I've tried produces and result


Any suggestions on how to get this infernal grub off my laptop so it will be usable again?

---

### Post by ubudog on 2010-01-10
Boot off a live cd or flash drive and open a terminal and type ```
sudo gparted
```  Post what it says.

---

### Post by tom.swartz07 on 2010-01-10
> **Zindiq said:**
> I am working on a Acer laptop Extensa4420, with Ubuntu installed on a partition. When this was installed, the Win platform went haywire, finally managed to get in and delete the Ubuntu partition and Win returned to normal - but now I cannot boot to either.

When I start the system, it says:

GRUB Loading.
error: no such partition
grub rescue>


I have been through the various forums and most of the commands suggested the computer does not recognize.

It does recognize insmod, but no boot path I've tried produces and result


Any suggestions on how to get this infernal grub off my laptop so it will be usable again?

Just to clarify, you no longer have Ubuntu on your system?
Either way, youll have to update your MBR to reflect the changes you made when you deleted the partitions. 

If you use XP, Heres a guide: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you dont mind using GRUB as your bootloader, just put a LiveCD in, boot to the live desktop and follow the instructions here:[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

Just replace SDA# with your Windows Partition.

---

### Post by Zindiq on 2010-01-10
That is correct - the partition with ubuntu has been deleted.

The command sudo is not recognized, as are most of the other commands I have seen listed.

My win install is sda2 i believe.



The other difficulty I have is that my PC did not come with a OEm instal disk, but rather had the recovery copy in a separate partition on my HD - making using it to boot a difficult proposition...

---

### Post by garvinrick4 on 2010-01-10
Has quite a few fix's for booting including Windows.


[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ubudog on 2010-01-11
[QUOTE=]The command sudo is not recognized, as are most of the other commands I have seen listed.[/QUOTE]

Did you boot off the live cd or type that in the grub rescue console?

---

### Post by wavesound on 2010-05-09
HI All
I am sat at the grub resue prompt I have tried to ls all the shown drives with / and /boot
But all I get is unknown file system.
This was an upgrade I did.

Cannot grub rescue not have a command to find the files it needs I assume there on one of the two disks, grub-config returns unknown command


Cheers
Bob

---

### Post by Kir_B on 2010-05-09
> **wavesound said:**
> HI All
I am sat at the grub resue prompt I have tried to ls all the shown drives with / and /boot
But all I get is unknown file system.
This was an upgrade I did.

Cannot grub rescue not have a command to find the files it needs I assume there on one of the two disks, grub-config returns unknown command


Cheers
Bob

Hey Bob.

I don't know for sure that it will help, but it sure worked for me and plenty of others.

If you have a live cd handy, click on this link; [COLOR=#cc33cc]***[COLOR=#66ffff][When  grub2 won't boot, click here for assistance]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]***[/COLOR], and follow the instructions given to me from "lmarmisa".

Good luck and let us know if it helped, or not.

---

### Post by jjrivet2009 on 2011-05-01
I am trying to fix an ACER Travelmate 5510
It originally had a virus and i got past that with the help of loading ubuntu.
 
However, when running the XP Recovery from the hidden partition, I accidentally deleted the partition that had ubuntu on it.
Now when the PC is booting it get the message "no such partition Grub Rescue >"
 
So i cant load anything now !
please help - i dont have any xp installation disks as they are on the hidden partition

---

### Post by pritam_par on 2011-08-10
This is quite long but worked for me

1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
2. Open a terminal - Applications, Accessories, Terminal.
3. Determine your normal system partition - (the switch is a lowercase "L")

      sudo fdisk -l
          * If you aren't sure, run

            df -Th. Look for the correct disk size and ext3 or ext4 format. 
4. Mount your normal system partition:
          * Substitute the correct partition: sda1, sdb5, etc. 

   sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
5. Only if you have a separate boot partition:
          * sdYY is the /boot partition designation (for example sdb3)
          *sudo mount /dev/sdYY /mnt/boot 
6. Mount the critical virtual filesystems:

      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys
7. To ensure that only the grub utilities from the LiveCD get executed, mount /usr

      sudo mount --bind /usr/ /mnt/usr
8. Chroot into your normal system device:

      sudo chroot /mnt
9. If there is no /boot/grub/grub.cfg or it's not correct, create one using

      update-grub
10. Reinstall GRUB 2:
          *Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 

      grub-install /dev/sdX
11.Verify the install (use the correct device, for example sda. Do not  specify a partition): sudo grub-install --recheck /dev/sdX

--------------------------------------------------------------------------
[My blog on open source]("http://opensource-sidh.blogspot.com/")

---

### Post by YesWeCan on 2011-08-10
> **jjrivet2009 said:**
> I am trying to fix an ACER Travelmate 5510
It originally had a virus and i got past that with the help of loading ubuntu.
 
However, when running the XP Recovery from the hidden partition, I accidentally deleted the partition that had ubuntu on it.
Now when the PC is booting it get the message "no such partition Grub Rescue >"
 
So i cant load anything now !
please help - i dont have any xp installation disks as they are on the hidden partition
You'll need to restore the standard MBR boot code so you can boot whatever OS you still have - you still have XP I assume?
boot live CD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

(assuming your disk is named sda)

---

### Post by Andrew_nuts on 2012-02-19
> **pritam_par said:**
> This is quite long but worked for me

1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
2. Open a terminal - Applications, Accessories, Terminal.
3. Determine your normal system partition - (the switch is a lowercase "L")

      sudo fdisk -l
          * If you aren't sure, run

            df -Th. Look for the correct disk size and ext3 or ext4 format. 
4. Mount your normal system partition:
          * Substitute the correct partition: sda1, sdb5, etc. 

   sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
5. Only if you have a separate boot partition:
          * sdYY is the /boot partition designation (for example sdb3)
          *sudo mount /dev/sdYY /mnt/boot 
6. Mount the critical virtual filesystems:

      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys
7. To ensure that only the grub utilities from the LiveCD get executed, mount /usr

      sudo mount --bind /usr/ /mnt/usr
8. Chroot into your normal system device:

      sudo chroot /mnt
9. If there is no /boot/grub/grub.cfg or it's not correct, create one using

      update-grub
10. Reinstall GRUB 2:
          *Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 

      grub-install /dev/sdX
11.Verify the install (use the correct device, for example sda. Do not  specify a partition): sudo grub-install --recheck /dev/sdX

--------------------------------------------------------------------------
[My blog on open source]("http://opensource-sidh.blogspot.com/")
 
This methods works great but it has little description. Installation with description on [grub rescue]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html"). This will be helpful with description. Also [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099). If previous method do not work

---

