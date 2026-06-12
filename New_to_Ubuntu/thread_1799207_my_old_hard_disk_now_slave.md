---
title: "my old hard disk now slave"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by okkie on 2011-07-07
my old hard disk  with full ubuntu 10.10 installation now used as a slave disk.
If I mount the disk and click on it it opens 'lost+found'.I need to get into that file to reach info I need.If I click on lost+found it tells me I do not have permission to open.
Can anyone please help to overcome the permission problem.The hard disk is now called 'slave'.
Thanks

---

### Post by coffeecat on 2011-07-07
The lost+found folder in a ext3/4 filesystem will only have contents if you've run a filesystem check after filesystem corruption and fsck has found stray data to recover. When you mount the main partition do you see any folders apart from lost+found? Are you sure you are mounting the correct partition and not an empty one?

Whatever, if you want to open that folder, open a root nautilus with:

```
gksudo nautilus
```

If you find that the folder is empty, post back more details and we can take it from there.

---

### Post by okkie on 2011-07-07
here more detail:I had so much trouble with things that went wrong with my system on the now slave disk that I decided to buy a new hard disk and I installed a new 10.10 system on it which is now functioning right.I then changed the old disk to a slave and connected it to the computer.All my music and photos are still on the old disk and some documents which I now need to copy to the new hard disk.
I can mount the disk but can only get to lost+found.If I go to properties it says 7.6 GB is used which should be the contents of lost and found then.Permissions is unknown.I was hoping that what I need is in lost+f.How do I apply apply gksudo nautilus to the slave disk as it obviously will work with my new installation?
If everything is in your view lost,what must I do to be able to use the slave disk in future as it is in mint condition.
Thanks

---

### Post by okkie on 2011-07-07
In fact now that I have run gksudo nautiles I can get to nothing.By the way my new hard disk is called 'file system' after installation and I don't know why.Before I changed the old disk to slave,just a name change,it was called 'new volume' by the computer.

---

### Post by psusi on 2011-07-07
If its name is "new volume" and the only thing in it is the empty lost+found directory, then you formatted it.

---

### Post by coffeecat on 2011-07-07
I think we need to see what is on your two hard drives in the way of partitions. Open a terminal and post the output of these two commands:

```
sudo fdisk -lu
df -h
```

---

### Post by okkie on 2011-07-08
thanks for your trouble.Output as follows:okkie@mealone:~$ sudo fdisk -lu
[sudo] password for okkie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   312576704   156288321   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042a98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1947383807   973690880   83  Linux
/dev/sdb2      1947385854  1953523711     3068929    5  Extended
/dev/sdb5      1947385856  1953523711     3068928   82  Linux swap / Solaris
okkie@mealone:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             915G   14G  855G   2% /
none                  496M  252K  496M   1% /dev
none                  501M  356K  501M   1% /dev/shm
none                  501M  432K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
okkie@mealone:~$

---

### Post by coffeecat on 2011-07-08
You have a 160GB drive which is designated sda - the first drive. And a 1000GB drive which is designated sdb, the second. I suspect, though, that your 160GB sda drive is what you are calling the "slave". Are these IDE/PATA drives or SATA? If SATA, the old master/slave designations have no meaning. You define drive priority by which SATA port the drive is plugged into and by BIOS settings.

Whatever....

Drive sda has one single partition which is not mounted so the output of df -h is not helping. Your Ubuntu system is on sdb - sdb1 is mounted as your root partition.

Did you reformat your sda drive as psusi suggests? I rather think you might have done. Repeat the df -h command but this time make sure that the partition on the 160GB drive is mounted.

---

### Post by okkie on 2011-07-08
Thanks.I think if you don't mind,we take it step by step as my age is beginning to claim its toll.
The 160GB disk is connected the old fashioned way and the new one is SATA cable connected.Maybe this should be set up correctly first.What do I do in the bios?

---

### Post by coffeecat on 2011-07-08
> **okkie said:**
> The 160GB disk is connected the old fashioned way and the new one is SATA cable connected.Maybe this should be set up correctly first.What do I do in the bios?

No, that's OK. I was assuming that both were the same, older IDE/PATA drives or both SATA. By old fashioned way I guess you mean with a wide ribbon cable, which is what IDE/PATA drives use. Don't worry about the BIOS. As the system is working OK, there's nothing to change. You just need to be aware that your older hard drive is designated sda.

Boot up Ubuntu and mount the sda 160GB. Clicking on where it appears in the Places menu will be just fine. Then run and post the output of:

```
df -h
```

Then we can see whether the filesystem is empty or not. If, by chance, you have reformatted the 160GB and you haven't backed up your music and other personal files, then there is software that you can use which may recover it, but let's see what "df -h" shows first.

---

### Post by okkie on 2011-07-09
I just get the feeling we are now making headway,thanks.
df -hokkie@mealone:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             915G   14G  855G   2% /
none                  496M  252K  496M   1% /dev
none                  501M  356K  501M   1% /dev/shm
none                  501M  432K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
/dev/sda1             147G  188M  140G   1% /media/slave
okkie@mealone:~$

---

### Post by coffeecat on 2011-07-09
> **okkie said:**
> /dev/sda1             147G  188M  140G   1% /media/slave

The drive you refer to as "slave" is showing only 188MB of use, which seems to be very little. Make sure your "slave" drive is mounted the same way as when you ran df -h that last time. Now open a terminal, and:

```
gksudo nautilus /media/slave
```

Do you see only the lost+found folder, or are there other folders and files present? If only the lost+found folder, you will now be able to open it. Is there anything inside?

---

### Post by okkie on 2011-07-09
only lost+found as follows:okkie@mealone:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             915G   14G  855G   2% /
none                  496M  252K  496M   1% /dev
none                  501M  356K  501M   1% /dev/shm
none                  501M  432K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
/dev/sda1             147G  188M  140G   1% /media/slave
okkie@mealone:~$ gksudo nautilus /media/slave
Initializing nautilus-gdu extension

(nautilus:3850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3850'

---

### Post by coffeecat on 2011-07-09
You don't say whether there are any contents in the lost+found folder when you open it with a 'gksudo nautilus' file browser. You can ignore the error messages you get in the terminal when you run gksudo nautilus.

---

### Post by okkie on 2011-07-10
Lost+found now opened and contains root,desktop,file system,network,slave and trash.I opened file system,home,okkie and luckily all the files I had on my present system which I was under the impression is on my new hard disk, are still there.I tried to make a backup but no luck.Computer now only detects my cd drive and no longer the dvd drive.
In retrospect,When I decided to reinstall 10.10 on the new hard drive I understood you change the old disk at the back to slave ,hookup the new disk and the install disc does the rest.actually all went well and I had a good system running.Only when I started to recover info from the old disk all what we are busy with now evolved.I hope this will be useful to others as well and thanks again.

---

