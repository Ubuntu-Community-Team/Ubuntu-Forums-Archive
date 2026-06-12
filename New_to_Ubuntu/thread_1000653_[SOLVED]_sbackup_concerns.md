---
title: "[SOLVED] sbackup concerns"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-03
hi.  following a thread last night, i have installed sbackup, made a backup as recommended using the instructions in this link [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html") and now i find that 1. things *seem[I]*[/I] to be slower.  2. i have a file named 'backup' in var for which 'the folder contents could not be displayed because i do not havethe permissions necessary to view this typeof folder.  and also a couple of icons for 'initrd.img.old' '/vmlinuz' and '/vmlinuz.old' and 'for which i get the message 'could not display... There is no application installed for this file type' when i try to open.
also i notice that on file monitor under 'file systems'  i get the following displayed '/dev/sda5 /   (type) EXT3  (total) 50.1 GiB (free)  36.8 (available) 34.3 GiB (used) 13.3 GiB  27%'  this may not seem significant but since i made a backup and tried to restore following the instructions this 27% has risen from only about  (i think) 14%.
also i am not sure at all whether the thing has actually restored or is in some limbo state.  sorry to seem so long winded but this is the only way i can think to describe what has happened.  i am probably just being overly concerned
oh, and everything seems to be working but just a bit oddly, i just need to know that i am not filling my system with duplicates of itself. (i cant put it all on an external hard drive cos i dont have anything like that
cheers
nigel

---

### Post by scorp123 on 2008-12-03
> **capnthommo said:**
>  i have a file named 'backup' in var for which 'the folder contents could not be displayed because i do not havethe permissions necessary to view this typeof folder.  Anything outside your own /home belongs to the administrative account "root" or a system account (stuff such as "bin", "daemon", "www", "syslog", and so on). You're not supposed to mess with those items unless you know what you are doing. The "error" is therefore correct.

> **capnthommo said:**
>  'initrd.img.old' '/vmlinuz' and '/vmlinuz.old'  "initrd" stands for "initial root disk"; it is a compressed file that contains drivers that are needed for your system to load. The suffix "old" suggests that this one contains the "initrd" of your previous kernel image. You probably did a system update (just like everyone else) and your system has retained an older copy of "initrd", just as it is supposed to do. "vmlinuz" is the compressed Linux kernel image that is loaded into memory upon system boot. "vmlinuz.old" is the previous version. You're not supposed to touch those files unless you know what you are doing.

> **capnthommo said:**
>  i just need to know that i am not filling my system with duplicates of itself.  Hard to tell based on your description.

As for backups: 
[http://ubuntuforums.org/showthread.php?p=6281196#post6281196](http://ubuntuforums.org/showthread.php?p=6281196#post6281196)

Are you sure that you can restore everything with "sbackup" in case you have a catastrophic failure? I personally am not convinced about that. But hey, it's your system, your data, your mileage. And it will vary. But if you're willing to learn how it's done so you can really get your data back or at least tell your newly installed system to install the same packages your old system had then read above please.

---

### Post by capnthommo on 2008-12-03
Thanks v much.  so thats cleared up the mystery of the files. 
i am *not* certain my system is backed up so i can recover from a disastrous crisis but until i can get a separate hard drive/storage i shall have to take my chances.  the link you included looks interesting and i shall have to give it a bit of deep reading.  i certainly agree that command line is better than using a gui system, its just that at present i have little - when i say little i mean no - experience of it.  it is another of the ubuntu/linux learning processes i need to address.  as i have said in another place, i have years experience using m/soft/windows etc and that doesn't encourage the user to become responsible for ones own system/decisions so i have a lot to learn.  still - whats life if not ba journey.  the strange increase in memory used must be down to the backup copy since its about doubled so i imagine that accounts for it.
anyway, thanks, you have calmed my fears a great deal
cheers
nigel

---

### Post by scorp123 on 2008-12-03
> **capnthommo said:**
>  i am *not* certain my system is backed up so i can recover from a disastrous crisis but until i can get a separate hard drive/storage i shall have to take my chances.  In case of limited storage you could do the following:
[LIST]
[*]search the forums here about **"remastersys"** ... that would give you a bootable DVD that would restore your system again. DVD's are cheap these days.
[*]copy your /home by burning whatever you can to CD's and DVD's
[*]Read the link I posted, especially the bits about "saving the package selection". The resulting file is very small. And still: In case of catastrophic failure you could with one single command tell your new system to go and get all the programs back your old system had. Very useful! So you don't have to hunt down those programs manually.
[*]search these forums about **"aptoncd"**. It's a program that will burn the package cache of all the things you installed onto DVD. Advantage: Instead of downloading everything again you can reinstall all packages from that DVD. This is useful if you have a slow and/or quota-limited internet connection.
[*]always keep a live CD ready somewhere somehow ;)[/LIST]

---

