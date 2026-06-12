---
title: "Root partition full - no space left on device"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by televisi on 2009-10-22
Hi All,
I'm using ubuntu server edition, for the past 3 days I unable to do "Rsync backup" which involves "mkdir" and "cp" functionality.

my "df -h":
```
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR=Red]/dev/mapper/VG-root--lv  30G   29G     0 100% /[/COLOR]**
tmpfs                 2.9G     0  2.9G   0% /lib/init/rw
varrun                2.9G  2.5M  2.9G   1% /var/run
varlock               2.9G     0  2.9G   0% /var/lock
udev                  2.9G  172K  2.9G   1% /dev
tmpfs                 2.9G     0  2.9G   0% /dev/shm
lrm                   2.9G  2.7M  2.9G   1% /lib/modules/2.6.28-11-server/volatile
/dev/sdb1             464M   25M  416M   6% /boot
**[COLOR=Blue]/dev/mapper/VG-data--lv  300G  146G  139G  52% /data1[/COLOR]**
```


if I run "mkdir /data1/blah/testing", the error:
**[COLOR=Red]/bin/mkdir: cannot create directory `/data1/blah/testing/': No space left on device[/COLOR]**

I'm not sure why both mkdir & cp unable to process, although the fact **[COLOR=Blue]/data1[/COLOR]** still have availability of 139GB?

Any clue?

Thanks heaps!

---

### Post by earthpigg on 2009-10-22
hi,

all linux filesystems need at least 5% of space to be free to function properly.

this is the price we pay for never needing to defrag.

---

### Post by televisi on 2009-10-22
is there any way I can know which one using the most of the partition? (ie: find large file from root excluding /data1 folder)

Also, Would this issue has something to do with swap files?

---

### Post by SirSlipALot on 2009-10-23
[Ubuntu Documentation]("https://help.ubuntu.com/") > [Community Documentation]("https://help.ubuntu.com/community") > [InstallingANewHardDrive]("file:///community/InstallingANewHardDrive?action=fullsearch&context=180&value=linkto%3A%22InstallingANewHardDrive%22") 


**Modify Reserved Space (Optional)**

 When formatting the drive as ext2/ext3, 5% of the drive's total space is reserved for the super-user (root) so that the operating system can still write to the disk even if it is full. However, for disks that only contain data, this is not necessary. 
NOTE: You may run this command on a fat32 file system, but it will do nothing; therefore, I highly recommend not running it. 
You can adjust the percentage of reserved space with the "tune2fs" command, like this: 
 sudo tune2fs -m 1 /dev/sdb1This example reserves 1% of space - change this number if you wish. 

Using this command does not change any existing data on the drive. You can use it on a drive which already contains data.

---

### Post by earthpigg on 2009-10-23
> **televisi said:**
> is there any way I can know which one using the most of the partition? (ie: find large file from root excluding /data1 folder)

Also, Would this issue has something to do with swap files?

i found this command on google (run in root terminal):

```
du -s * | sort -nr | head
```

then when you find the biggest one, move into it and run the command again from within that directory.

rinse, repeat.

unless you did some custom configuration: ubuntu uses swap ***partitions***, not swap files... and this doesn't look related.

---

### Post by mapes12 on 2009-10-23
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by bumanie on 2009-10-23
Try > sudo apt-get autoclean to clean up some left over packages etc. that are no longer needed due to updates.

---

### Post by televisi on 2009-10-23
Okay,
at the moment I'm running the following commands:
```
du -s * | sort -nr | head
``` 
Result: still waiting for the result...

```
sudo find / -type d -iname *Trash* | grep Trash
``` 
Result:  still waiting for the result...

```
sudo find / -path /data1/ -prune -or -size +500M -print
```  
Result: found 3 big files, they are:

```

-rw-r----- 1 root mlocate **[COLOR=Red]13G[/COLOR]** Oct 20 20:10 /var/lib/mlocate/mlocate.db
-rw------- 1 root root    [COLOR=Red]**16G**[/COLOR] Oct 24 08:27 /var/lib/mlocate/mlocate.db.RhKgGq
-r-------- 1 root root [COLOR=Red]**7.8G**[/COLOR] Oct 24 08:27 /proc/kcore

```I believe they are the victims?

I do some search on "empty kcore", found this [site]("http://help.lockergnome.com/linux/proc-kcore-big-empty--ftopict205677.html"), seems I'm not supposed to change kcore file?

Also, I believe mlocate is something to do with updatedb command?, should I empty it or even stop the service?, or should I make it rarely run?

Thanks heaps

---

### Post by televisi on 2009-10-23
Whoa!!!!,
when I kill "updatedb" process, my root folder gone back to normal.
This is what I found:

```

> ps aux | grep mlocate
root     28869  0.0  0.0   9008    80 ?        S    Oct21   0:00 /bin/bash /etc/cron.daily/mlocate
root     28875  1.4  0.0   4128   416 ?        D    Oct21  66:43 /usr/bin/updatedb.mlocate

> sudo kill 28869; sudo kill 28875; 

```

Now, my "df -h"
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VG-root--lv
                       30G  [COLOR=Blue]**1.4G   27G   5%**[/COLOR] /
tmpfs                 2.9G     0  2.9G   0% /lib/init/rw
varrun                2.9G  2.9M  2.9G   1% /var/run
varlock               2.9G     0  2.9G   0% /var/lock
udev                  2.9G  172K  2.9G   1% /dev
tmpfs                 2.9G     0  2.9G   0% /dev/shm
lrm                   2.9G  2.7M  2.9G   1% /lib/modules/2.6.28-11-server/volatile
/dev/sdb1             464M   25M  416M   6% /boot
/dev/mapper/VG-data--lv
                      300G  146G  139G  52% /data1

```

Yay!!!, now, to avoid same issue in the future, what do you think I should do? and **do I really need updatedb functionality** anyway? as most of the time I use "find" func instead?

I also notice with "locate" func, I can't use to find file as specific as "find" (although "locate" is totally faster with "find") please correct me if I am I wrong...

---

### Post by delphiexile on 2009-10-24
> **televisi said:**
> is there any way I can know which one using the most of the partition? (ie: find large file from root excluding /data1 folder)

Also, Would this issue has something to do with swap files?

You have a tool to do this
Applications-> Accessories-> Disk Usage Analyzer (this for detailed information)

but i prefer you go to 

System-> Administration -> System Monitor , click then on the Filesystem Tab , and tell us how much space you've used in the /dev/sda1 or (hda1 if your disk is not sata) ; if you are using more than 95% of disk space , it means everything is explained , you'll need to free up disk space.

If not , we should look further.

---

### Post by televisi on 2009-10-25
> **delphiexile said:**
> You have a tool to do this
Applications-> Accessories-> Disk Usage Analyzer (this for detailed information)

but i prefer you go to 

System-> Administration -> System Monitor , click then on the Filesystem Tab , and tell us how much space you've used in the /dev/sda1 or (hda1 if your disk is not sata) ; if you are using more than 95% of disk space , it means everything is explained , you'll need to free up disk space.

If not , we should look further.

Hi delphiexile, thanks for your suggestion, unfortunately I'm using Ubuntu server edition and all of them using CLI (as I'm not installing any desktop)

---

