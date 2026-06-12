---
title: "My GRUB doesn't load windows"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by absolut24 on 2008-12-07
Hey guys,
I've been running windows for a while and I decided to install ubuntu. So I created a new partition and installed it and it went fine. However when I boot now GRUB has an entry for windows but hwen I click on it it doesn't boot. 
Here is my GRUB file:

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		26c427b8-7e4b-4f24-b451-8c66184bb736
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=26c427b8-7e4b-4f24-b451-8c66184bb736 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		26c427b8-7e4b-4f24-b451-8c66184bb736
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=26c427b8-7e4b-4f24-b451-8c66184bb736 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26c427b8-7e4b-4f24-b451-8c66184bb736
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26c427b8-7e4b-4f24-b451-8c66184bb736 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		26c427b8-7e4b-4f24-b451-8c66184bb736
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26c427b8-7e4b-4f24-b451-8c66184bb736 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		26c427b8-7e4b-4f24-b451-8c66184bb736
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

And here is my HDD's configuration

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2       60050   482343561    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9af734a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13672   109820308+   7  HPFS/NTFS
/dev/sdb2           13673       19457    46468012+   f  W95 Ext'd (LBA)
/dev/sdb5           13673       19228    44628538+  83  Linux
/dev/sdb6           19229       19457     1839411   82  Linux swap / Solaris

thanks guys

---

### Post by lovelyvik293 on 2008-12-07
I think that the /dev/sdb is secondary hard drive and that's why windows is not booting.To boot the windows just make the sdb primary.

---

### Post by absolut24 on 2008-12-07
How would I do that?
Thanks for the quick reply

---

### Post by kansasnoob on 2008-12-07
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

And here is my HDD's configuration

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

Device Boot Start End Blocks Id System
/dev/sda2 2 60801 488376000 f W95 Ext'd (LBA)
/dev/sda5 2 60050 482343561 7 HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9af734a

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13672 109820308+ 7 HPFS/NTFS
/dev/sdb2 13673 19457 46468012+ f W95 Ext'd (LBA)
/dev/sdb5 13673 19228 44628538+ 83 Linux
/dev/sdb6 19229 19457 1839411 82 Linux swap / Solaris

Well Grub begins numbering with 0 (zero), so where it says in the menu list: rootnoverify (hd1,0), hd1,0 is sdb1.

What I don't know is where Windows actually is?????????

We know it's not sdb1, but it could be sda2, sda5, or sdb2. (I doubt sdb2 because it's an extended partition.

As far as Grub is concerned sda2 = (hd0,1), or sda5 = (hd0,4).

Do you know what was on your first hard drive, and second hard drive?

---

### Post by caljohnsmith on 2008-12-07
What exactly happens when you boot Windows using that Grub entry that you all ready have? Do you get any errors? Also please post:
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one. That will help clarify which drive you are booting on start up.

---

### Post by kansasnoob on 2008-12-07
As I look at that more closely my best educated guess is, where it says:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

Change that so it says:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Microsoft Windows XP Professional
rootnoverify (hd0,4)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

***But that's 50% guess!***

You know to do that you have to open the menu list with Gedit by:

```
sudo gedit /boot/grub/menu.lst
```

Then be sure to click on Save, then File > Quit.

I just wish I were dead sure, but I'm not!

---

### Post by kansasnoob on 2008-12-07
Ah good! Listen to Caljohnsmith! He knows 110% more about these boot issues than I do!

---

### Post by caljohnsmith on 2008-12-07
> **kansasnoob said:**
> Ah good! Listen to Caljohnsmith! He knows 110% more about these boot issues than I do!
Thanks for the kind words, kansasnoob, great to see you around since we haven't bumped into each other recently. Hopefully we can help absolut24 get Windows booting OK. :)

---

### Post by absolut24 on 2008-12-07
I should clarify:
The windows partition is intalled on:
 /dev/sdb1 * 1 13672 109820308+ 7 HPFS/NTFS

sda is simply a storage drive

---

### Post by absolut24 on 2008-12-07
```

sudo xxd  -l  2 -p /dev/sda

```
eb48
```

sudo xxd -s 1049 -l 2 -p /dev/sda

```
04ff
```

sudo xxd  -l  2 -p /dev/sdb

```
33c0
```

sudo xxd -s 1049 -l 2 -p /dev/sdb

```
00ff

I should also specify that windows is installed on /dev/sdb1 * 1 13672 109820308+ 7 HPFS/NTFS

---

### Post by caljohnsmith on 2008-12-07
OK, according to those commands you ran, you have Grub installed to the MBR (Master Boot Record) of your sda drive, and you have a Windows MBR in your sdb drive. But something doesn't seem quite right with the results you got from the second command you ran on the sda drive, because you got "04ff" when I would have expected "0481"; "04ff" means that Grub looks on the same drive (sda) in partition #5 for its boot files (sda5), whereas "0481" would mean Grub is looking on the second boot drive (sdb) in partition #5 for its boot files (sdb5) which should be correct. 

But let me first ask again, what exactly happens when you boot Windows using that Grub entry that you all ready have? Do you get any errors? Please also post the output of:
```
sudo mkdir /mnt/sda5 /mnt/sdb1
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda5 /mnt/sdb1
cat /mnt/sda5/boot.ini /mnt/sdb1/boot.ini
```
Note "-l" is a lowercase L, not a one.

---

### Post by kansasnoob on 2008-12-07
Then it probably comes down to adding "makeactive" into the Win entry something like (but not exactly) this:

title Windows XP
root (hd1,0)
makeactive
chainloader +1 

Wait for Caljohnsmith. He'll have you straightened out pronto!

---

### Post by kansasnoob on 2008-12-07
Hmmm, what happened here?

---

### Post by absolut24 on 2008-12-07
When I start windows in grub with the current settings I get:

Starting up...
A disk read error occured
press ctrl+alt+del to restart

```

sudo mkdir /mnt/sda5 /mnt/sdb1
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda5 /mnt/sdb1

OUTPUTS:

/mnt/sda5:
total 68
drwxrwxrwx 1 root root     0 2008-09-20 20:54 Admin FTP
drwxrwxrwx 1 root root  4096 2008-09-06 19:15 BACKUP
drwxrwxrwx 1 root root     0 2008-09-06 14:46 Documents
drwxrwxrwx 1 root root  4096 2008-12-05 20:13 Movies
drwxrwxrwx 1 root root  4096 2008-09-06 19:17 Personal
drwxrwxrwx 1 root root  4096 2008-09-06 15:29 pictures
drwxrwxrwx 1 root root     0 2008-09-06 19:17 RECYCLER
drwxrwxrwx 1 root root  4096 2008-09-09 21:53 School
drwxrwxrwx 1 root root  4096 2008-09-06 17:32 System Volume Information
drwxrwxrwx 1 root root 40960 2008-12-05 20:13 tv shows
drwxrwxrwx 1 root root  4096 2008-12-05 20:25 windows software

/mnt/sdb1:
total 2095485
-rwxrwxrwx 1 root root          0 2008-09-06 17:28 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        211 2008-12-05 20:48 boot.ini
-rwxrwxrwx 1 root root          0 2008-09-06 17:28 CONFIG.SYS
drwxrwxrwx 1 root root          0 2008-09-23 14:54 cygwin
drwxrwxrwx 1 root root       4096 2008-09-06 17:32 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-09-06 17:28 IO.SYS
drwxrwxrwx 1 root root       4096 2008-10-18 15:40 lcc
-rwxrwxrwx 1 root root          0 2008-09-06 17:28 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-09-06 18:19 MSOCache
-rwxrwxrwx 1 root root      47564 2004-08-04 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-04 08:00 ntldr
drwxrwxrwx 1 root root          0 2008-09-06 18:25 NVIDIA
-rwxrwxrwx 1 root root 2145386496 2008-12-06 00:16 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-12-05 20:53 Program Files
drwxrwxrwx 1 root root          0 2008-09-06 18:17 RECYCLER
drwxrwxrwx 1 root root          0 2008-09-23 20:37 Scenario
drwxrwxrwx 1 root root       4096 2008-09-06 17:31 System Volume Information
drwxrwxrwx 1 root root      49152 2008-12-05 20:53 WINDOWS
drwxrwxrwx 1 root root      12288 2008-09-19 14:28 xampp


cat /mnt/sda5/boot.ini /mnt/sdb1/boot.ini

OUTPUTS

cat: /mnt/sda5/boot.ini: No such file or directory
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by caljohnsmith on 2008-12-07
OK, so your Windows is indeed on sdb1, and it has all its boot files which is a good sign. Often that "disk read error" is caused by the file system parameters being slightly corrupt in the Windows partition boot sector, and fortunately "testdisk" can usually fix it if that is the case. 

But first please post the output of the following:
```
sudo xxd -s 0x80 -l  2 -p /dev/sdb1
sudo dd if=/dev/sda count=60 | gzip -c > ~/Desktop/sda.MBR.gz
```
Hopefully the first command will return "08cd", so if not, be sure to let me know. The second command will create a really small "sda.MBR.gz" file on your desktop; please attach that file to your next post so I can check your sda MBR. Next, make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows from Grub, and please use the original Windows entry in the menu.lst that you have from your first post.

P.S. Many thanks to meierfra for providing the xxd command above and the signatures for finding out which boot code is in a partition boot sector.

---

### Post by kansasnoob on 2008-12-07
You didn't edit anything yet did you?

I'm not kidding when I say caljohnsmith will get this straightened out!

You see my thought would be to relocate grub to sdb/aka: hd1 and then edit the menu list but two people here have this down to a true science!

That's meierfra and caljohnsmith!

If either of them are giving you instructions just ignore the rest of us!

---

### Post by kansasnoob on 2008-12-07
Butting out now!

---

### Post by absolut24 on 2008-12-07
Hey caljohnsmith,
 Thank you so much!!
Testdisk was able to set my 160GB which contains the windows and linuz partition as sda1. 
I just to change the grub entry to 

root (hd0,0)

and remove the map. 
Thanks for all your help.

---

### Post by pearlie on 2009-02-19
Thanks caljohnsmith - I had the same problem, and this method worked for me right out of the box. Whew!

---

