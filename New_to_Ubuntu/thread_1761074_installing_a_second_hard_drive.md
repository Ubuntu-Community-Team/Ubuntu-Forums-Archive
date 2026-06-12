---
title: "installing a second hard drive"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-17
Hi folks, I have an existing hard drive that has Windows 7 on it.  I want to install ubuntu on a secondary drive by itself.

Question 1. 

Will the menu to boot give me the choice of the OS to boot to and then go to that drive?

Question 2.

How do I make the Windows drive the secondary drive to boot into and not the C: drive that it currenlt is on?

Can this be done by swapping the drives or changing cables?

Question 3. 

How about installing different linux distros onto the second drive and be able to boot to any of them?


Thanks guys, you are a big help.

---

### Post by YesWeCan on 2011-05-17
Question 1. Yes.

Question 2. "C:" is a windows concept and has nothing to do with the boot order that the Grub boot-loader chooses. By default it will boot Ubuntu first but you can change this.

Question 3. Yes. This would require creating separate partitions for the different distros. You can do this after installing Ubuntu or during the install.


I strongly recommend you disconnect the Windows disk while you do the Ubuntu install. This will make sure that Grub is put on the Ubuntu disk and not on the Windows disk. This way, you will normally boot the Ubuntu disk but you will still be able to boot W7 directly, if you ever need to, as you do now. After the install, reconnect the W7 disk and tell the bios to boot the Ubuntu disk first. In Ubuntu, run 'sudo update-grub' to scan your other disk and add a W7 entry to your Grub menu.

---

### Post by TAspr on 2011-05-17
> **YesWeCan said:**
> Question 1. Yes.

Question 2. "C:" is a windows concept and has nothing to do with the boot order that the Grub boot-loader chooses. By default it will boot Ubuntu first but you can change this.

Question 3. Yes. This would require creating separate partitions for the different distros. You can do this after installing Ubuntu or during the install.


I strongly recommend you disconnect the Windows disk while you do the Ubuntu install. This will make sure that Grub is put on the Ubuntu disk and not on the Windows disk. This way, you will normally boot the Ubuntu disk but you will still be able to boot W7 directly, if you ever need to, as you do now. After the install, reconnect the W7 disk and tell the bios to boot the Ubuntu disk first. In Ubuntu, run 'sudo update-grub' to scan your other disk and add a W7 entry to your Grub menu.


So, in your reply, *"I strongly recommend you disconnect the Windows disk while you do the  Ubuntu install. This will make sure that Grub is put on the Ubuntu disk  and not on the Windows disk"* This will only install it on the drive connected?

---

### Post by YesWeCan on 2011-05-18
Obviously a disconnected drive cannot be written to.
You dont have to disconnect it but the trouble is hat the Ubuntu installer defaults to putting Grub on the MBR of the first disk, called sda, which is designated by your bios and is probably your W7 disk. You can tell the installer to change this if you keep a lookout for the menu. If it is easy to disconnect the disk then you avoid any potential mistakes.
There are regular posts here where newbies have not realised all this and ended up deleting Ubuntu or reinstalling it and then changing the grub location and then not being able to boot Windows. Best to keep the Windows disk untouched by Ubuntu.

---

### Post by TAspr on 2011-05-18
> **YesWeCan said:**
> Obviously a disconnected drive cannot be written to.
You dont have to disconnect it but the trouble is hat the Ubuntu installer defaults to putting Grub on the MBR of the first disk, called sda, which is designated by your bios and is probably your W7 disk. You can tell the installer to change this if you keep a lookout for the menu. If it is easy to disconnect the disk then you avoid any potential mistakes.
There are regular posts here where newbies have not realised all this and ended up deleting Ubuntu or reinstalling it and then changing the grub location and then not being able to boot Windows. Best to keep the Windows disk untouched by Ubuntu.


Gotcha, I should have reworded that a little different..  Man, this is scarey, as I do not want to screw up the windows drive.

---

