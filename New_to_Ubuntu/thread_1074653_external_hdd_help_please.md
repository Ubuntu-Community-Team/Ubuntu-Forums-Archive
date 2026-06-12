---
title: "external hdd help please"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by coops351 on 2009-02-19
im new to linux and i trying out different distributions and im starting to like kubuntu 8.10 alot, so im happy staying with this OS for a while.

the problem im having is when i connect my external hard drive to my computer the it says i have to force and open.

can anyone show me how you do that, and be able to mount it and get the data of it so i can put it on my system :)

thanks

---

### Post by drs305 on 2009-02-19
It sounds like you have an NTFS device with an unclean shutdown. You can mount it with:
```

sudo mount -t ntfs-3g /dev/disk-device /media/ntfs -o force

```

Make sure /media/ntfs exists (or change to an existing mount point.
Replace "disk-device" with the device designation (sdb1, sdd2, etc).

If that doesn't work, please post the results of:
```
sudo fdisk -l
```

---

### Post by Therion on 2009-02-19
Are you getting the error message that tells you to use **-force -o** option or something similar?  
If so, open a Terminal: Applications-> Accessories-> Terminal and type in the command the error is showing you with sudo in front of it.

If that doesn't work, keep your Terminal open and copy and paste the following into it:```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by coops351 on 2009-02-19
its saying that i need to run dpkg

---

### Post by coops351 on 2009-02-19
i also need to download the OS again cus the disc is corrupt and im having loads of errors and bugs on the system so i'll reply in couple of hours and tell you whats happening.

cheers fellas for the help

---

