---
title: "Accesing other linux files from a different flavour of linux"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by superman on 2007-02-11
Hi everyone,

I have suse 10.1 and kubuntu 5.04 on the same hard drive on 2 different partitions. I was wondering how easy is it to access my media files on my suse partition from kubuntu.. 

thanks in advance

superman

---

### Post by Stephen Howard on 2007-02-12
shouldn't be any problem just mount the partition on a convenient directory:  
   [INDENT][FONT="Fixedsys"] mount /dev/hd[partition] /home/username/convenientdirectory[/FONT][/INDENT]

---

### Post by superman on 2007-02-12
I checked my fstab to see what I could find but all I found is this.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I think I see is the one partition that kubuntu is running under.. 5 and 6 are kubuntu if i'm not mistaken and the cdroms and my floppy. So it looks like I will have to add the partitions to my fstab if I am not mistaken. Am I correct. 

Sincerely 

superman

---

### Post by Stephen Howard on 2007-02-12
Post the output from:  
[INDENT][FONT="Fixedsys"]cat /proc/partitions    [/FONT][/INDENT]

That should tell us the partitions you have.  You could also post the output from this command: 
[INDENT][FONT="Fixedsys"]ls /dev/hd*[/FONT][/INDENT]

With that info we should be able to figure out the partitions.

Alternatively, you could simply boot into Suse and see what its /etc/fstab says.

---

### Post by Stephen Howard on 2007-02-12
> So it looks like I will have to add the partitions to my fstab if I am not mistaken. Am I correct. 

Adding to the fstab is the most convenient method, but you can do it manually by using the [FONT="Fixedsys"]mount[/FONT] command.  Its probably easier to do it manually first, and once you've figured out the details add a line into fstab.

---

### Post by superman on 2007-02-12
> **Stephen Howard said:**
> Post the output from: [INDENT][FONT="Fixedsys"]cat /proc/partitions [/FONT][/INDENT] That should tell us the partitions you have. You could also post the output from this command: [INDENT][FONT="Fixedsys"]ls /dev/hd*[/FONT][/INDENT] With that info we should be able to figure out the partitions. Alternatively, you could simply boot into Suse and see what its /etc/fstab says. Here is what I get when i do cat /proc/partitions 

major minor  #blocks  name

   3     0   60051600 hda
   3     1     779121 hda1
   3     2          1 hda2
   3     3   11743515 hda3
   3     4   17502817 hda4
   3     5   28772383 hda5
   3     6    1253038 hda6
 254     0     779121 dm-0
 254     1   11743515 dm-1
 254     2   17502817 dm-2
 254     3   28772383 dm-3
 254     4    1253038 dm-4

My fstab from kubuntu looks like this.

/dev/hda1            swap                 swap       defaults              0 0
/dev/hda3            /                    reiserfs   acl,user_xattr        1 1
/dev/hda4            /home                reiserfs   acl,user_xattr        1 2
/dev/hda5            /windows/C           vfat       users,gid=users,umask=0002,utf8=true 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
/dev/fd0             /media/floppy        auto       noauto,user,sync      0 0

---

### Post by Stephen Howard on 2007-02-13
Okay, this is how I see your setup:


[FONT="Fixedsys"]
hda1	swap	(weird config)	
hda2	unused (weird remnant)
hda3	root			
hda4	home 		
hda5	root  and/or  windows  (weird dual use)
hda6	swap 
[/FONT]


hda1 is a trifle odd because it doesn't mount swap properly - the first 'swap' on that line should read 'none'.

hda2 is harmless - just an unused partition

hda5 is really odd - based on your 10:36 posting, kubuntu thinks its a dos partition, but the other fstab (see your 5:36 posting) lists it as a root partition.

Given the general confusion, I think it'll be easier if you just boot up Suse, cd into the media directory and enter this command:

```
[FONT="Fixedsys"]df .[/FONT]
```

Write down the /dev/hda number that it outputs.

Next, boot into Kubuntu and create an empty directory somewhere convenient (eg  [FONT="Fixedsys"]mkdir ~/mymedia [/FONT]would create a directory call 'mymedia' in your /home).

Next type the following command, where xx is the number you wrote down earlier:

```
[FONT="Fixedsys"]mount /dev/hdaXX ~/mymedia[/FONT]
```

The above steps should have mounted the partition with the media at ~/mymedia.  cd into mymedia and then navigate around to the actual media directory.

If the above works, add the following line to your kubuntu /etc/fstab:

/dev/hdaXX    /home/{username}/mymedia    defaults 0 0

---

