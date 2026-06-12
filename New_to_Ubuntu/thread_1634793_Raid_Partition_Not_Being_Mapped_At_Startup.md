---
title: "Raid Partition Not Being Mapped At Startup"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by mercraus on 2010-12-01
I'll start off by saying thanks in advance to everyone who reads this and takes the time to respond. All help is appreciated.

Here's my setup:
-I'm running Ubuntu 10.10 64-bit
-I have 4 HDDs connected to my internal raid controller, which creates 2 logical drives: a JBOD and Raid 5 array
-The JBOD has 1 disk and 2 partitions: an ext4 mounted at /, and a swap partition. (I obviously boot off of this)
-The Raid 5 array has 3 disks and 1 partition: an ext4 mounted at /home (purely storage)

Here's my problem:
When I boot my computer I get this error: "The disk drive for /home is not ready yet or not present"

What I know so far:
-The Raid 5 array is located at /dev/mapper/nvidia_daiedbda
-The ext4 partition on the Raid 5 array is located at /dev/mapper/nvidia_daiedbda1
-When I boot, my /dev/mapper/ folder has the drive, but not the partition in it, like this:
```
ls /dev/mapper/
control     nvidia_daiedbda     nvidia_deficada     nvidia_deficada1     nvidia_deficada5
```
-I can fix this manually by doing
```
kpartx -a -v /dev/mapper/nvidia_daiedbda
```

So, how do I fix having to do this every time I turn on the computer? Thanks again for the help.

---

### Post by mercraus on 2010-12-01
bumpitty bump?

---

### Post by mercraus on 2010-12-02
Anyone have a suggestion?

---

### Post by mercraus on 2010-12-03
Third time's the charm?

---

### Post by mercraus on 2010-12-12
Still having the problem. Can anyone help please?

---

### Post by sandyd on 2010-12-12
> **mercraus said:**
> I'll start off by saying thanks in advance to everyone who reads this and takes the time to respond. All help is appreciated.

Here's my setup:
-I'm running Ubuntu 10.10 64-bit
-I have 4 HDDs connected to my internal raid controller, which creates 2 logical drives: a JBOD and Raid 5 array
-The JBOD has 1 disk and 2 partitions: an ext4 mounted at /, and a swap partition. (I obviously boot off of this)
-The Raid 5 array has 3 disks and 1 partition: an ext4 mounted at /home (purely storage)

Here's my problem:
When I boot my computer I get this error: "The disk drive for /home is not ready yet or not present"

What I know so far:
-The Raid 5 array is located at /dev/mapper/nvidia_daiedbda
-The ext4 partition on the Raid 5 array is located at /dev/mapper/nvidia_daiedbda1
-When I boot, my /dev/mapper/ folder has the drive, but not the partition in it, like this:
```
ls /dev/mapper/
control     nvidia_daiedbda     nvidia_deficada     nvidia_deficada1     nvidia_deficada5
```-I can fix this manually by doing
```
kpartx -a -v /dev/mapper/nvidia_daiedbda
```So, how do I fix having to do this every time I turn on the computer? Thanks again for the help.
```

sudo nano /etc/rc.local
```
add 
```

/bin/bash -c kpartx -a -v /dev/mapper/nvidia_daiedbda
```
press control + x

---

### Post by mercraus on 2010-12-14
> **sandyd said:**
> ```

sudo nano /etc/rc.local
```
add 
```

/bin/bash -c kpartx -a -v /dev/mapper/nvidia_daiedbda
```
press control + x
Yay, someone responded!!!

Thank you for the suggestion, but it didn't fix the problem. Maybe the script isn't executed until after the OS tries to mount home?

---

### Post by oloflarsson on 2011-05-04
Hello :)
Did you find a solution to this yet? Please tell me in such case. 
I am experiencing a quiet similar problem: One partition is missing in the /dev/mapper folder though I can add it using kpartx.

The question is: **How do I make it appear automatically at startup?**

==Now below is a big braindump hehe==

In my case I am running a Ubuntu 11.04 and Windows 7 in a dual boot setup.
I have two 2TB harddrives and use raid 0. The raid is a Intel Software Raid (isw) ("fakeraid" using dmraid). This means that it is not a real hardware raid and the volumes and partitions show up in the /dev/mapper/ folder like this:

```

olof@olof-P55-UD5:~$ ll /dev/mapper
total 0
drwxr-xr-x  2 root root     160 2011-05-04 12:03 ./
drwxr-xr-x 18 root root    4820 2011-05-04 10:03 ../
crw-------  1 root root 10, 236 2011-05-04 10:03 control
lrwxrwxrwx  1 root root       7 2011-05-04 10:33 isw_dbfdbhchhg_Media -> ../dm-4
lrwxrwxrwx  1 root root       7 2011-05-04 10:33 isw_dbfdbhchhg_OS -> ../dm-0
lrwxrwxrwx  1 root root       7 2011-05-04 10:03 isw_dbfdbhchhg_OS1 -> ../dm-1
lrwxrwxrwx  1 root root       7 2011-05-04 10:03 isw_dbfdbhchhg_OS2 -> ../dm-2
lrwxrwxrwx  1 root root       7 2011-05-04 10:03 isw_dbfdbhchhg_OS3 -> ../dm-3

```

So what I have done is that I created two raid 0 volumes (using the computer bios).
The first volume is isw_dbfdbhchhg_OS.
The second volume is isw_dbfdbhchhg_Media.

On partition isw_dbfdbhchhg_OS1 I have grub.
On partition isw_dbfdbhchhg_OS2 I have Windows 7.
On partition isw_dbfdbhchhg_OS3 I have Ubuntu.

But as you can see I only have the volume isw_dbfdbhchhg_Media.
There are no partitions. Though there should be.
isw_dbfdbhchhg_Media1 is missing.

The following verifies that isw_dbfdbhchhg_Media1 is missing:
```

olof@olof-P55-UD5:~$ sudo kpartx -l -v /dev/mapper/isw_dbfdbhchhg_Media
isw_dbfdbhchhg_Media1 : 0 6442500096 /dev/mapper/isw_dbfdbhchhg_Media 2048

```

and to add it I can just run:
```

sudo kpartx -a -v /dev/mapper/isw_dbfdbhchhg_Media

```

then i can mount it:
```

sudo mount -t ntfs /dev/mapper/isw_dbfdbhchhg_Media1 /mnt/media

```

**BUT: How do I make it appear automatically at startup?**

Here are som interesting links I found releated to this subject:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://linux.die.net/man/8/kpartx](http://linux.die.net/man/8/kpartx)
[http://people.redhat.com/~heinzm/sw/dmraid/readme](http://people.redhat.com/~heinzm/sw/dmraid/readme)
[http://ubuntuforums.org/showthread.php?t=1369224](http://ubuntuforums.org/showthread.php?t=1369224)


And here is some more info on my system:

This below tells us that this media volume is using a GPT partition table and the os volume is using a msdos partition table.
msdos is the default but it does not allow you to create partitions larger than 2TB. Therefore I used GPT.
```

olof@olof-P55-UD5:~$ sudo parted -l
Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary               boot
 2      106MB   351GB  351GB  primary
 3      351GB   702GB  351GB  primary


Error: /dev/sdb: unrecognised disk label                                 

Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_dbfdbhchhg_Media: 3299GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3299GB  3299GB  ntfs


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_dbfdbhchhg_OS: 702GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   351GB  351GB  primary  ntfs
 3      351GB   702GB  351GB  primary  ext4

```

This bellow tells us that I have two harddrives using Intel Software Raid (isw)
If you type "sudo dmraid -r -vv" (not the two "v" chars) you get even more info.
```

olof@olof-P55-UD5:~$ sudo dmraid -r -v
INFO: RAID devices discovered:

/dev/sdb: isw, "isw_dbfdbhchhg", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_dbfdbhchhg", GROUP, ok, 3907029166 sectors, data@ 0

```

**Well I will continue my search for a solution an post if I find one.**

---

