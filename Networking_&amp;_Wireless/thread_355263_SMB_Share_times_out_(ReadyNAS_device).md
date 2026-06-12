---
title: "SMB Share times out (ReadyNAS device)"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by thevinn on 2007-02-07
I have a ReadyNAS device that is configured properly and working in Windows. When I mount it in Ubuntu, it works until I start reading from files. Then, any command or window associated with the volume hangs or times out. I get warnings in logs about smbfs timeouts.

My fstab entry looks like this:

//192.168.1.200/Data /media/nas  smbfs  _netdev,password="",noauto,nouser,dmask=770,fmask=770,gid=plugdev   0      0

I've tried using cifs to mount it, and it doesn't hang. However, the cifs option ignores my settings for uid and gid. I get an unknown uid as the owner of everything that gets mounted, and "nogroup" for the gid. Nothing I do in fstab affects the ownership of files mounted via cifs.

Any idea why smbfs is hanging up?

Do I need to provide any additional information?

---

### Post by supersigmoid on 2007-06-20
I, too, am having the same issue, only with a Buffalo LinkStation Live.  Ownership and permission settings work great with smbfs, but it stalls as described.  I would really like to get cifs working with the appropriate file ownerships and permissions.  Has anyone had any luck with this since the problem was first posted?

---

### Post by supersigmoid on 2007-07-07
I've found the solution.  I couldn't get smbfs to work without freezing, but I found a fix for CIFS ignoring ownership settings.

The solution can be found here: [http://ubuntuforums.org/archive/index.php/t-188027.html]("http://ubuntuforums.org/archive/index.php/t-188027.html").  When Linux extensions for CIFS are enabled, your uid,gid,file_mask and disk_mask mount options are ignored.

To disable Linux extensions and thus allow those options to work, you need to run:
```
/sbin/modprobe cifs
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
```
each time before you mount your NAS.  To automate this on each boot I've placed these lines in the [FONT="Courier New"]pre_mountall[/FONT] function in [FONT="Courier New"]/lib/init/mount-function.sh[/FONT]--I don't know if that's the appropriate place for it, but it does work.

Enjoy.

---

