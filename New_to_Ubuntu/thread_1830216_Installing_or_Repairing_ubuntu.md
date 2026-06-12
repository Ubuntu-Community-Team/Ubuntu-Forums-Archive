---
title: "Installing or Repairing ubuntu"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by sauyadav on 2011-08-21
Hi, I have Ubuntu 11.04 installed on a partition (a 160 GB disk with a partition formatted in ext3 and a 2 GB partition for swap). My primary OS is Windows 7 and I use Ubuntu as a backup OS and sometimes for net surfing (since it boot quicker than Windows 7). Windows 7 is installed in another 1 TB HDD. Both disks are bootable with their respective OS . I used EasyBCD to make entry for Ubuntu in Windows boot menu. Some days ago I foolishly deleted a folder from Ubuntu drive (which I mount in Windows 7 using Ext2Fsd). Now Ubuntu isn't booting neither from Windows boot menu, and when I try to boot directly from Ubuntu HDD by changing boot queue from BIOS, it shows boot menu of GRUB but crashes after sometime while starting Ubuntu.

Is there any way to repair Ubuntu installation?
And if there isn't then is there a way to fresh install Ubuntu in that partition without formatting it? (I have lots of data in that drive)

---

### Post by elgordodude on 2011-08-21
Do you know which folder you deleted?

It can most likely be repaired, but if I were you, and seeing as how you probably have the space on your 1 tb drive I would boot into windows and start copying all the files and folders you know you want on to that drive. May not be necessary but a backup never hurt anyone, (at least that I know of)

---

### Post by Mark Phelps on 2011-08-21
> **sauyadav said:**
> Is there any way to repair Ubuntu installation?
Before you get into reinstalling, you should try the following:
1) Disconnect the Win7 drive
2) Boot into the Ubuntu drive, holding down a SHIFT key the whole time.  This should force the display of a GRUB menu.
3) When you get the menu, choose the top-most Recovery Mode entry
4) Then, choose the option to Repair Broken Packages.

When that finished, choose the option to reboot normally.

That should get you back into a desktop.

If that works, then do the following:
1) Reconnect the Win7 drive -- but CONTINUE to boot from the Ubuntu drive
2) Boot into Ubuntu.  Open a terminal and enter "sudo update-grub". That will regenerate the GRUB menu and add an entry for Win7.
3) Reboot.  You should see a GRUB menu now.

---

### Post by sauyadav on 2011-08-22
> **Mark Phelps said:**
> Before you get into reinstalling, you should try the following:
1) Disconnect the Win7 drive
2) Boot into the Ubuntu drive, holding down a SHIFT key the whole time.  This should force the display of a GRUB menu.
3) When you get the menu, choose the top-most Recovery Mode entry
4) Then, choose the option to Repair Broken Packages.

When that finished, choose the option to reboot normally.

That should get you back into a desktop.

If that works, then do the following:
1) Reconnect the Win7 drive -- but CONTINUE to boot from the Ubuntu drive
2) Boot into Ubuntu.  Open a terminal and enter "sudo update-grub". That will regenerate the GRUB menu and add an entry for Win7.
3) Reboot.  You should see a GRUB menu now.

I did this. Repair broken packages option never came. Ubuntu booted, some text came to screen. After some seconds display turned off, and then, I left it for 15 min in case something is happening (hdd access light was blinking). Keyboard was working, I checked by toggling Numlock. Finally I pressed Ctrl+Alt+Delete and System restarted.

---

### Post by sauyadav on 2011-08-22
> **elgordodude said:**
> Do you know which folder you deleted?

It can most likely be repaired, but if I were you, and seeing as how you probably have the space on your 1 tb drive I would boot into windows and start copying all the files and folders you know you want on to that drive. May not be necessary but a backup never hurt anyone, (at least that I know of)

I don't remember. I also don't have much space left on 1 TB drive, so backup using it is not possible. Therefore, installing Ubuntu without formatting the drive is only solution for me, if its possible.

---

### Post by Wim Sturkenboom on 2011-08-22
Buy an external HD and backup on there ! You need one anyway, especially if you fiddle with systems the way you do :).

And don't keep it connected when not in use as it might get corrupted if your OS does not shutdown properly.

---

### Post by sauyadav on 2011-08-22
> **Wim Sturkenboom said:**
> Buy an external HD and backup on there ! You need one anyway, especially if you fiddle with systems the way you do :).

And don't keep it connected when not in use as it might get corrupted if your OS does not shutdown properly.

I don't fiddle with the system that much, I deleted that folder because it has name like 'dsfdst57rhfgj8k8' (don't actually remember its name) which MS update sometimes make in the root of drives other than windows drive when installing an update. I am planning to borrow an external from a friend, but before that I want to confirm if I can do anything else (I would prefer if I don't have to format, and reinstall ubuntu, it take lots of time to get things back as they were)

---

### Post by candtalan on 2011-08-22
Other things such as  the need for a good backup aside:

In the Ubuntu install process, fairly early on, when the partitioner has started, you are asked to decide which partition the installation should target. In this same screen, there is an 'advanced' option, which may be labelled as 'Other' or 'Something else' or whatever. Choose this, and you will be shown a simple GUI list of partitions and drives. Chose the existing Ubuntu system partition (not the swap) and opt to 'change' it.

When you see the details, set it for use as your file system (you say it is ext3) and as root ( / ) but - and this is very important - leave the 'format' box UNCHECKED so it will not be formatted.
Then proceed.

Ubuntu install will overwrite all system and other files but will not try to delete or overwrite your data area.

HTH

It is quite usual for GNU/Linux based systems such as Ubuntu to use a boot loader such as grub which is built in, and this will be easily capable of managing Windows 7 and other OSs if you wish. I have machines with several hard drives each with several OSs on them.

---

### Post by sauyadav on 2011-08-22
> **candtalan said:**
> Other things such as  the need for a good backup aside:

In the Ubuntu install process, fairly early on, when the partitioner has started, you are asked to decide which partition the installation should target. In this same screen, there is an 'advanced' option, which may be labelled as 'Other' or 'Something else' or whatever. Choose this, and you will be shown a simple GUI list of partitions and drives. Chose the existing Ubuntu system partition (not the swap) and opt to 'change' it.

When you see the details, set it for use as your file system (you say it is ext3) and as root ( / ) but - and this is very important - leave the 'format' box UNCHECKED so it will not be formatted.
Then proceed.

Ubuntu install will overwrite all system and other files but will not try to delete or overwrite your data area.

HTH

It is quite usual for GNU/Linux based systems such as Ubuntu to use a boot loader such as grub which is built in, and this will be easily capable of managing Windows 7 and other OSs if you wish. I have machines with several hard drives each with several OSs on them.

My files are in home/sau/ folder, should I move them somewhere else like in a new folder in root?

---

### Post by candtalan on 2011-08-22
> **sauyadav said:**
> My files are in home/sau/ folder, should I move them somewhere else like in a new folder in root?

during the process (advanced install) I described, the /home/sau folder will be the only one to be left alone and not overwritten. So, no, do not 'move' it to another place on the same system. However it is strongly advised to copy and paste that folder (turn on view hidden files first) into another drive  such as either your Windows system or another perhaps external hard drive.
The /home/[user] folder is  your own stuff, a bit like windows My Documents (only better  :-)  )
so it is good to keep copies of it or its contents.

---

### Post by sauyadav on 2011-08-22
I am installing Ubuntu right now, Installer gave me an option to upgrade which will keep my files, as well as installed programs, but will reset the system files. Thanks for responding.

---

### Post by Wim Sturkenboom on 2011-08-22
I'll pray for you ;)

Good luck.

---

