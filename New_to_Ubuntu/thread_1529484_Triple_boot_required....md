---
title: "Triple boot required..."
date: 2010-07-12
forum: New to Ubuntu
---

### Post by gauravkumar on 2010-07-12
Hi All,
 
I really don't know if this is possible or might make system unstable but I just want to do the same.
I have windows 7 installed on my system. And on the xternal HDD in have Ubuntu 10.04 installed.
What i want now i to retain Ubuntu on the xternal HDD and also install BackTrack Linux over the same...
is it possible and how can i do it without formatting the Ubuntu....
 
Note: My Xternal HDD has only one partition with Ubuntu installed over it...
 
Thanks in Advance
Gaurav Kumar

---

### Post by mikewhatever on 2010-07-12
Resize the Ubuntu partition, install Backtrack. Theoretically, you can install as many operating systems as you like, as long as there is sufficient disk space. Obviously, you can not install backtrack over Ubuntu and retain Ubuntu at the same time.
You might want to read up on partitions and partitioning first.

---

### Post by audiomick on 2010-07-12
Hi.
You might want to read up on Grub as well.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I don't know how the Back Track installer behaves, but there is a slight chance that you might have to re-install or re-configure Grub.

---

### Post by rsvr85 on 2010-07-12
> You might want to read up on Grub as well.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I don't know how the Back Track installer behaves, but there is a slight chance that you might have to re-install or re-configure Grub.

And the windows bootloader.  As Ubuntu is installed on an external drive i assume you have GRUB installed on the same disk? Meaning if it's not priority in the BIOS or plugged in, Windows' bootmanager kicks in.  
The same thing audiomick mentioned could happen to the Windows bootmanager too (potentially making your whole system unbootable).

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

```
bootrec /fixmbr
``` usually does the trick.

[Create a Bootable Windows 7 System Repair USB Drive]("http://mintywhite.com/windows-7/7maintenance/create-bootable-windows-7-system-repair-usb-drive-netbooks/")
[create the Recovery DVD]("http://mintywhite.com/windows-7/burn-the-windows-7-iso-to-a-dvd-how-to/")
[Download a Windows 7 System Repair/Recovery Disc]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by gauravkumar on 2010-07-12
Well i faced the issue of my Windows MBR overWritten by Ubuntu's MBR but i was able to fix that through repairing...and Yes I Installed mbr on the xternal disc itself....
Can't i partition and do the same thing with backtrack...
i mean can i install two boot mbr's for ubuntu and backtrack over the same xternal hdd.

---

### Post by mikewhatever on 2010-07-12
It's important to understand, there is no such thing as Windows MBR, Ubuntu MBR and so on. MBR is simply the first sector on an HDD that points the boot process somewhere else.

---

### Post by rsvr85 on 2010-07-12
> **gauravkumar said:**
> Well i faced the issue of my Windows MBR overWritten by Ubuntu's MBR but i was able to fix that through repairing...and Yes I Installed mbr on the xternal disc itself....
Can't i partition and do the same thing with backtrack...
i mean can i install two boot mbr's for ubuntu and backtrack over the same xternal hdd.

I don't see any reason why not.  Providing the OS can boot from USB.
Remove your Windows disk just to be safe and prepare to reinstall/repair GRUB (as aforementioned in post#3)

---

