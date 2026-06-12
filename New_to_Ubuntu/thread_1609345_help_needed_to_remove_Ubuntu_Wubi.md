---
title: "help needed to remove Ubuntu Wubi"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Peterfc on 2010-10-30
I foolishly installed Ubuntu by using Wubi. When the Wubi option came up i just went with it. My windows XP is used for Accounts and Payroll, i have backed up to Usb sticks ect.

I want to remove the Wubi Ubuntu and reinstall Ubuntu into it's own partition. My worry is removing Wubi Ubuntu and causing harm to a machine that has critical data and Proframs on it. The data is backed up but it's still a worry.

I know i can go to Settings, Control Panel, Add and Remove and would it be just this simple to remove Wubi Ubuntu. What other tips could you give to make this easy?

I tried to install Ubuntu from a CD and when i got to the part to Partition the only option i was given was for the whole drive as a single partition. I could find no way to change the partition size. The drive is 250GB.

Thanks for taking the time to read my problem.

---

### Post by anand_30 on 2010-10-30
> **Peterfc said:**
> I foolishly installed Ubuntu by using Wubi. When the Wubi option came up i just went with it. My windows XP is used for Accounts and Payroll, i have backed up to Usb sticks ect.

I want to remove the Wubi Ubuntu and reinstall Ubuntu into it's own partition. My worry is removing Wubi Ubuntu and causing harm to a machine that has critical data and Proframs on it. The data is backed up but it's still a worry.

I know i can go to Settings, Control Panel, Add and Remove and would it be just this simple to remove Wubi Ubuntu. What other tips could you give to make this easy?

I tried to install Ubuntu from a CD and when i got to the part to Partition the only option i was given was for the whole drive as a single partition. I could find no way to change the partition size. The drive is 250GB.

Thanks for taking the time to read my problem.

Even if you uninstall ubuntu you will be asked during boot to either go with windows or ubuntu.
For removing ubuntu entry try this->[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

I myself have done this but its long time ago about 2 years.

But I don't know what will happen if you don't fix MBR and do dual.i think in that case grub will show you the option and if you choose windows then again you have to choose between ubuntu(which is inside windows and uninstalled) and windows.

So IMO backup all your data which you have done then fix your mbr and then install ubuntu side by side.

Now about your question related to ubuntu installation->
completely backup any drive(I prefer last),there is option to specify partitions manually during installation,select it.Now you will get all the information about your drives.Select backedup drive(in my case last).You may divide it into parts or install ubuntu directly to it.

To divide into parts select that drive and delete it(there is a button to delete).Now select that unpartitioned space and partition as you like.Make 1 for swap at last(1Gib sufficient if you don't do hibernating if you do increase it),another for '/' i.e root.If you like you can do another for '/home'.

If still space it remaining let it be,you can retrive it later using disk management in windows or Gparted for ubuntu.[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

Thats it.(May be its too long answer don't get bored :) )

If you find this difficult to understand try [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Look at manual partitioning.

Hope this helps.
:popcorn:

---

### Post by Rubi1200 on 2010-10-30
Uninstalling Wubi via Add/Remove Programs *should* *not* cause any problems.

Backups are always good, of course.

I suggest you also read this:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
especially the sections on installing and uninstalling.

Unless there is something unusual in your setup, there is no reason that uninstalling should cause problems.

---

### Post by cgroza on 2010-10-30
Remove it as any other program. It will not cause any damage to  the computer.

---

### Post by Mark Phelps on 2010-10-30
A recurring problem with removing Wubi from XP is that it leaves the boot entry in boot.ini.  IF you see that still there after Wubi removal, simply open Notepad and remove the one line associated with Wubi.  Don't remove anything else.  That will clean up your boot menu, in fact, with that line gone, you shouldn't be seeing a boot menu after that.

---

### Post by Peterfc on 2010-10-30
Hi Guys 

Thanks for the help.

As advised i did another backup. This time i used system backup System Tools, System and then Backup. After this i had a backup file of 25GB. I then installed a 40GB hard drive to keep it on. I am going to leave Wubu Ubuntu where it as and just do a clean install of Ubuntu in it's own partition. 

New question i tried to use Gparted but this came up with an error and said to Fdisk this i tried but i didn't remember the Fdisk ?. I don't have Acronis or Partition Magic.

Gparted said to run Fdisk and then reboot twice. But does anybody know the parameter to use I think it was something like Fdisk R ???

Thanks again for the help and for taking the time to read my plea for help.

---

