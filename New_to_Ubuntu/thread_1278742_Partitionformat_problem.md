---
title: "Partition/format problem"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Kackar on 2009-09-29
hi all.

I've installed ubuntu 9 on my new 160gb hdd together with my XP. Created 40gb+40gb partitions to install both system. Once I've got the system up and working, I decided to partition and format the remaining 80gb as ext3 for extra space.

I ran the ubuntu setup disk and created the remaining partition but did not format it, hoping that I could on gpart-partition editor. I repartitioned the 80gb on gpart (as primary-had no other choice) and assigned ext3. I can now see the new partition under My Computer but can not write to it. I get an error message that I don't have permission to create it in the destination. Not sure if gpart formatted this partition because it only took maybe 1-2 minutes to format it.

I'd appreciate if someone could help me with this issues pls.

thanks.

---

### Post by lidex on 2009-09-30
Not sure why it won't automount but have a look here:
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by QIII on 2009-09-30
Hang on.

You are saying you attempt to save to the file using "My Computer" in Windows to an ext3 partition?

---

### Post by oldfred on 2009-09-30
You need to make a directory, mount the partition to the directory, give rights to the directory to you- chown and if you want to permanently mount every time you reboot, edit your fstab, and finally copy files.

More Info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Change New_directory to whatever you want to call your newdirectory

mkdir new_directory
sudo mount -t ext3 /dev/sdxy /mnt/new_directory
    or /home/yourname/new_directory or where ever you want to see the new data in your file structure
sudo chown -R yourusername:yourgroupname /mnt/new_directory/

Once you get it working then we can work on fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by oldfred on 2009-09-30
Another correction the make directory must be the full path or else it will make it in the current directory you are in.

mkdir new_directory
actually makes ~/new_directory where ~ is /home/username

This is probably the better place to put a data directory?

so if you want to create the new directory in mnt

mkdir /mnt/new_directory  
If you try this you will need sudo since it is in the root area.

mkdir /data
sudo mount -t ext3 /dev/sd[COLOR=Red]xy[/COLOR] ~/data [COLOR=Red]where sdxy is your drive & partition[/COLOR]
sudo chown -R yourusername:yourgroupname ~/data

---

