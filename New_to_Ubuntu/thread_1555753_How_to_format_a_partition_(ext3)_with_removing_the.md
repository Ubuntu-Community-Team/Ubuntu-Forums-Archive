---
title: "How to format a partition (ext3) with removing the bad clusters?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by honeybear on 2010-08-18
I used this mkfs.ext3 but now I want to exclude the bad sectors during a formating procedure

Which command (console) shall be typed for that ?

---

### Post by stlsaint on 2010-08-18
If you are comfortable with terminal check out: [dd]("http://linux.about.com/od/commands/l/blcmdl1_dd.htm")

Thats just a brief (very brief) intro into what dd can do.

---

### Post by scorp123 on 2010-08-18
> **stlsaint said:**
> If you are comfortable with terminal check out: [dd]("http://linux.about.com/od/commands/l/blcmdl1_dd.htm") 

I fail to see how "dd" could be helpful here?? :confused:

---

### Post by philinux on 2010-08-18
> **honeybear said:**
> I used this mkfs.ext3 but now I want to exclude the bad sectors during a formating procedure

Which command (console) shall be typed for that ?

Bad sectors are remapped by the HD itself.

How many have you got.

---

### Post by scorp123 on 2010-08-18
> **honeybear said:**
> I used this mkfs.ext3 but now I want to exclude the bad sectors during a formating procedure 

Did you check the manual? ```
man mkfs.ext3
```

There is a "-c" switch that will check for bad blocks before creating the actual filesystem. I guess this is what you want?

From the manual (command: "**man mkfs.ext3**")
```
...

-c     Check the device for bad blocks before creating 
the file system. If this option is specified twice, 
then a slower read-write test is used instead of a fast read-only test.

...
```

---

### Post by stlsaint on 2010-08-18
> **scorp123 said:**
> I fail to see how "dd" could be helpful here?? :confused:

Than consider reading into dd. If you know where bad clusters than dd can be of use? Has many more options for formatting that im no expert on but if are the dd expert than possible you can shed some light where im wrong at!

---

### Post by honeybear on 2010-08-18
> **philinux said:**
> Bad sectors are remapped by the HD itself.

How many have you got.

some 10 still the same after 5years

---

### Post by honeybear on 2010-08-18
> **scorp123 said:**
> Did you check the manual? ```
man mkfs.ext3
```

There is a "-c" switch that will check for bad blocks before creating the actual filesystem. I guess this is what you want?

From the manual (command: "**man mkfs.ext3**")
```
...

-c     Check the device for bad blocks before creating 
the file system. If this option is specified twice, 
then a slower read-write test is used instead of a fast read-only test.

...
```

but the problem is that during install of ubuntu, it doesnt check them :( :(

---

### Post by scorp123 on 2010-08-18
> **stlsaint said:**
> Than consider reading into dd.  I use Linux since 1996. Thank you. ):P

> **stlsaint said:**
>  If you know where bad clusters than dd can be of use?  Right. Please show a command example, yes? Talk is cheap. Show me how it's done. Thank you ;)

> **stlsaint said:**
>  if are the dd expert than possible you can shed some light where im wrong at! "dd" copies blocks of binary data. That's it. It doesn't do zip for a filesystem. It can be useful if you have a badly damaged filesystem and you absolutely need a copy of what's still readable. Yes, in that case "dd" might be helpful. But then again this is not what OP asked ...

---

### Post by scorp123 on 2010-08-18
> **honeybear said:**
> but the problem is that during install of ubuntu, it doesnt check them :( :( No, because usually it's not needed and it takes an awful lot of time. 

But you could have the disk checked after installation:

You could boot into the live CD mode and then use a program such as "**gparted**". I am not sure if it's there "out of the box". If it is you will find it here:

***System > Administration > GParted***

If it's not there you will have to install it (Yes! this will work even if you are running off the live CD!), e.g. via this console command:
```
sudo apt-get install gparted
```

... and because you are running via Live CD it should not ask you any password at all. This is normal for the Live CD.

So once "gparted" is there you can open it, find the right harddisk partition and then have it checked by right-clicking on the partition and then click *"Check ... "*

It essentially will trigger the same filesystem checks that you would trigger via the console. So if "gparted" says that everything is OK, then there should be no problem.

If you want a console command ... OK, here we go:

Here just as above I will assume that you finished installing Ubuntu and that you rebooted using the Live CD session. According to the manual of **"fsck.ext3"** (***"man fsck.ext3"***) there is a "-c" switch for checking bad blocks, plus there is a "-f" switch that will force the check even if the OS thinks there is no need to do any checks.

So you'd use something like:

```
sudo fsck.ext3 -c -f /dev/sdXX
```

The parameter "sdXX" is the Linux Ext3 filesystem you want to have checked. So if your Linux OS is on the first partition of the first disk, then this would usually be **/dev/sda1** ... and so forth. If in doubt you can check this via **"gparted"** or via this command:

```
sudo fdisk -l
```

This will simply list all harddisk partitions and tell you their type and their device name. So it should be easy to find the correct partition ...

If I do that here I get this:

```
> sudo fdisk -l 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          17      136521   83  Linux
/dev/sda2              18       77825   624992760    5  Extended
/dev/sda5              18         328     2498076   83  Linux
/dev/sda6             329        1258     7470193+  83  Linux
/dev/sda7            1259        1717     3686886   83  Linux
/dev/sda8            1718        2630     7333641   83  Linux
/dev/sda9            2631        3683     8458191   83  Linux
/dev/sda10           3684        5907    17864248+  82  Linux swap / Solaris
/dev/sda11           5908       77825   577681303+  83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d8754c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032074

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c159

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30402   244196352    7  HPFS/NTFS


```

So /dev/sdd doesn't list a thing ... simply because it indeed is empty. /dev/sde1 is a Windows installation ... and the rest is all Linux.

Depending on how many harddisks and partitions you have in your system, your output might be far longer ... or far shorter, depending on how things are partitioned.

---

### Post by honeybear on 2010-08-19
thank you for your help! 

During installation: 

As you recommended to do gparted after, - well, I am sorry to say this but it hasnt worked the problem is that after installation the PC has missing some important programs:

passwd 
and few others that I noticed.

During install, it took ages copying those few files, and visibly not good on the resulted data at boot :( 

So it resutls in a non logable PC. From the linux install, the installation does not recommend bad clusters checking its process :(

---

### Post by scorp123 on 2010-08-20
> **honeybear said:**
> the problem is that after installation the PC has missing some important programs:

passwd 
and few others that I noticed. Sorry, I don't understand that. 

What you are supposed to do is:

1.) Install Ubuntu
2.) Reboot into Live CD
3.) Install "gparted" into Live CD
4.) Use the Live CD to scan the disk you just installed Ubuntu on.


What you suggest sounds like you didn't reboot but instead tried using your PC immediately after the installation?? That of course doesn't work.

And "passwd" is an integral part of any Unix-like system. If it's "missing" then you are doing something wrong :)



> **honeybear said:**
>  During install, it took ages copying those few files, and visibly not good on the resulted data at boot :(  You are not supposed to mess with the OS if you don't know what you are doing. You will just end up with a broken system.

Please follow the order I suggested.

1.) Install Ubuntu
2.) Reboot
3.) Boot the system with the Live CD
4.) Install "gparted" into Live CD session
5.) Scan the harddisk you installed Ubuntu on

... and don't mess with things manually if you are not sure what you are doing.

Hope this works for you ... bye ):P

---

