---
title: "New Hard Drive- cant put files on"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by tokies on 2009-04-30
I am using Ubuntu 9.04. I have a new 1TB hard drive formated ext4. When I try and use it it does not let me copy anything. I believe i need to give myself permission to copy on to the hard drive?

I am a total newbie to all of this and have rarely used terminal how to I fix this.

??
I have name the drive "Hi"

If you could dumb it down as much as you can I will be thankful

---

### Post by Dougie187 on 2009-04-30
Do you get any sort of error messages when you try to access the drive?

---

### Post by y_garti on 2009-04-30
is it your primary hd where you install ubuntu 
 or additional drive that you add after the installtion

---

### Post by unutbu on 2009-04-30
This is a nice HowTo on installing a new hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Pedro Villarroel on 2009-04-30
The same happend to me 2 times after i formated my 2 externals disks from fat32 to ext4, i logged as ROOT and gave me permitions to use the external hdd i i was able to use them.

Im new to linux just 2 days ago, so i hope i dint say something stupid that you already know, :P

i also sorry for my english as im just learning.

root is disable in ubuntu, here is the forums i can look for the way to able the root acc, i dont remember the instructios at the moment ( im a noob ;) )

geatings from spain.
Peace.

---

### Post by Pedro Villarroel on 2009-04-30
Ok, so to be a little more clear.

**1) activate root acc**
You can enable root as followed:

sudo xterm
passwd

Supply root password.

You can now log in as root or issue
the su command to change to root.

**2: Enter as ROOT and change the ownership**
for some reason the owner becomes root after you format a disk

**3: well, put some files to see if worked**
step 3 is just becose 2 steps was to short :P

peace

---

### Post by tokies on 2009-04-30
thanks for your help!!! I am going to try it out. error is i do not have access to think drive i believe and i think this is what i was looking for

---

### Post by markharding557 on 2009-04-30
you can type sudo -i to open a root console.

---

### Post by tokies on 2009-05-01
su command to change to root. ?

sorry stupid question but I have used the xterm thing to log in and I tried to change permission but it said unknown permissions so then I need to use the su command to change to root but what is the su command to change to root or am i just typing in su?

Do I reformat the hard drive again?

I check the installing new drive out I did not see anything about permissions change listed except for other users.

I am sorry but I Am REALLY new to all of this as stated before. Sorry. ...

---

### Post by halitech on 2009-05-01
to expand on what Pedro posted

Open a terminal and first post the results of
```
sudo fdisk -l
```

look for the drive you want to write to (should be /dev/sdXX)

then run these commands:
```
sudo mount /dev/sdXX /location/of/mount/point
```
```
sudo chown -R username:username /location/of/mount/point
```
```
sudo chmod -R 755 /location/of/mount/point
```

change /location/of/mount/point to where you have the drive mounted and username to your username

---

### Post by pastalavista on 2009-05-01
In terminal (or alt-f2 command box) type ```
gksu nautilus
```

You will be root now, so be careful. Navigate to file system /media and right-click on the drive you just installed and then open the 'Permissions' tab. Then you can change the owner and permissions to read and write.

---

### Post by tokies on 2009-05-02
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          78      626503+   b  W95 FAT32
/dev/sda2              79       38913   311942137+   5  Extended
/dev/sda5              79       37335   299266821   83  Linux
/dev/sda6           37336       38913    12675253+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00005c1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      118651   953064126   83  Linux
/dev/sdb2          118652      121601    23695875    5  Extended
/dev/sdb5          118652      121601    23695843+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e538a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90fec4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121602   976761496+   b  W95 FAT32

---

### Post by tokies on 2009-05-03
thanks!!! did it with your help the nat thing was the easy, thank you 1000 times

---

