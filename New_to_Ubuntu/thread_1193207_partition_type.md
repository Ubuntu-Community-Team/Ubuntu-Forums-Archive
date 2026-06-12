---
title: "partition type"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by amir aljaberi on 2009-06-21
hi 
i have some question::P
1.which is better type of partition to instal ubuntu on it? is it fat32 or ntfs ? 
2.will ubuntu cd  format the partition to ext3/ext4? 
3. can i read/write ext3/ext4 from widows?

thx:D

---

### Post by AgentZ86 on 2009-06-21
> **amir aljaberi said:**
> hi 
i have some question::P
1.which is better type of partition to instal ubuntu on it? is it fat32 or ntfs ? 
2.will ubuntu cd  format the partition to ext3/ext4? 
3. can i read/write ext3/ext4 from widows?

thx:D

I would think the best is to install Ubuntu on ext3/ext4, but I'm not sure windows can see it so you would want to create a fat 32 or ntfs file storage partition so that windows can see at least that partition.

Thats about all I know.

---

### Post by amir aljaberi on 2009-06-21
thx for ur help 
can ubuntu read/write ntfs?

---

### Post by Scarlath on 2009-06-21
I would personally recommend installing on an ext3 partition. There are software for Windows that allows it to mount ext3 partitions also. Sure you can find them on google :)

---

### Post by amir aljaberi on 2009-06-21
> **Scarlath said:**
> I would personally recommend installing on an ext3 partition. There are software for Windows that allows it to mount ext3 partitions also. Sure you can find them on google :)
so ext3/ext4 is better for ubuntu.
another question, can ubuntu read/write ntfs

thx

---

### Post by Hreinsi on 2009-06-21
yes it can. Im doing it:D

---

### Post by AgentZ86 on 2009-06-21
> **amir aljaberi said:**
> thx for ur help 
can ubuntu read/write ntfs?

Yes

---

### Post by amir aljaberi on 2009-06-21
> **Hreinsi said:**
> yes it can. Im doing it:D

Thx dear :D

---

### Post by amir aljaberi on 2009-06-21
thx all for ur help

---

### Post by amir aljaberi on 2009-06-21
hi again :D
I M waondering how big the swap partition if my ram is 3 gb?
and i have 4 partition 1 for xp, 2 for ubuntu and 3,4 for storage,so do i need to make mount point to all partitions ? 

thx

---

### Post by LewRockwell on 2009-06-21
swap = 1x maximum ram

---

### Post by amir aljaberi on 2009-06-21
> **LewRockwell said:**
> swap = 1x maximum ram

so u mean 3giga swap and what about other partitions ?

thx

---

### Post by DeanoCYM on 2009-06-21
This maybe helpful for reading/writing to Ext2/3 partitions in windows. Never tried it myself though.. Not sure how old it is either.

[ http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html ]( http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html )

---

### Post by amir aljaberi on 2009-06-21
> **DeanoCYM said:**
> This maybe helpful for reading/writing to Ext2/3 partitions in windows. Never tried it myself though.. Not sure how old it is either.

[ http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html ]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html")

thx for ur help  
 i have 4 partition 1 for xp, 2 for ubuntu and 3,4 for storage,so do i need to make mount point to all partitions ?
 plz what does /boot partition mean? and do i need to make it?

---

### Post by LewRockwell on 2009-06-21
> **amir aljaberi said:**
> thx for ur help  
 i have 4 partition 1 for xp, 2 for ubuntu and 3,4 for storage,so do i need to make mount point to all partitions ?
 plz what does /boot partition mean? and do i need to make it?

you have one primary partition for XP

you have one primary partition for Ubuntu

you need one primary partition for swap

then you need to create one extended partition where you can do whatever you want inside of it.

I would recommend keeping Ubuntu all on one partition and if you want to move stuff to storage partitions inside your extended partition then you could.

---

### Post by -kg- on 2009-06-21
> **LewRockwell said:**
> you have one primary partition for XP

you have one primary partition for Ubuntu

you need one primary partition for swap

then you need to create one extended partition where you can do whatever you want inside of it.

I would recommend keeping Ubuntu all on one partition and if you want to move stuff to storage partitions inside your extended partition then you could.

If you don't have Ubuntu installed yet, you can alternatively put all the partitions except for XP inside an Extended partition, making them Logical partitions.  The only Primary partition you really need is for XP.  Ubuntu will run entirely from a Logical partition...root, swap, and all.  Windows will also access any Logical partition that it's able to read; ext2/3 included (with the proper driver), but you can include an ntfs/fat partition as one (or more) of the extra partitions and both Windows and Ubuntu will be able to access them.

The reason I make this comment is on the off-chance that you might want to install another distro of Windows.  There is a 4-Primary partition limit on physical hard drives, and if you use them all up unnecessarily, you will have to play shuffleboard with your partitions if you want to do that.

Read the Wiki linked to in my signature block and then make your choices.

<edit> Really, you can install using the Live CD and the installer will create your partition scheme automatically.  You can also use the manual partitioning method and create any size and types of partitions you wish, then mark them with the appropriate mount point (whatever you want, as long as you *at least* have a "/" (root) and a swap partition).  There is quite a selection of mount points, and although I've never used that method, it would be logical that you should be able to create your own (such as /storage, if it doesn't already exist in the list).

---

### Post by amir aljaberi on 2009-06-22
thx all for ur help
100gb for windows(ntfs)
35 gb ext4 for ubuntu /
5 gb swap
100gb ntfs shared
60 gb ntfs shared 

i hope this will be ok

---

### Post by -kg- on 2009-06-22
That will certainly work.  You have the required Windows, Ubuntu root, and swap partitions...whatever you want to do with the rest of the drive is optional and totally up to you.

---

### Post by amir aljaberi on 2009-06-22
> **-kg- said:**
> That will certainly work.  You have the required Windows, Ubuntu root, and swap partitions...whatever you want to do with the rest of the drive is optional and totally up to you.

thx man for ur help, appreciate it.:D

thax all :P

---

