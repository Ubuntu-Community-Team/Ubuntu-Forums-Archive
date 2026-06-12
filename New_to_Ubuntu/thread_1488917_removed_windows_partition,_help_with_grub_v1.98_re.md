---
title: "removed windows partition, help with grub v1.98 required"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by razaz03 on 2010-05-20
Hi all,

So I move to uninstall my windows partition for my netbook earlier due to my new-found appreciation for ubuntu, with a couple of problems:

Using a 9.10 liveCD, I deleted the contents of the windows partition, and copied the contents of my ubuntu one to it, such that:

sda1 - former NTFS windows partition
sda2 - extension
    sda5 - ext3 linux partition

So sda1 contents reformatted, sda5 contents copied to sda1, then sda2 deleted. sda1 expanded to encompass entire disk, and root is happy.

I got the error 22 message with Grub, so I assumed I needed to reinstall it. At this point I believe I did it via the terminal but incorrectly. Upon reboot now it sends me to a blank GRUB screen (version 1.98-1ubuntu5) with no apparent means of progressing. 

I figure perhaps GRUB doesn't recognize my kernal? Reboot via the liveCD, find [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 
which graciously directs me to the laymans
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I receive the error 'attempting to install grub to a partition instead of the mbr', which I hear is all the craze with the slicker GRUB. I --force it as instructed, and am given the all-clear in the terminal. Rebooting now and it is still stuck on black GRUB screen at startup- I can not even boot into my liveCD anymore (for reasons unbeknown to me). I figure maybe I have GRUB incorrectly configured, but have no idea how to progress from here.

Any help would be greatly appreciated.

Regards,

razaz03

---

### Post by Elfy on 2010-05-20
Can you boot the livecd - open nautilus from Places - mount the ubuntu partition - then go to /boot/grub

Have you got menu.lst or menu.cfg?

Possibly need to unmount the disk - right click on the desktop and unmount.

If menu.cfg - reinstall grub [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If menu.lst - reinstall grub - [https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)

---

### Post by razaz03 on 2010-05-20
I can not boot from the livecd, it takes me straight to the blank GRUB screen. I used to be able to press f4 with my bios (recovery) which would subsequently load the contents of my liveCD but this doesn't seem to work now, any quick-fixes there?

I'm not sure but as I skimmed over the grub/grub2 differences (seeing as how 9.10 employs grub2) I reckon it's menu.cfg. Before I can attempt a re-reinstall, how can I load the liveCD?

Thanks,

razaz03

---

### Post by -kg- on 2010-05-20
The inability to boot to the Live CD won't be a GRUB issue, no matter *what* version of GRUB you're using.  Somehow, the setting to boot to the CDROM drive has been changed in BIOS, unless your CD drive itself has failed.

First, pull up BIOS and make sure that your CD drive is before the hard drive in the boot sequence.  Then, if and when that is correct, next I would check and make sure the connection (and since this is a netbook, I assume that you're using an external disk drive) to the cd drive is good and, if you have another computer to use, hook the cd drive up to the other computer and make sure the cd drive itself is working properly.

Failing the ability to get the CD drive working, another way you might be able to get in and fix your problem is to create a bootable USB drive and boot to that.

Oh, and whatever the craze, you *still* need the requisite portion of GRUB in your MBR area in order to access it for booting up.  I'm not sure what those instructions are about, but the only reason I install GRUB in the partition instead of the MBR is when I'm installing multiple OSes and want a certain OSes  GRUB to control things.  That OSes GRUB goes in the MBR and the rest go in their seperate partition.

---

### Post by -kg- on 2010-05-20
> I receive the error 'attempting to install grub to a partition instead of the mbr', which I hear is all the craze with the slicker GRUB. I --force it as instructed

Where in that link did you read that instruction?  The only thing I could find (in the OP) was:

> **Reinstalling GRUB 2 from LiveCD**

If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: Grub2 - Reinstalling GRUB 2:

    * Boot the Karmic or Lucid LiveCD (Try without installing).
    * From the Desktop, open a terminal - Applications, Accessories, Terminal.
    * Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
    * If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
    * Mount your normal system partition:
      Code:

      sudo mount /dev/sdXY /mnt

          o Example: sudo mount /dev/sda1 /mnt
          o Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. [COLOR="Red"]Grub 2 works best when installed in the MBR of the drive to which BIOS boots.[/COLOR] Also remember that you mount the partition (including the number) in this step, but [COLOR="Red"]you do not include the partition number when you run the "sudo grub-install" command later.[/COLOR]
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
          o Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. **[COLOR="Red"]Do not specify a partition number[/COLOR]**. [COLOR="RoyalBlue"](Emphasis mine)[/COLOR]
    * Unmount the partition:
      Code:

      sudo umount /mnt

    * Reboot.



Following these instructions (especially what I emphasized), you would not have installed GRUB to the partition instead of the MBR and would have had no need to "--force" it.

---

### Post by razaz03 on 2010-05-20
> **forestpiskie said:**
> Can you boot the livecd - open nautilus from Places - mount the ubuntu partition - then go to /boot/grub

Have you got menu.lst or menu.cfg?

Possibly need to unmount the disk - right click on the desktop and unmount.

If menu.cfg - reinstall grub [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If menu.lst - reinstall grub - [https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)


Mounted at /media/... I have menu.lst yet when I type grub in a shell output is 'grub' is currently not installed. you can install it by typing: apt-get install grub (tried but output is: unable to fetch some archives, maybe run apt-get update or try with --fix missing)

the menu.lst file and hence your link directs me to a grub1 install but the HOWTO I followed earlier ([http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)) was a reinstall for grub2. 

Really confused here any help would be appreciated.

Regards,

razaz03

---

### Post by razaz03 on 2010-05-20
to -kg-: I was especially careful re your emphasized points (/dev/sdX as opposed to /dev/sdXY) during the initial install, with no joy. 

I believe the sudo grub-install --root-directory=/mnt /dev/sdX command returned the warning message consisting of how unwise it would be to install to a partition/MBR (can't remember exact message but it returned an error until i --forced it. I said it was the craze as googling the error and reading the first thread, people recognize the message since GRUB2 and continue with it anyway)

---

