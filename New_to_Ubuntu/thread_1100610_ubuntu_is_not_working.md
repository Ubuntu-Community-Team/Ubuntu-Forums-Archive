---
title: "ubuntu is not working"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by dileepdinesh on 2009-03-19
hi guys, i am a ubuntu beginner, i installed ubuntu inside windows because my project is completely based on linux. So now in between, i had to shutdown the computer during working with ubuntu by pressing the power button of my laptop, now when i try to boot up, it shows that menu.lst is missing, and i am completely screwed...My entire project files is inside it .....so guys please help me...

---

### Post by taurus on 2009-03-19
Pressing the power button to shut down Ubuntu (wubi) or windows is not the right thing to do.

```

**_Cannot boot into Ubuntu_**

Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the windows explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location. 

**_Corrupted NTFS filesystem_**

All reported cases of damaged filesystems so far were from people that hard rebooted (pulling the plug).

When you hard reboot, you can always damage your filesystem whether you use wubi or not. What happens is that new users sometimes get stacked with wubi/ubuntu and since they do not know what to do they tend to hard-reboot more often than necessary. Sometimes they get lucky, sometimes they do not. Since wubi sits on top of ntfs of course when they do not get lucky, ntfs gets corrupted. Sometimes people blame Wubi for that even though a quick googling will show you that there are tons of people experiencing ntfs corruption without having ever used wubi or ntfs-3g (and a full software industry lurking on that...), most of them after a hard reboot...

If ntfs filesystem gets corrupted you have to run chkdsk /r from the windows recovery console on the Windows CD (or other recovery CD available on the web) or in the msdos console (if you can boot into Windows). At the moment there is no fsck for ntfs on the Linux side, otherwise it would be possible to fix errors automatically within Linux itself, as it happens for other filesystems, without having to rely on Windows tools.

Best advise is to simply avoid hard rebooting. Whatever the OS. 

```

---

### Post by dileepdinesh on 2009-03-19
hi, thanx for the reply, but when i chek the ubuntu folder from inside windows, i can't find the disks folder, but i did find that found.000 folder with the same files you told inside, wht shud i do

---

### Post by avtolle on 2009-03-19
Run chkdsk /r would be my recommendation (as set out in taurus' post, *supra*).

---

### Post by LowSky on 2009-03-19
first off Reboot windows... corectly, Start menu> shut down and choose reboot, see if things come back correctly,  sometimes they do

And please shudown you PC the proper way, otherwise you risk damaging the hard drive and possibly causeing a short out of the processor or power supply, and none of that is fun.

Im fixing this because Taurus wrapped it in CODE tags that make it hard to read ( side scrolling and such)

> Cannot boot into Ubuntu

Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). 
If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. 
If you do not see those, look for found.000. You need to change the windows explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location. 

Corrupted NTFS filesystem

All reported cases of damaged filesystems so far were from people that hard rebooted (pulling the plug).

When you hard reboot, you can always damage your filesystem whether you use wubi or not. What happens is that new users sometimes get stacked with wubi/ubuntu and since they do not know what to do they tend to hard-reboot more often than necessary. Sometimes they get lucky, sometimes they do not. 
Since wubi sits on top of ntfs of course when they do not get lucky, ntfs gets corrupted. Sometimes people blame Wubi for that even though a quick googling will show you that there are tons of people experiencing ntfs corruption without having ever used wubi or ntfs-3g (and a full software industry lurking on that...), most of them after a hard reboot...

If ntfs filesystem gets corrupted you have to run chkdsk /r from the windows recovery console on the Windows CD (or other recovery CD available on the web) or in the msdos console (if you can boot into Windows). At the moment there is no fsck for ntfs on the Linux side, otherwise it would be possible to fix errors automatically within Linux itself, as it happens for other filesystems, without having to rely on Windows tools.

Best advise is to simply avoid hard rebooting. Whatever the OS.

---

