---
title: "moving /home to its own partition"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by steve70 on 2009-03-22
I need some help...

This weekend, I decided to move /home to its own partition. I don't run into any problems until its time to edit the /etc/fstab file. After adding the specific line to the end of the file, multiple errors return on the terminal. 

I tried various posts (including WordPress and Psychocats) to no avail. If there's someone that can help, it'll greatly be appreciated.

---

### Post by llamabr on 2009-03-22
post your fstab file.

---

### Post by jimv on 2009-03-22
what are the errors?

---

### Post by steve70 on 2009-03-22
After reinstalling ubuntu all day trying to get this right, I get two types of errors. It's either... 

1.GTK error stating that it can't display the /etc/fstab file..or

2.I get access to the /etc/fstab file, but after I attach the line for the new /home destination, I get an I/O error after I save the file and close gedit.

---

### Post by steve70 on 2009-03-22
Through multiple installs of 8.10 Here's what I did to get things going
(New partition after splitting HD with gparted= sda3)


1) Created a partition = sudo mkdir /mnt/newhome

2) Mounted and checked new partition

3) Copied /home to partition= used "sudo find . -depth -print0 | sudo cpio &#8211;null &#8211;sparse -pvd" AND "sudo cp -a -v -u /home/* /mnt/newhome/" (on separate occasions, of course!)

4) Renamed current home= sudo mv /home /old_home 

5) Made a new home folder= sudo mkdir /home 

6) Unmounted the partition= sudo umount /mnt/newhome 

7) Mounted the partition in new home folder= sudo mount /dev/sda4 /home 

8) Edited fstab, sudo gedit /etc/fstab, and added line = /dev/sda3 /home ext3 nodev,nosuid 0 2 to the end of the file. 

By the time I save the file and close gedit, this error occurs...

** (gedit:25118): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.2LVIRU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory

---

### Post by steve70 on 2009-03-22
> **llamabr said:**
> post your fstab file.

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0 /dev/sda3 /home ext3 nodev,nosuid 0 2

---

### Post by hyper_ch on 2009-03-23
[http://www.pyschocats.net](http://www.pyschocats.net) --> Aisyu has written a nice guide on howto move one's /home

---

### Post by presence1960 on 2009-03-23
> **steve70 said:**
> After reinstalling ubuntu all day trying to get this right, I get two types of errors. It's either... 

1.GTK error stating that it can't display the /etc/fstab file..or

2.I get access to the /etc/fstab file, but after I attach the line for the new /home destination, I get an I/O error after I save the file and close gedit.

Since you have been reinstalling all day what is one more time? Back up your current data on home. Reinstall using Live CD. **Create a separate home partition with the partitioner. Make sure you set the mount point to /home.** Then you won't have to do any maneuvering after the install, it will be done for you.

---

### Post by steve70 on 2009-03-31
presence1960- Thanks for the info. Reinstalled using manual settings, everything's good!

---

### Post by philinux on 2009-03-31
> **steve70 said:**
> presence1960- Thanks for the info. Reinstalled using manual settings, everything's good!

Well now reinstalling will be a doddle from now on. ):P

This is the best way to install ubuntu or any os for that matter.

---

