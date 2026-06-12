---
title: "Can't Mount Windows 10 Drive"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2016-07-31
I just updated my other drive from Windows 7 to 10 and now can no longer mount it to copy files to it. I get the below error even though I just restarted from a Windows 10 session back to Ubuntu, so it shouldn't have had time to hibernate.

> Error mounting /dev/sdb1 at /media/roger/DRV1_VOL1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/roger/DRV1_VOL1"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


---

### Post by sudodus on 2016-07-31
I *think* this is the problem:

Windows has certain tricks to boot fast - semi-hibernation, and you have to disable it to make linux mount its files. The reason is that things would be messed up, if linux reads and particularly if linux writes or changes files, and after that Windows does its trick, and overwrites something assuming the hibernation was untouched.

Browse for **disable Windows fast startup** via the internet, and I think you will find useful links. (I did).

---

### Post by TheFu on 2016-07-31
I'm guessing it is this ... 

Win8+ doesn't close file systems at reboot.  It leaves them _open_ in some way unless you've taken specific action to disable that *feature*.  It is called "Fast Startup." There was a big stink about this among Linux users back when it was first introduced.  
[https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) explains.

If that isn't it, please post back.

---

### Post by HDTimeshifter on 2016-07-31
Disabling Windows Fast Startup as well as Hibernation on Shutdown didn't work, but turning off hibernation completely did. I had to run "powercfg /h off" from the command prompt to do this.

---

