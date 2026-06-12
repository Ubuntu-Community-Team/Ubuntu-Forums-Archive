---
title: "Installed Linux Mint - Grub Gone - Can't boot"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by tonsil on 2010-05-18
I was pretty excited about the release of Linux Mint 9, so I got an ISO, and installed it next to my Ubuntu and Windows XP. Installation went fine, until I restarted my machine. When I boot, right after the memory count I see the following:

Verifying DMI Pool Data.......
Boot from Atapi CD-ROM
error: unknown filesystem.
grub rescue> (cursor blinks)

Whereas I'm still excited about Mint, I must get back to Ubuntu. How do I put things back? Please help!!

---

### Post by daimaru on 2010-05-18
start from live cd --> then resinstall grub from command line. this worked for me:
Reinstalling GRUB 2 from LiveCD
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: Grub2 - Reinstalling GRUB 2:

    * Boot LiveCD to the Desktop.
    * Open a terminal - Applications, Accessories, Terminal.
    * Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
    * If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
    * Mount your normal system partition:
      Code:

      sudo mount /dev/sdXY /mnt

          o Example: sudo mount /dev/sda1 /mnt
          o Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. Grub 2 works best when installed in the MBR of the drive to which BIOS boots. Also remember that you mount the partition (including the number) in this step, but you do not include the partition number when you run the "sudo grub-install" command later.
          o Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
    * Only if you have a separate boot partition:
          o
            Code:

            sudo mount /dev/sdXY /mnt/boot

            with sdXY being your /boot partition designation.
    * Reinstall GRUB 2:
      Code:

      sudo grub-install --root-directory=/mnt /dev/sdX

    *
          o Example: sudo grub-install --root-directory=/mnt /dev/sda
          o Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do not specify a partition number.


---------------
grub should recognize your other operating system. hope this works for you. good luck!

---

### Post by tonsil on 2010-05-18
It worked! Thank you so much!!! :)

---

