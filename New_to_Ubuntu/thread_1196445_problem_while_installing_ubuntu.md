---
title: "problem while installing ubuntu"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by amir aljaberi on 2009-06-24
hi 
my partitions before installing was like that:
c:/windows
d:/storage
e:/storage
m:/storage 

and after installation in first time i made partion like that:

c:/windows i didn't any make change to it
d:/ ubuntu mount point : /
swap area 
e: i didnt make any change
m:didnt make any change

so after finish installing and start ubuntu it gave that u cannot access e and m partiotion and c partition didnt appear.

so i tried to install ubuntu again and while making partition i made like that :
for c partition: ntfs i made mont point like that /mnt/wind_c
for partition d: ext4 mount point /
for parttion e : ntfs mount point /mnt/shared
for partition m: ntfs mount point /mnt/shared 

after that it gave me that u cannot make the same mount point for partitions( e and m)

so what is the problem ? how can i share between windows and ubuntu ?
and if i make sharing between 2 os( without reformat) , will that destroy my data in partitons?

 plz help me:(

---

### Post by 3rdalbum on 2009-06-25
What did you do to try and access those partitions? I'm having trouble following your post. And I'm not sure why you reinstalled Ubuntu.

---

### Post by amir aljaberi on 2009-06-25
i couldnt access partions through ubuntu .
i tried to open partition and it gave me write the password 
so i reinstall to make mount point for those partitions becuz i didnt make mount point for e and m partitons in the first time

thx

---

### Post by ~sHyLoCk~ on 2009-06-25
Ok if I understand correctly, your main problem is that you can not access your "ntfs" drives (viz. c,e and m)? 
If that's the issue then no need to reinstall ubuntu and your data is safe!
Go to synaptic and install ntfs-3g.
Open /etc/fstab and add your drives. 

Do 
sudo mkdir /windows/c
sudo mkdir /windows/e
sudo mkdir /windows/m
Check fdisk -l to find out your drive's location. Then add fstab entries as follows:

/dev/sda5   /windows/c        ntfs-3g  defaults,rw 0 0

Similarly add for drives e and m. Also make sure to put the proper device number here I used sda5 as an example substitute 5 for whatever values appear!

Hope this helps.

---

### Post by amir aljaberi on 2009-06-25
hi there 
so i dnot need to make mount point for ntfs partition?

---

### Post by kansasnoob on 2009-06-25
> **amir aljaberi said:**
> hi 
my partitions before installing was like that:
c:/windows
d:/storage
e:/storage
m:/storage 

and after installation in first time i made partion like that:

c:/windows i didn't any make change to it
d:/ ubuntu mount point : /
swap area 
e: i didnt make any change
m:didnt make any change

so after finish installing and start ubuntu it gave that u cannot access e and m partiotion and c partition didnt appear.

so i tried to install ubuntu again and while making partition i made like that :
for c partition: ntfs i made mont point like that /mnt/wind_c
for partition d: ext4 mount point /
for parttion e : ntfs mount point /mnt/shared
for partition m: ntfs mount point /mnt/shared 

after that it gave me that u cannot make the same mount point for partitions( e and m)

so what is the problem ? how can i share between windows and ubuntu ?
and if i make sharing between 2 os( without reformat) , will that destroy my data in partitons?

 plz help me:(

You have much to learn:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

You didn't mention how many drives were involved, but if all four of those partitions were on one drive you've already written over and destroyed any existing data since there is a four primary partition limit on all drives!

Also you need to learn Linux partition numbering:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html)

---

### Post by ~sHyLoCk~ on 2009-06-25
> **amir aljaberi said:**
> hi there 
so i dnot need to make mount point for ntfs partition?

Making the mount points don't work sometimes, but I pray to God that you didn't select the format option!

---

### Post by amir aljaberi on 2009-06-25
> **~sHyLoCk~ said:**
> Making the mount points don't work sometimes, but I pray to God that you didn't select the format option!

looool :D

so i should use ur steps  to share partitions between windows and ubuntu 

thx

---

### Post by amir aljaberi on 2009-06-25
> **kansasnoob said:**
> You have much to learn:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

You didn't mention how many drives were involved, but if all four of those partitions were on one drive you've already written over and destroyed any existing data since there is a four primary partition limit on all drives!

Also you need to learn Linux partition numbering:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html)

ooooh too much information:D it takes 2 weeks to read all info:popcorn:
all i need is to share 2 partitions between ubuntu and windows :D
and i was wondering if it essential to make mount point for all partitions

---

### Post by ~sHyLoCk~ on 2009-06-25
> **amir aljaberi said:**
> looool :D

so i should use ur steps  to share partitions between windows and ubuntu 

thx

If that doesn't work try [this]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Manually_Mount_and_Unmount_a_device").

---

### Post by amir aljaberi on 2009-06-25
hi 
i enabled and installed ntfs-config, now i can read/write ntfs partition :D thx
BUT plz why ubuntu slow in browsing application and also its slow to response ?

---

### Post by ~sHyLoCk~ on 2009-06-25
> **amir aljaberi said:**
> hi 
i enabled and installed ntfs-config, now i can read/write ntfs partition :D thx
BUT plz why ubuntu slow in browsing application and also its slow to response ?

What's your system spec?

---

### Post by amir aljaberi on 2009-06-25
processor 1.6 C7-M VIA L2 128
GRAPHICS [FONT=Arial]VIA        Chrome9 HC IGP
320 HDD
3 GB RAM 

DO I NEED TO INSTALL DRIVER FOR GRAPHICS ?
[/FONT]

---

