---
title: "Making a bootable partitioned usb pen drive"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Grawrhee on 2011-04-01
Hello there!

I have a USB pen drive which I want to split up to two partitions, one for installing Ubuntu and one which I want to be able to access from Windows.

How do I fix the partitions the easiest way, with diskmgmt.msc? (disk manager or whatever it's called in English)
What file systems should I use? FAT32 for the Windows-accessible, ext4 for the linux?
 As for the installation itself I'll just follow the "Show me how" from  the download page (and some googling when I fail miserably).

Preferably I'd like grub (or similar) to let me choose whether to boot from the USB or from the regular hard drive, but I can't install it on the computer itself - is this possible? Otherwise I'm totally okay with setting the boot order in the BIOS setup utility instead.

I'm on a laptop running Windows 7,
the USB is a Kingston DataTraveller 112 with 14.4 GB of free space (I've flipped the removable bit so my gullible Windows can do a little more with it),
the distro I'd prefer is Bodhi 1.0.0 (that's pretty much Ubuntu, right?),
it's all very 32-bit.

Cheers,
Sam

---

### Post by sanguinoso on 2011-04-01
You can set up your partition table with parted, and put an ext4 partition and an ntfs partition. Install the ubuntu into ext4. Then Windows will be able to access the ntfs and so will the ubuntu partition on ext4.  When you do a true ubuntu install (As in not the live) it will overwrite the Windows Master Boot Record (I last did this with Windows XP). What this means is, is that when you try to boot Windows when the usb drive is not plugged in, the boot will fail even if you change the bios boot order. What you can do is reset the Windows Master Boot Record, here is a link for Windows 7 [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html). Then when you want to boot ubuntu just enter the boot menu manually (by pressing f12 or whatever) and then select the thumb drive.

---

### Post by false truths on 2011-04-01
I just recently did this on two different USB flash drives. The first step is to check your computer's BIOS and make sure that it supports USB flash drive booting, and make sure it's enabled. Then boot into your Ubuntu live CD.

From the live CD, go into GParted (System-Administration) and find your flash drive in the GParted-Devices menu. If there is an existing partition, shrink it to about half the size of the flash drive (leave a MINIMUM of 4GB for Ubuntu). If there is not an existing partition, make one. The most common type for multiplatform support is FAT32, although NTFS is another viable option. Then make your Ubuntu partition. This one should be EXT4.

Now open the Ubuntu installer program from the desktop, and follow the installation as normal.

When you get to the partitioning choices, choose Manual (Advanced). Go down the list of partitions to choose from and choose the EXT4 partition on your flash drive. Right-click it and open options. Choose EXT4, and set the mount point to "/". Close that window. Next, set the bootloader to install on the flash drive, not in a partition, but the pre-partition space (should be the same label as the flash drive partitions but without a number on the end). Continue installing like normal.

When your install is finished, reboot, remove the CD when it prompts you, and enjoy your new portable Ubuntu system on a flash drive.

---

### Post by bodhi.zazen on 2011-04-01
Just know that Windows will only recognize the first partition, so put Ubuntu into the second.

---

### Post by Grawrhee on 2011-04-01
Thanks for the replies!

I was pretty worried about if the order of partitions mattered to Windows.

Will try following your instructions after some sleep and we'll see how it goes :)

---

### Post by oldfred on 2011-04-01
Herman has a good set of instructions for either flash or SSD.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by C.S.Cameron on 2011-04-01
I think a Live install, (usb-creator, UNibootin), will also only work if it is on the first partition, FAT32, also accessible by windows.

Just make a folder and allocate space for Windows stuff.

You can access this when booting the flash drive by going to filesystem/cdrom. You will need to use gksu nautilus to write to it.

Edit:
You may want a Full install, Judging by the size of your drive, the following step by step works for Full install of 10.10 to USB device with Windows partition, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by Learning Linux 2011 on 2011-04-02
You could also install Linux onto the entire USB drive and then get another USB drive for data.  They are pretty cheap these days.  That way there wouldn't be any confusion.

---

### Post by Grawrhee on 2011-04-02
Success! I now have a little pocket Ubuntu (ended up with 10.10). It worked like a charm (an unusually slow charm, but it is a flash stick after all ^_^ )
And now to redoing pretty much everything because I misread C.S.Cameron's post and got a veeery big swap space.
I didn't plug out the hard drive but that's mainly because I'm not too much into cracking open my laptop if I can avoid it. Still worked great though I had to change the advanced settings to get the GRUB right. 

Thanks for the help, learned a lot!

also,
@Learning Linux 2011
that's nowhere near as fun and then I'd have to haul around two of those really heavy and cumbersome USB drives :)

---

### Post by C.S.Cameron on 2011-04-02
You should be able to plug your flash drive into the computer running the live USB and start gparted. this will allow you to adjust partition size as you require.

---

### Post by Grawrhee on 2011-04-02
Doesn't the order I created the partitions make a difference?
If I want to decrease the size of the swap space, can I then add the removed space to any of the other partitions?

I will however still redo it all. I used a 64-bit live CD instead of a 32-bit. (and on a compleeetely unrelated note, I will also try to find a decent marker pen so I won't mistakenly use a 64-bit live CD instead of 32-bit)

---

