---
title: "I want to remove my second Internal hard drive"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by ReadyFreddy on 2011-02-06
I want to remove my secondary hard drive.  I used the umount (sudo umount /media/DRIVENAME) command, unmounted its, shutdown, physically removed the drive, and now every time i restart, I have to press "S" to skip the mounting of a drive thats not in the computer.

So clearly, I missed a step.  Any help would be greatly appreciated. I guess I could reinstall ubuntu, but that would defeat the purpose of learning this new (to me) world of linux.

Thanks in advance!

---

### Post by yeats on 2011-02-06
Check your /etc/fstab file to see if there is an entry for the removed drive.  If you can you paste the output of ```
cat /etc/fstab
``` here, someone may be able to help you troubleshoot.

---

### Post by ReadyFreddy on 2011-02-06
Yes there is an entry, /dev/sdb1, mount point is /media/USB_Music, type is ntfs-3g.  (it was an external drive at one point on my old windows system, until I put it in the machine)

---

### Post by Paqman on 2011-02-06
Open the file with:
```
gksu mousepad /etc/fstab
```

Comment out that line (put a # at the start), save the file and type:
```
sudo mount -a
```

If you get no errors, you're good.

---

