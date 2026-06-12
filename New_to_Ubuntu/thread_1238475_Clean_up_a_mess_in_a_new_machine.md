---
title: "Clean up a mess in a new machine"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by AlanAbbott on 2009-08-12
I started of by installing UBUNTU 9.4 64bit, pasted over about 34GB of data from other machines. The second step was to install VIRTUALBOX and under it WINDOWS XP 32 home & pro & 64, with several propriety systems each. Next I tarted to test the use of two motitors at a time with no success. (LG 17" LCD, Bhango 22" wide and a Phillips 17" CRT) with on board Geforce (M2N-VN DVI). I installed the NVIDIA drives. Next I installed Windows XP 64 in a part of the disk drive after shrinking it about 40GB. Lossing my access to UBUNTU, I recovered my access through the futher shrinking the disk by 10GB, this instalation was not succesful. I futher shrank by 2.5GB and was succesfull in this istallation and obteined the entries to the three OS, small UBUNTU, decktop UBUNTU and WINDOWS XP 64bit. I am left with 10GB not used space. the next step I took was to get a ATI RADEON HD4350 and test the two monitors with this as the second outlet was digital only (DVI-D).
I down loaded the ATI drivers but could not fined were to change the parameter sugested in the HOWTO. Now my machine has started to run extremly slow. I think the best would be to start fresh  reinstalling everything.
My questions are:
Can I some haw reinstall UBUNTU in the 234GB it is using now without lossing my data and the virtual machines.
How can I edit the initial loader, were it asks which OS to boot.
How can I recover the lost 10GB pluss the 2.5GB of the UBUNTU used to recover the access to the other OS.

---

### Post by AlanAbbott on 2009-08-13
Well, I started with passing my most important data (photos & source files) to the windows partition and then reinstalled Ubuntu, I lost the VirtualBox with everithing in it.
The Grub straitened out, now the first OS is the large UBUNTU. I still have to test to see if the stand alone windows work, I can see its contence and my files are still available in this system.
Thanks for letting me write out  my problem, this way I was able to see it in a new light.
The two monitors not working was because the HDV adapter was a HDV-D to VGA and not a HDV-I to VGA. I changed it and now it works. I still have to set it up so that I do not have to uncheck mirror each time I restart.

---

### Post by lkraemer on 2009-08-13
If you didn't format when you did the re-install of Ubuntu, your VDI's
should still be in their folder.  Go to PLACES -> HOME FOLDER
then do a CNTRL H scroll down to .VirtualBox, then to HardDisks
and your Virtual Disk Images should still exist.  If so, just
re-install VirtualBox (PUEL Version) and re-create your Guest OS,
and then attach one of these VDI's to your Guest OS.  It will work fine.
(Be sure to install the Guest Additions for Windows as a Guest OS.)

lkraemer

---

### Post by AlanAbbott on 2009-08-14
I reinstalled VirtualBox and found everything, thanks. What are the guest additions for windows, were do I find then?

---

### Post by 3rdalbum on 2009-08-14
> **AlanAbbott said:**
> I reinstalled VirtualBox and found everything, thanks. What are the guest additions for windows, were do I find then?

When you have the virtual machine running, go to whatever the second menu is in Virtualbox and select "Install Guest Additions". In My Computer on Windows, you'll see a CD device that contains the drivers.

If you want to install 3D drivers you must be in Safe Mode (on Windows).

---

### Post by philinux on 2009-08-14
Lots of peeps who uses virtualbox seem to miss this little gem.

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

