---
title: "Installing 10.10 to external USB HD?"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by BillHookMan on 2011-03-06
Hello,

I am trying to install Ubuntu to my external 320 GB USB HD. Tried installing it like normal Ubuntu install, from CD and pointed out the external source of my HD and started installation process. Everything went right, unless in the very end of installation it started to nag something about bootloader etc.

I am not very familiar with these kind of things, but should there be done somekind of "/" directories in advanced partition menu before proceeding installation? :confused: If so, could someone instruct me what kind of partitions there should be set up that Ubuntu would install painlessly to the very end?

Cheers and thanks in andvance! :)

---

### Post by maqtanim on 2011-03-06
Welcome to UF. :)

Which option did you choose for the installation? Did you choose the  Manual Partition? If you did so then, there should be a mount point in  the manual partition. Select the mount point to "/" from the drop down  list. The rest should go fine.

---

### Post by Dutch70 on 2011-03-06
This should answer your questions. 

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by BillHookMan on 2011-03-06
> **maqtanim said:**
> Welcome to UF. :)

Which option did you choose for the installation? Did you choose the  Manual Partition? If you did so then, there should be a mount point in  the manual partition. Select the mount point to "/" from the drop down  list. The rest should go fine.

Hello, and thank you for the welcome.

I tried the "easiest" installation procedure, wipe out entire disk and install ubuntu. In very end it started to nag something about bootloader and suggested that it should be put up, and when I picked option from drop down box (it was something like dev/blablbab) installation stated that encountered unknown error and informed that installation procedure will not continue. There was also option that "dont install boot loader" and it said that then boot loader should be installed manually, but I dont know how to do it.

Gonna try now that / thing in intallation and hope it then makes necessary space to installation. :)

---

### Post by Dutch70 on 2011-03-06
It is probably a good idea to unplug your internal hdd before installing. Although I've never installed to an external hdd.

---

### Post by beew on 2011-03-06
If you choose manually creation partitions (instead of erasing whole disk) then when you are shown the partition table there will be a box in the bottom which asks you where to install the bootloader. Pick from the drop down menu your external drive (usually sdc, sda would be the internal drive, sdb would be the live usb from which you are installing, or it would be sdb in case you install from a live CD, but check first, you can  figure out from the partition manager graphic at this point)

To manually create the partitions.** Choose the correct drive** and then create a partition of about 15 - 20G  from the unallocated space (this is where the system and all your programs will eventually be installed),  choose   "/" (without the quotes) from the drop down menu to be the mount point and  format it in ext4;  then create another ext4 partition from the remaining unallocated space to be your /home partition (so the mount point would be "/home"), this is where all your data and settings will be stored, you can make it any size you want, depending on your need. Finally add a swap partition in the end (file type is "Linux swap"), they say it should be 1.5 x ram but in my installation I just made it 2 Gs (I use it on different computers as a portable so i don't know how much ram they have anyway)

---

### Post by BillHookMan on 2011-03-06
This is how it nags:

[[IMG]http://i2.aijaa.com/t/00065/7630253.t.jpg[/IMG]]("http://aijaa.com/v.php?i=000657630253.jpg")
I am trying to install it to the 250 gb external. 

[[IMG]http://i4.aijaa.com/t/00579/7630260.t.jpg[/IMG]]("http://aijaa.com/v.php?i=005797630260.jpg")
Then the nagging starts.

[[IMG]http://i9.aijaa.com/t/00864/7630261.t.jpg[/IMG]]("http://aijaa.com/v.php?i=008647630261.jpg")

[[IMG]http://i2.aijaa.com/t/00986/7630262.t.jpg[/IMG]]("http://aijaa.com/v.php?i=009867630262.jpg")

---

### Post by BillHookMan on 2011-03-06
> **beew said:**
> If you choose manually creation partitions (instead of erasing whole disk) then when you are shown the partition table there will be a box in the bottom which asks you where to install the bootloader. Pick from the drop down menu your external drive (usually sdc, sda would be the internal drive, sdb would be the live usb from which you are installing, or it would be sdb in case you install from a live CD, but check first, you can  figure out from the partition manager graphic at this point)

To manually create the partitions.** Choose the correct drive** and then create a partition of about 15 - 20G  from the unallocated space (this is where the system and all your programs will eventually be installed),  choose   "/" (without the quotes) from the drop down menu to be the mount point and  format it in ext4;  then create another ext4 partition from the remaining unallocated space to be your /home partition (so the mount point would be "/home"), this is where all your data and settings will be stored, you can make it any size you want, depending on your need. Finally add a swap partition in the end (file type is "Linux swap"), they say it should be 1.5 x ram but in my installation I just made it 2 Gs (I use it on different computers as a portable so i don't know how much ram they have anyway)
I did exactly as you wrote, but have the same prob as shown in pics I posted. :(

---

