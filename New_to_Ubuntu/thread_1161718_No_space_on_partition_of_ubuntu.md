---
title: "No space on partition of ubuntu"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by varunreeves on 2009-05-17
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  8.3G  728M  93% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  216K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.7M  249M   2% /dev
tmpfs                 251M  420K  251M   1% /dev/shm
lrm                   251M  2.0M  250M   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda3              20G  7.2G   12G  39% /media/disk
/dev/sda4              25G  6.4G   17G  28% /media/Yojimbo

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux
/dev/sda2            1246        1494     2000092+   5  Extended
/dev/sda3            1495        4105    20972857+  83  Linux
/dev/sda4            4106        7296    25631707+  83  Linux
/dev/sda5            1246        1494     2000061   82  Linux swap / Solaris



please see this for properly formatted version.I dont know how to paste formatted code so please tell me that also----http://pastebin.ubuntu.com/174024/

This is the structure now the problem :
1.I log in to sda1 i.e it is where ubuntu is it has a space of 11gigs as u see
2.I  did not have sda4 initially and all that space was raw space.I then decided to use partition manager and formatted it and selected a mount point like there was for sda3 and named it Yojimbo so now my /media directory  on the filesystem in the directory--- /media:  are /media/disk --sda3 20 gigs (used 7.2)gigs and /media/Yojimbo---sda4 25 gigs(6.4 gigs used).Before step two I had a around 8-9 gigs of space on the sda1 which showed as free space.Now I presumed I had done everything right and so I had another 25 gigs of space.I then place some files on the new partiotion thereby filling it up by 7.2 gigs but now the when I see the free space in the sda1 it shows that the free space has reduced by 7.2gigs!!!!!.So naturally I decided find how this has happenned .I tried right cliking on all folder on the "/" directory ie /home  , /tmp  , /media etc and so I saw that when I right click on /media and click properties it tells me that used space is 7.2 gigs i.e it is counting the used space of sda4 as the used space in sda1.The other sda ie sda3 is ok i.e it just has a mount point /media/disk  but no problems like sda4 .

3.I accidently deleted the /tmp directly i.e the tmp folder under root.I was trying to make more space.
4.Another problem surfaced now.I have an external hard drive which is 500 gigs.I use it to back up data.I did this again and unmounted it but the /media directory still shows /maxtor and shows 1.5 gigs as the used space and now the sda1 which is my installation partition shows free space = 0.

5.I use sudo rm to remove the folder /media/maxtor and now I get free space 1.5 gigs but still the 7.2 gigs is not avialable on sda1.
6.The /media/maxtor folder appears when I do update or some thing and restart and so I have to delete again.

7.I guess I did not do proper mounting or formatting of the sda4 drive.
please help

---

### Post by jms1989 on 2009-05-17
Try umounting all partirtions in /media and clearing your log files.

---

### Post by varunreeves on 2009-05-17
hello ,thanks.How do I delete the logs

---

### Post by zvacet on 2009-05-17
> Now I presumed I had done everything right and so I had another 25 gigs of space.I then place some files on the new partiotion thereby filling it up by 7.2 gigs but now the when I see the free space in the sda1 it shows that the free space has reduced by 7.2gigs!

You must made mistake,because from what are you saying it look that you copied files on wrong partition or you copied them on both.Check what do you have on root and on new partition.If you have same files on both then delete from root and you will still have your files on new partition.

---

### Post by mapes12 on 2009-05-17
> I accidently deleted the /tmp directly i.e the tmp folder under root.This Howto may help: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

