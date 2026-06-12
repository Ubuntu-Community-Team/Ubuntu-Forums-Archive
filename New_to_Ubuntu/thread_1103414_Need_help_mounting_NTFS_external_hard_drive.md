---
title: "Need help mounting NTFS external hard drive"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by gogogo111 on 2009-03-22
Hello everyone, I wouldn't say I'm new to Ubuntu, just I'm switching this time permanently. I don't game anymore on the PC, so I decided that Windows was pointless, and popped Ubuntu on here.

Anyways, I packed up all my photos, music, movies, etc. onto my external SEAGATE hard drive. However Ubuntu is giving me this message,  in this screenshot.


 I never removed the hard drive when I had it plugged in from so I never did a "Safely Remove Hardware" in Windows. How can I mount my drive and access my files? For the record I did try the mount command it told me to do however it just gave me information on how to use the mount command.

---

### Post by drs305 on 2009-03-22
If the command was telling you how to mount it, it probably meant the mount command had something wrong with it. A typical mount command if there was an unclean mount would be:
```
sudo mount /dev/sdXX -t ntfs -o force /media/mountpoint
```

Make sure the mount point exists and change sdXX to whatever the correct device designation is. You can check the devices with "sudo fdisk -l".

You might also want to install and use ntfs-config, which can add an entry into fstab for you. To install it:
```

sudo apt-get update
sudo apt-get install ntfs-config

```

---

### Post by gogogo111 on 2009-03-22
Ok, I was able to access it now. Thanks for the help! :p

---

### Post by kansasnoob on 2009-03-22
Install ntfsprogs either from synaptic or;

```
sudo apt-get install ntfsprogs
```

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

Use ntfs-fix as described here:

[http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/](http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/)

---

