---
title: "Doubt about virtual machine on ubuntu!!!"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-09-29
If i go for installing Windows xp in virtual machine(Qemu Launcher) on ubuntu then if I remove ubuntu to install new released edition then would i will be able to recover & restore that in this new machine in same virtual machine?

---

### Post by muteXe on 2009-09-29
Would work (i think) if you had your home folder in a separate parition.

---

### Post by eshant_engineer on 2009-09-29
please can you give more explanation....

Thanks for replying

---

### Post by undecim on 2009-09-29
You don't need to reinstall your operating system to upgrade Ubuntu, so you keep all of your files an settings.

If you want, though, you can save the virtual hard disk of the machine to another computer

---

### Post by Calmor on 2009-09-29
> **eshant_engineer said:**
> If i go for installing Windows xp in virtual machine(Qemu Launcher) on ubuntu then if I remove ubuntu to install new released edition then would i will be able to recover & restore that in this new machine in same virtual machine?

You can either keep your home folder on a different partition so that it's not affected by the upgrade, or you can back up your home partition (recommended anyway) and then install the virtual machine onto your new edition from your backup.

I've ran VirtualBox for a while and have had no issues.  In fact, I keep the virtual hard drive file on an NTFS partition so that I can access it from both Windows and Linux.  In that time, I've upgraded from 8.10 to 9.04, and also upgraded Windows from Vista to 7.  I just had to move the hard drive file to my Linux partition while I upgraded Windows.

One of the biggest benefits of the virtual machine is that you can move it to another computer or give it more resources as required.

---

### Post by muteXe on 2009-09-29
Your VM instance is just a big file, so like a few others have mentioned you can move it about like one. Stick it on an external drive for example, then copy it back, if you do decided to reinstall your OS.

---

### Post by eshant_engineer on 2009-09-29
Thanks all for helping.....

---

### Post by Jerold on 2009-09-29
When you copy and move the VM around, keep an eye on your permissions. You may want to record the file permissions as they stand now. For example, [ls /vm/path -hal > vm_permissions.txt]. Use the preserve arguments when using a tar or cp command. If you copy straight to a NTFS partition you will loose your permissions unless you archive the files within a tar file.

---

