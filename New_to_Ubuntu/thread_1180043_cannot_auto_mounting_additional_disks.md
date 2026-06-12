---
title: "cannot auto mounting additional disks"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by PingMonster on 2009-06-06
Hi..

I am having trouble auto mounting additional disk in ubuntu.

I HAD old ubuntu running with two additional HDDs.
They both served as samba shared storage previously.

My old ubuntu "/" was running ext3 and I just re-installed ubuntu "/" as ext4.
I can manually mount both drive if fstab has no entry for those drive but when I edit fstab for those drives it just puts out 'You are not privileged to mount this volume." error.

This is the entry I have put in fstab but the error comes up when I manually mount.

UUID=88a940ac-cbf2-480e-b911-fcb308092502   /media/500Gb ext4 defaults 0 0

I also tried with 
/dev/sdb1  /media/500Gb   ext4    defaults  0 0

Can you please help me?

---

### Post by tad1073 on 2009-06-06
you need to change permission for those drives.

right-click drive>properties>permissions

This link might be helpful:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by PingMonster on 2009-06-06
Thank you for that.

I just ran 
"sudo chown -R myname:myname /media/320Gb" but still not mounting.

I must be doing something wrong.

what would be the command line to change permission for DRIVE?

---

### Post by PingMonster on 2009-06-06
I ran
"sudo chown -R myname:myname /media/320Gb"
"sudo chmod -R 755 /media/320Gb"

It does not have any effect but now I have lost usb external drive.
I have rebooted few times but ubuntu no longer sees this drive.

---

### Post by Chops II on 2009-06-14
I think i am up to this point with this problem too. When i chowned /media to my username and permissions, and tried to mount the usb drive, it "disappeared" but in fact it was removed from my list of drives in "places" but still appears under "computer" as a different name. It seems to mount as owned by root with 000 permissions and cannot sudo chmod the permissions. Any further ideas?

---

### Post by Chops II on 2009-06-14
Hooray, i win!
Went into Applications -> System Tools -> configuration editor -> system -> storage -> default_options -> vfat and found that the umask was 777. set a more appropriate dmask and fmask and now it works.
Just letting everyone else know.

---

