---
title: "Shrinking the windows partition safely?"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-01
Okay, I just reinstalled windows. I had the drive partitioned like I want it, but it overwrote everything. Stupid windows. Heres the current partitions:
 
200mb (system), 282GB Windows, 15GB unallocated. The 15GB WAS Recovery and HP tools, but I don't want them. Windows WILL NOT let me shrink it past 144GB. This is leaving more than half my drive for windows! 
Heres a screenie for ya. 
[IMG]http://img51.imageshack.us/img51/4999/parion.png[/IMG]
 
 
Okay. I want my drive partitioned like this. (values are approx.)
 
Windows Sda1 - 100GB
Ubunt Sda2 "/" - 50GB
Ubuntu Sda3 "/home" - 125GB
Swap Sda4 -8GB
 
How can I do this? I have a HP windows 7 disk (1 & 2) + Supplimentary disk. I also have an Ubuntu 11.04 disk. I have other OSes on disk if i need to boot off them for anything.
 
 
PS! This is a FRESH install, I have NOTHING on here of importance. I can reinstall at the tip of a hat.

---

### Post by oldfred on 2011-08-01
While this discusses Vista, the issues are the same in 7.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

But if you have nothing to lose, I would just use gparted. I am one that always recommends windows tools for windows and using windows MMC to shrink windows, but if using a new version of gparted you should have no issue. You will have to reboot Windows several times so it can run chkdsk and recognize its new size. And I would be sure to do that before installing Ubuntu. Older versions of gparted would move the start of windows from sector 2048 to sector 63 (like XP was) and then you had to run repairs to make windows work. Now gparted starts Linux partitions at 2048 also and that issue is gone.

Do you have a windows repair CD? The 100MB boot/recovery should let get that far even if you have issues with the main install, but I always want a repairCD or liveCD or USBs for every system I install. And usually have another Linux repair CD or Supergrub just in case.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by YesWeCan on 2011-08-01
For better future flexibility, have you considered making your linux partitions logical, all inside an extended partition? This would leave you with two spare primary partitions rather than none. GParted will make this an easy task.

---

### Post by oldfred on 2011-08-01
+1 on YesWeCan's suggestion of an extended partition.

Plus you could then also create a shared NTFS partition for any data you may want in both systems. I have Firefox & Thunderbird profiles & all photos in the shared NTFS, but now use XP hardly at all. (I have said for a couple of years I was going to stop using Windows but there is one or two things I keep going back for).

---

### Post by Lucypie on 2011-08-02
That blasted 200MB system partition is considered a "primary partition" in which you cannot create more than 4 of. I will try the extended, but will I be able to uses EXT2IFS?
 
PS. I want to thank you all so very very very much. I would be bald and dead by head-banging-on-keyboard if it weren't for everyone helping me. xD

---

