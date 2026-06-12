---
title: "Need help installing for dual boot"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by galltopp on 2011-02-04
im trying to install ubuntu 10.10 on a dual boot with vista.
im very confused with the root partition and stuff, im not the slightest bit sure. every where i looked people said leave 10gb for ubuntu, there is 14.65gb of unallocated space ready for ubuntu, can someone just walk me through installing ubuntu, i just got very confused about the root partition and /home and i dont want to mess anything up, thanks

---

### Post by vacco on 2011-02-04
[Here is a nice guide to the Linux file system hierarchy]("http://www.tuxfiles.org/linuxhelp/linuxdir.html"). You can basically just keep your entire Ubuntu system on a single partition, spare a swap partition (twice the amount of your RAM is recommended for a swap partition, equal amount as RAM or greater is required for hibernation to work)

The reason to use more partitions is to preserve data if you want to reinstall your system, for example keep your personal files after reinstall by keeping /home on a separate partition. You will probably be fine with everything on one partition though.

To install, it is basically just to put the CD in the tray, follow the instructions and select to install Ubuntu aside the other OS on your drive (Windows) when it asks about partitioning. Personally, I like to select manual partitioning, but if you are not comfortable with this, just select one of the other options.


Edit: I hope this wasn't too confusing. To clear things up a little bit: unless you select to manually partition the drive, you will not have to worry about a swap partition. Ubuntu will take care of things for you (I think). If you select Try Ubuntu when you boot the live CD, and then select Install to disk, you will have access to the internet (and this forum) if you are puzzled by anything during installation.

---

### Post by galltopp on 2011-02-04
yeah, my laptop seems to overheat after trying it first then turns off, and you mentioned install ubuntu aside another os? that didnt come up for me :S i just got manual partition and something about using the whole disk, i will try again in another 10 mins and let you know

---

### Post by vacco on 2011-02-04
It's been a few months since the last time I installed Ubuntu on a computer, but I thought there should at least be an option to split the disk between your current OS and Ubuntu which you are about to install.

Do you currently have Windows installed and working on your hard drive? If not, that could be the reason why no more alternatives are shown. You should install Windows before you install Ubuntu.

Another possibility I can think of is not enough space.

EXPLANATION (Read if you want to):
If Windows is installed last, it will overwrite GRUB with its own bootloader.
What this means in practice is that your computer will be booting right into Windows even though you have Ubuntu installed.

If you have have to install Windows after Linux (or have should happen to do so by mistake), there is a simple fix using the live CD, but I presume you are not interesting in messing around with stuff like that right now.

---

### Post by galltopp on 2011-02-04
yes im running windows vista now, well i tried it again and it didnt come up, i should have enough space, i have 22.82gb free on the vista bit, and i have 14.65gb unallocated space. mabye acer have their own bootloader or something? because i have to hit f12 straight away to load the cd.

---

### Post by vacco on 2011-02-04
The F12 thing is just a matter of BIOS settings.
The bootloader is installed on your hard drive, meaning it does not kick in until your computer has decided to boot from hard drive.

Partitioning manually should be fairly easy since you already have som unallocated space to use.
Choose to edit partitions manually, then highlight the unallocated space (or right click on it if that doesn't work).

1. Choose create partition.
2. Configure as this:
   - file system = ext4
   - mount point (use as) = /
   - leave free space equal to your RAM or more if you can afford to. If not, leave 2 GB or so. Click OK
3. Choose create partition again (with the remaining unallocated space highlighted)
4. Select swap (might be either under file system or under mount point
   - use the remaining space you left in the last step. Click OK
5. Select Write to disk/Continue (or something)

---

