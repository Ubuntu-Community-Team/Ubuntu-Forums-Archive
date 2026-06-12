---
title: "Bootloader doesn't install"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Valeralol on 2010-08-30
Hi all,I bought dvd-rom drive and now can boot ubuntu installer)But now i've got another broblem.When istallation is about ~90% (Installing bootloader process)mistake happens.I've got 2 HDD(First has 2 ntfs partions for Windows,Second has ext4 Partion for Ubuntu and Swap partion) and Ubuntu cant install bootloader to no of that partitions...I think Win7 can prevent this...How can i solve this problem?Thanks.

---

### Post by Windows Nerd on 2010-08-30
> **Valeralol said:**
> Hi all,I bought dvd-rom drive and now can boot ubuntu installer)But now i've got another broblem.When istallation is about ~90% (Installing bootloader process)mistake happens.I've got 2 HDD(First has 2 ntfs partions for Windows,Second has ext4 Partion for Ubuntu and Swap partion) and Ubuntu cant install bootloader to no of that partitions...I think Win7 can prevent this...How can i solve this problem?Thanks.
Please post the output of:

```
fdisk -l
```

When you installed, did you select manually specify partitions or guided?

Scott

Edit: I forgot to tell you that you will need to enter the above command into a terminal from your LiveCD.

---

### Post by Valeralol on 2010-08-31
Here it is.

---

### Post by andrewthomas on 2010-08-31
> **Windows Nerd said:**
> When you installed, did you select manually specify partitions or guided?


or did you choose to use entire (/dev/sdb) drive?

---

### Post by Valeralol on 2010-08-31
I tried all variants.Nothing works.

---

### Post by Valeralol on 2010-08-31
Any solution?

---

### Post by jtarin on 2010-08-31
> **Valeralol said:**
> I tried all variants.Nothing works.
That statement rules out a solution...there must be one varient you didn't try.:P

Unplug your Windows drive and work with /dev/sdb alone. Make a it a primary partition not extended.

Your /dev/sdb......try to delete all partions, then format the drive as fat32. Then partition and format as Linux. Remove the boot flag from that partition. It is not your boot partition.Plug your other drive back and now run the fdisk command again and post the results

---

### Post by ivikas on 2010-08-31
Hello Valeralol,
              Do you have an ubuntu or Linux OS Already installed on the second Harddisk? If yes,may be i can help you.I got this same error, when the installation reaches about 95 percent,it says that boot loader cannot be installed and if we select the partition,it won't install in any of it and the next option is to install withouth grub.So, all it happens is that if you have an Linux OS already installed(in my case ubuntu 8.04 LTS Desktop),the grub version used in this earlier os is an old one compared to the ubuntu 10.04 LTS Desktop,so the ubuntu 10.04 LTS Desktop's Grub Won't Install.A way to get over this is,to download mbrfix.exe(available for windows 7 64 and 32 bit.

```
 http://www.sysint.no/nedlasting/mbrfix.htm 
```

Run this program inside the windows 7 to fix the MBR.This will cause the old grub to be removed from the MBR(Master Boot Record) replacing with windows 7 Boot loader.Once completed do the install process over again and it will work.

I hope this will be  helpfull to  you.

---

