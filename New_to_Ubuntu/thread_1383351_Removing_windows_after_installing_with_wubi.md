---
title: "Removing windows after installing with wubi?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-01-17
Greetings all,
Recently I had been using XP and got a virus. I decided to try throwing in the towel with Windows and I installed Ubuntu from within the viral XP. I did this mostly because I didn't have convenient access to a CD burner at the time.
Now that I'm pretty certain I'll be happy with just Ubuntu, I'd like to remove Windows completely. Preferably I'd like to do this without having to completely re-do my current Ubuntu installation and re-install all software, which is fine if I must but it'd be a pain. I've seen various posts around the internet that discuss bits and pieces of how to do this, such as wiping one existing partition, making it into EXT3, copying the entire Ubuntu partition there, etc.
Is there a tenable (for me, a newbie) way to do this?
If it matters, here is my setup (please excuse the antique hardware, it's how I roll):
First IDE cable has 2 hard drives, master is a 10gb and slave is a 40gb
Master drive has 7.5gb and 2.5gb FAT32 partitions. XP installation lives on the bigger one.
Slave drive has 2 20gb FAT32 partitions. One of these has the Ubuntu installation.
Also, if this weren't possible and I wanted to wait a bit before re-installing everything, is there a way to set things up to skip the Windows bootloader and go directly to GRUB? I tried just changing boot device priority in my BIOS to the second drive, and it doesn't work.
Thanks!

---

### Post by Shhnap on 2010-01-17
What you need is LVPM: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

That will do all of the hard work for you I believe. :D

---

### Post by Paqman on 2010-01-17
Once you've migrated Ubuntu onto it's own partition using LVPM, you can remove Windows by doing the following:
[LIST=1]
[*]Boot into your LiveCD.
[*]Go to System > Admin > Gparted partition editor.
[*]If any swap partitions are mounted right click on them and "swapoff".
[*]Delete the Windows NTFS partition.
[*]Expand the Ubuntu partition(s) into the space created.
[*]Boot into Ubuntu and run the command "sudo update-grub" to clean up the Grub menu.
[/LIST]

I'd advise backing up any crucial data before messing about with partitions.

---

### Post by knurledflanges on 2010-01-17
Seems ideal, with my concern being the note on the LVPM page that it was last tested with 8.04 (I have 9.10). Does this seem like a reasonable thing to try?

Also, just to be clear, does LVPM set up GRUB on the drive that houses the new Ubuntu installation partition at the time that it does the swap? If so, it seems like what I should do (after backing everything up) is:
1. Use gparted to format the 20gb partition that doesn't house my current Ubuntu installation on the second hard drive as EXT3 to use as a new home for Ubuntu.
2. Use gparted to format the 2.5gb partition on the first drive as linux-swap to use as a swap file (it doesn't have any program files on it now and I have 1gb of ram).
3. Use LVPM to swap Ubuntu onto the 20gb EXT3 partition.
4. Point my BIOS to the 2nd hard drive for boot priority.
5. Test that GRUB loads with no Windows bootloader first and the transferred Ubuntu installation works.
6. Wipe the original 20gb FAT32 partition that Ubuntu was installed on using wubi and use gparted to expand the new Ubuntu partition or do whatever with the rest of that drive.
7. Wipe, unplug, or do whatever with the 10gb drive that Windows and the swap file live on.

That should work barring any compatibility issues with 9.10, right?
Thanks so much for the help.

---

