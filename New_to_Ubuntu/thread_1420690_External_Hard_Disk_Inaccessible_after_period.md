---
title: "External Hard Disk Inaccessible after period"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by gallifrey on 2010-03-03
Hello all, 
         I am running Karmic on my laptop, and I have three 1.5 TB external hard drives which I swap between frequently. My problem is that if I leave the drives in, and do not access them for a period of time, they become inaccessible, i.e. I will click on the icon on the desktop or in Places, and it will tell me there is no device mounted, even though I was using it fine just an hour before. 

i have a feeling that it is because the USB drives spin down after a period, and Ubuntu detects them as being 'disconnected'. Would it help if I added individual entries for each in fstab?? Or do I need to adjust some settings elsewhere?

Any help and advice would be most appreciated!

---

### Post by Jefferythewind on 2010-03-03
You could always re-mount the hard drives.  This could be a little annoying though, although that is pretty intense to have 3 hard drives connected to your laptop at all times... but that is your choice.

```
mkdir /mnt/extHD1
mount /dev/sda1 /mnt/extHD1
```

where /dev/sda1 is the location of your external HDD, you can find this location in GParted or by typing in:

```
sudo fdisk -l
```

hope this helps.  I use an external HDD all the time and I haven't had this problem.  It seems to stay mounted for a long time, and when I access after a period of inactivity, i can hear the HDD spin up again.

---

