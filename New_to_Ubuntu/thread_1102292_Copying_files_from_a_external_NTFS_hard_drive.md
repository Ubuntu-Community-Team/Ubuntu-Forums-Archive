---
title: "Copying files from a external NTFS hard drive"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Castor68 on 2009-03-21
Before I installed Ubuntu in my hard disk, I put all my files in a external hard drive whit a NTFS file system.

How can I copy them from it in Ubuntu?. I know there issues with the NTFS and I don't want to lose them for making a mistake.

---

### Post by prshah on 2009-03-21
> **Castor68 said:**
> I know there issues with the NTFS

There are no "issues" whatsoever with Ubuntu accessing NTFS drives; and there have been none since Ubuntu 7.10 (when out-of-box support for ntfs was added).

How are you planning to use the "external" drive in Ubuntu? Is it a USB drive? In that case, you simply plug it in and it will be recognized and loaded automatically.

For anything else, post back with more information for detailed guidance.

---

### Post by Castor68 on 2009-03-21
It's a 500 GB Seagate FreeAgent. I'll try and I tell you later.

Thanks for the help.

---

### Post by Castor68 on 2009-03-21
I pluged it and I got the next message:

$LogFile indicates unclean shutdown (0,0)
Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.
Choose one action:
Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: If you don't have Windows then you can use the 'force' option for your own responsability. For example type on the command line:
mount -t ntfs-3g /dev/sdb1/media/FreeAgent Drive -o force.
Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/FreeAgent Drive ntfs-3g force 0 0

---

### Post by leonardo_neo on 2009-03-21
> **Castor68 said:**
> I pluged it and I got the next message:

$LogFile indicates unclean shutdown (0,0)
Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.
Choose one action:
Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: If you don't have Windows then you can use the 'force' option for your own responsability. For example type on the command line:
mount -t ntfs-3g /dev/sdb1/media/FreeAgent Drive -o force.
Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/FreeAgent Drive ntfs-3g force 0 0

I usually do the first trick in such cases. 

If you have a dual boot, or windows in some other comp, then mount the external hard disk to that, and then "safely unmount/remove" the external hard disk.

Then try to mount the disk on Ubuntu, and it wont have any problem.

I know for some this trick is unpalatable as it is something dependent on Windows, but I never new about the second trick, so I used to do like that. If you are not comfortable with the second trick, then of course you can choose the first one.

---

### Post by Castor68 on 2009-03-21
I don't have a dual boot. But, I'll try to get a laptop with Vista.

If anyone knows another answer ... plese, tell me !!

---

### Post by brian4120 on 2009-03-21
I have done option 2 several times on my own external drive without any problems. But I agree, if you are being very cautious about mounting your drive, go with option 1.

---

### Post by InfectedWithDrew on 2009-03-21
I highly recommend that you safely unmount it in Windows.

----------------
Now playing: [Red - Hide](http://www.foxytunes.com/artist/red/track/hide)

---

