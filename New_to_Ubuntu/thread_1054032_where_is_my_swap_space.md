---
title: "where is my swap space?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by merlin666 on 2009-01-29
I installed Intrepide from Live CD and used gparted for a dual boot system. After the sda1 for XP I added a 15Gb ext3 partition and then a 2.5 Gb Swap partition. When booting I get a range of messages referring to disk caching, which leads me to suspect something wrong with Swap space. When I check I get the following:

$ top

top - 08:10:25 up 27 min,  2 users,  load average: 0.18, 0.17, 0.11
Tasks: 117 total,   1 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.7%sy,  0.0%ni, 96.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1282208k total,   697768k used,   584440k free,    17128k buffers
Swap:        0k total,        0k used,        0k free,   268180k cached

What can I do so that Ubuntu finds the allocated 2.5 Gb?

---

### Post by taurus on 2009-01-29
Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by sisco311 on 2009-01-29
Please post the output of:
```
free -m
sudo blkid
cat /etc/fstab
```

---

### Post by Binny88 on 2009-01-29
Did u perform swapon.(using that partiton as swap). If u havent done it then
run  gparted, rightclick the swap partiton & press th swapon icon.
Be careful though, the swapon might be reversed at next restart &  you have to manually swap it on again.

Good Luck

---

### Post by merlin666 on 2009-01-30
> **Binny88 said:**
> Did u perform swapon.(using that partiton as swap). If u havent done it then
run  gparted, rightclick the swap partiton & press th swapon icon.
Be careful though, the swapon might be reversed at next restart &  you have to manually swap it on again.

Good Luck
Thanks, that does the trick. I must have turned it off when resizing partitions. How can I set it to be enabled on startup and stop all the messages during the boot process? RElated commands from above are as follows:

$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4d64506

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7376    59247688+   7  HPFS/NTFS
/dev/sda2            9410        9729     2570400    f  W95 Ext'd (LBA)
/dev/sda3            7377        9409    16330072+  83  Linux
/dev/sda5            9410        9729     2570368+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2496458e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52d56e0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161    7  HPFS/NTFS


$ sudo blkid
/dev/sda1: UUID="D4F4901C188B62C0" LABEL="Applications" TYPE="ntfs" 
/dev/sda3: UUID="01858de3-92ef-49c9-bd3e-0d9cab8c8fc8" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="764b4e68-f4c1-4c7b-bc0e-52cc2c752ba0" 
/dev/sdb1: UUID="B0EC9783EC974290" LABEL="BigDrive" TYPE="ntfs" 
/dev/sdc1: UUID="B0E45122E450EC5A" LABEL="Portable" TYPE="ntfs" 

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=01858de3-92ef-49c9-bd3e-0d9cab8c8fc8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=506c3b10-c687-4605-ac8d-6a623b17e6ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sisco311 on 2009-01-30
Edit the fstab and replace the UUID of the swap partition.
```
gksu gedit /etc/fstab
```
replace
> # /dev/sda5
UUID=*506c3b10-c687-4605-ac8d-6a623b17e6ac* none swap sw 0 0with
> # /dev/sda5
UUID=**764b4e68-f4c1-4c7b-bc0e-52cc2c752ba0** none swap sw 0 0save the file and mount the partitions:
```
sudo mount -a
```

---

### Post by caljohnsmith on 2009-01-30
> **sisco311 said:**
> Edit the fstab and replace the UUID of the swap partition.
```
gksu gedit /etc/fstab
```
replace
```
# /dev/sda5
UUID=506c3b10-c687-4605-ac8d-6a623b17e6ac none swap sw 0 0 
```
with
```
# /dev/sda5
UUID=764b4e68-f4c1-4c7b-bc0e-52cc2c752ba0 none swap sw 0 0 
```
save the file and mount the partitions:
```
sudo mount -a
```
I just wanted to mention that if you do it this way, most likely you will also need to update your /etc/initramfs-tools/conf.d/resume file and then regenerate all the /boot/initrd images so they will be updated with the new swap UUID. How about also posting:
```
cat /etc/initramfs-tools/conf.d/resume
```
If that shows the same UUID as you have in your fstab, i.e. "506c3b10-c687-4605-ac8d-6a623b17e6ac", then I think it is much easier to simply change your swap UUID back to what it originally was:
```
sudo mkswap -U 506c3b10-c687-4605-ac8d-6a623b17e6ac /dev/sda5
```
Otherwise, you will have to change your fstab, resume file, and also regenerate all your initrd images in /boot in order to completely update your system with the new swap partition UUID. There's nothing wrong with that if that's what you want to do, but I prefer to just run the single command to change the swap partition UUID back to what it originally was. Good luck and let us know how it goes. :)

---

### Post by merlin666 on 2009-02-23
> **caljohnsmith said:**
> 
If that shows the same UUID as you have in your fstab, i.e. "506c3b10-c687-4605-ac8d-6a623b17e6ac", then I think it is much easier to simply change your swap UUID back to what it originally was:
```
sudo mkswap -U 506c3b10-c687-4605-ac8d-6a623b17e6ac /dev/sda5
```
Otherwise, you will have to change your fstab, resume file, and also regenerate all your initrd images in /boot in order to completely update your system with the new swap partition UUID. There's nothing wrong with that if that's what you want to do, but I prefer to just run the single command to change the swap partition UUID back to what it originally was. Good luck and let us know how it goes. :)
Thank you.

I was suspicious that something was wrong when I booted again and got various disk messages. Indeed, the swap space is there but not used:

top - 17:48:16 up 38 min,  2 users,  load average: 0.30, 0.39, 0.48
Tasks: 127 total,   3 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.1%us,  2.6%sy,  0.0%ni, 76.9%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1282208k total,  1232812k used,    49396k free,   115840k buffers
Swap:  2570360k total,        0k used,  2570360k free,   443592k cached

When I tried:
```
sudo mkswap -U 506c3b10-c687-4605-ac8d-6a623b17e6ac /dev/sda5
```
I got:
/dev/sda5: Device or resource busy

So what to do now?

---

### Post by caljohnsmith on 2009-02-23
Merlin666, did you all ready change your fstab file? I hope you left it with the original swap UUID. How about first posting:
```
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
free
```
And we can work from there.

---

### Post by merlin666 on 2009-02-23
I have changed the fstab. Now I am not sure if it works or not:

~$ sudo blkid -c /dev/null
/dev/sda1: UUID="D4F4901C188B62C0" LABEL="Applications" TYPE="ntfs" 
/dev/sda3: UUID="01858de3-92ef-49c9-bd3e-0d9cab8c8fc8" TYPE="ext3" 
/dev/sda5: UUID="764b4e68-f4c1-4c7b-bc0e-52cc2c752ba0" TYPE="swap" 
/dev/sdb1: UUID="B0E45122E450EC5A" LABEL="Portable" TYPE="ntfs" 
/dev/sdc1: UUID="B0EC9783EC974290" LABEL="BigDrive" TYPE="ntfs" 
rolf@cagney2:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=506c3b10-c687-4605-ac8d-6a623b17e6ac

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=01858de3-92ef-49c9-bd3e-0d9cab8c8fc8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=764b4e68-f4c1-4c7b-bc0e-52cc2c752ba0  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

$ free
             total       used       free     shared    buffers     cached
Mem:       1282208    1265976      16232          0     119348     368668
-/+ buffers/cache:     777960     504248
Swap:      2570360       2152    2568208

---

### Post by caljohnsmith on 2009-02-23
> **merlin666 said:**
> I have changed the fstab. 
That's what I tried to warn you about in post #7: it's not as simple as just changing your fstab to use the new swap UUID if you want to keep your Ubuntu splash screen on start up, because you would also have to change your resume file and regenerate all your initrd images so they use the new swap UUID. How about doing the following:
```

gksudo gedit /etc/fstab
```
And change the swap UUID back to what it originally was:
```
# /dev/sda5
UUID=[COLOR="Blue"]506c3b10-c687-4605-ac8d-6a623b17e6ac[/COLOR] none swap sw 0 0
```
Then do:
```
sudo swapoff -a
sudo mkswap -U 506c3b10-c687-4605-ac8d-6a623b17e6ac /dev/sda5
```
Then reboot, and let me know if you get the Ubuntu splash screen with the progress bar OK or not. Once you are back in Ubuntu, also post:
```
free
```
And we can work from there.

---

### Post by merlin666 on 2009-03-21
Thank you, finally got around to doing this. Swap seems to fill up now once all memory is used.

Now to the next task - getting a graphics driver for mobility radeon 9600 (intrepid didn't install one).

---

