---
title: "How to format my pendrive"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-03-24
hi

I want to format my pen drive . how should i do that in my ubuntu system
please help

---

### Post by KCG102282 on 2009-03-24
Install Gparted if you havent done so ```
sudo apt-get gparted
```. Then plug in the pen drive open gparted and format it how you like.

---

### Post by albandy on 2009-03-24
you can use gparted in System --> Administration --> Partition Editor
right click on the pendrive partition and then select format

also by command line you can format your pendrive this way:

sudo mkfs.vfat -F32 /dev/sd(x)

where x in sd(x) is the device name, for example if your usb device is sdc then
sudo mkfs.vfat -F 32 /dev/sdc

---

### Post by luckydeveloper on 2009-03-24
my pendrive is giving me hell.. there is one folder which i want to delete it.. when i right click on it and click delete.. it is saying it cannot delete the file.. i've changed the permissions also .. but still it is not deleting.. 

and when i unmount that pen drive.. it asks me whether it should empty the trash.. i gave it yes.. 

but still wheni plugin my pen drive back .. the folder is still there.
i want to fully delete all the contents from my pendrive..please help

---

### Post by luckydeveloper on 2009-03-24
> **albandy said:**
> you can use gparted in System --> Administration --> Partition Editor
right click on the pendrive partition and then select format

also by command line you can format your pendrive this way:

sudo mkfs.vfat -F32 /dev/sd(x)

where x in sd(x) is the device name, for example if your usb device is sdc then
sudo mkfs.vfat -F 32 /dev/sdc

will the above command format the pendrive in FAT32 format?

---

### Post by albandy on 2009-03-24
> **luckydeveloper said:**
> will the above command format the pendrive in FAT32 format?

Yes, I asumed he want to format it in Fat32 (for compatibility between operating systems)

---

