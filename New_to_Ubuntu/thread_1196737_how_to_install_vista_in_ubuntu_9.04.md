---
title: "how to install vista in ubuntu 9.04"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by santhust on 2009-06-25
hi.
I wish to know as to how one can intall windows vista into ubuntu 9.04.
Is it possible to do this through virtual box. Any one who has done this can share his experience.
thanks.

---

### Post by xtjacob on 2009-06-25
I use vista in virtual box, but I didn't install it into it. My laptop came with it and i used vmware converter. The boot-up time is long and the performance is slow if you don't give it a lot of ram.

---

### Post by philcamlin on 2009-06-25
i wouldent use a vm....:popcorn:

---

### Post by Mark Phelps on 2009-06-25
+1 on the NOT installing using a virtual machine.  Vista is slow enough when it has ALL the resources at its disposal.  Unless you have a LOT of memory (4GB or more) and a very fast multi-core processor, by the time you give the VM the resources it needs to run Vista reasonably fast, your host machine will have nearly no resources left.

Would be better to dual-boot.  But realize that will overwrite GRUB and you will have to reinstall that to get back to be able to boot Ubuntu.

---

### Post by santhust on 2009-06-28
> **Mark Phelps said:**
> +1 on the NOT installing using a virtual machine.  Vista is slow enough when it has ALL the resources at its disposal.  Unless you have a LOT of memory (4GB or more) and a very fast multi-core processor, by the time you give the VM the resources it needs to run Vista reasonably fast, your host machine will have nearly no resources left.

Would be better to dual-boot.  But realize that will overwrite GRUB and you will have to reinstall that to get back to be able to boot Ubuntu.

Thanks!
How about running windows xp. i just need to use some things that are easy to install in windows or ran smoothly in it.
I have 2.4 GHz dual core processor and 4 GB of ram.

---

### Post by 3rdalbum on 2009-06-28
Why don't you just install Virtualbox and try it? The process is very simple to work out.

Create a new virtual machine. In the wizard that appears, set the VM to have a virtual hard disk of whatever size you want (use the "dynamic size" option if you want).

Before booting the virtual machine, click on its entry in the list on the left pane, and click the "CD-ROM" text in the right pane. Tell it to pass through your real CD-ROM drive to the guest OS. In the boot order bit of the right pane, tell it to boot from CD-ROM first.

Put in your Windows disc and start the VM, the Windows installer will appear and then the procedure is the same as on real hardware.

After installing Windows, change the boot order to the virtual hard disk.

---

### Post by Mark Phelps on 2009-06-29
> **santhust said:**
> Thanks!
How about running windows xp. i just need to use some things that are easy to install in windows or ran smoothly in it.
I have 2.4 GHz dual core processor and 4 GB of ram.
WinXP is not nearly so resource demanding as Vista.  I have older XP machines that run just fine with 500M of memory.  So, using a VM with XP in it should pose no problems.

---

