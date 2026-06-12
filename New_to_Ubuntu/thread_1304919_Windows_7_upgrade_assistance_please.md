---
title: "Windows 7 upgrade assistance please"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Threbus5 on 2009-10-29
Hello.
I have Vista and Ubuntu dual boot on a Gateway notebook.

If booted into Vista and after an attempt to upgrade to Windows 7 the computer posts the message that the NTFS partition is not really a Windows NTFS. Then it insists on a clean Windows 7 install.

I like my Ubuntu and its fully operational settings.
Do not like Vista at all but need some direct Windows compatibility. Do not believe that a clean install should be necessary - only want to replace Vista with Windows 7 on the Vista partition.

Searched the forums and found nothing that seemed quite applicable but will look again if necessary. I know how to backup and restore Ubuntu and can use fdisk.

Could this process remove Vista and install Windows 7 with Ubuntu?-> Backup Ubuntu to an external, reformat the Ubuntu partion to NTFS, upgrade to Windows 7, then re-partition, re-install, and restore Ubuntu?

If that would not work, could someone please describe the easiest most successful process to just replace Vista with Windows 7 and leave Ubuntu alone?

Thank you.

---

### Post by mikewhatever on 2009-10-29
We don't provide support for W7 here, but in your case, it seems rather obvious. Install W7 using the ntfs partition.

---

### Post by Threbus5 on 2009-10-31
> **mikewhatever said:**
> We don't provide support for W7 here, but in your case, it seems rather obvious. Install W7 using the ntfs partition.


Thank you Mike.
I appreciate your taking the time to respond. However, because multiple threads exist in this forum for resolving Ubuntu and windows problems, such as dual boots, partitioning, drivers, and other interoperability issues - including those associated with Windows 7 - my request seems reasonable for forum discussion.

It seems highly unlikely that I am the only poor soul trying to upgrade from Vista to Windows 7 on a Dual boot Vista/Ubuntu machine.

I will keep experimenting and eventually among the forum members, someone of us will figure it out.

Take care.

---

### Post by Merk42 on 2009-10-31
Not sure why it's giving you the error about not being NTFS, are you sure you're pointing Windows 7 to the correct partition?
Show us the output of```
sudo fdisk -l
```

You should just be able to upgrade/format your NTFS partition (back up your files on the NTFS partition first).  At which point Windows bootloader will override GRUB, so you'll have to reinstall GRUB via a LiveCD.
Also, what version of Ubuntu are you running as there has been a change to GRUB2 as of Karmic.

---

### Post by halitech on 2009-10-31
I think the underlying issue is why does Win7 think the NTFS partition is not a valid NTFS partition? 

Would it work to use Partition Editor (either in Ubuntu or from the Live CD) to delete the windows partition completely, install Win7 in that space, and then repair GRUB?

Is GRUB currently installed to the MBR or another location?

---

### Post by phidia on 2009-10-31
Threbus5, You might want to check the Win7 forum [here]("http://www.sevenforums.com/").

---

### Post by sandyd on 2009-10-31
> **Threbus5 said:**
> Thank you Mike.
I appreciate your taking the time to respond. However, because multiple threads exist in this forum for resolving Ubuntu and windows problems, such as dual boots, partitioning, drivers, and other interoperability issues - including those associated with Windows 7 - my request seems reasonable for forum discussion.

It seems highly unlikely that I am the only poor soul trying to upgrade from Vista to Windows 7 on a Dual boot Vista/Ubuntu machine.

I will keep experimenting and eventually among the forum members, someone of us will figure it out.

Take care.
mine went completely smoothly, have you tried running checkdisk?

---

### Post by cariboo on 2009-10-31
Actually, I ran into a Vista installation on a fat 32 partition yesterday, it was on an Acer desktop. You should be able to check what the partition type is from Ubuntu.

---

### Post by mwalimu54 on 2009-10-31
Windows has historically not played nicely as a second OS.  MS doesn't seem to think that anyone might run two OS's.  From my limited perspective (I haven't run Windows on my machine for over a year) if all else fails you could totally wipe your HD, install 7 first, and then install Ubuntu.  Ubuntu does very well with sidling up to another existing OS, so to install in that order usually works better.  Maybe someone else can point out a less labor-intensive fix.

---

### Post by Mark Phelps on 2009-11-01
> **Threbus5 said:**
> Hello.
I have Vista and Ubuntu dual boot on a Gateway notebook.

If booted into Vista and after an attempt to upgrade to Windows 7 the computer posts the message that the NTFS partition is not really a Windows NTFS. Then it insists on a clean Windows 7 install.
Have you looked at the NTFS partition and confirmed that is it Active and not hidden?  If Gateway installed a hidden NTFS partition at the beginning of the drive (e.g., to use to hide a recovery image), it could be that Seven sees that and is getting confused.
> Could this process remove Vista and install Windows 7 with Ubuntu?-> Backup Ubuntu to an external, reformat the Ubuntu partion to NTFS, upgrade to Windows 7, then re-partition, re-install, and restore Ubuntu?
That COULD work, but Seven is picky in what it will actually "upgrade".  Lots of conflicting info out there as to what WILL and WILL NOT upgrade.
> If that would not work, could someone please describe the easiest most successful process to just replace Vista with Windows 7 and leave Ubuntu alone?
Not that a true Seven "upgrade" requires evidence of a prior Vista installation -- it either needs to find Vista already installed and activated on the machine, or you need to have a Vista Installation DVD.  An OEM-provided recovery CD is likely NOT to work.

Be sure to use the Seven builtin option of burning a Recovery CD when you get it installed and working.

---

