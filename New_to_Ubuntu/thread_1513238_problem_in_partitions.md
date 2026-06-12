---
title: "problem in partitions"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by phy4eveything on 2010-06-19
Hi every body
first I'm sorry for my bad English
second I'm a beginner in Linux and I need help in a problem . You know that the system partion in Linux prevent to copy or cut , &#8230;.. until writing password (enter to it as a root)
my problem is that the other partions do that with me and I do not know why . sometimes i restart the GUI to temporally fix it and it come again

---

### Post by HereInOz on 2010-06-19
Are you saying that your Home partition is sometimes not accessible to you and it says that access is denied?

Or are you talking about another partition or folder?

---

### Post by phy4eveything on 2010-06-19
thank you for replay 
no i do not mean my Home folder i mean other patition (fat partitions my pic my moveis , song .............)

---

### Post by yetiman64 on 2010-06-19
> **phy4eveything said:**
> thank you for replay 
no i do not mean my Home folder i mean other patition (fat partitions my pic my moveis , song .............)

Hi phy4eveything, If your drives or partitions are mounted to your /media folder, could you copy and paste into terminal the command
```
cd /media && ls -la && cd
``` and copy and paste the output here, (tell us which folders you need access to) and we can tell you which commands to use to change folder ownership/permissions etc to give you read and write access. 

By default "root" owns the folders in /media and if permissions are set to 755 you won't be able to write to them (ie cut and paste).

---

### Post by phy4eveything on 2010-06-19
hi yetiman64 
i do it 
total 64
> total 64
drwxr-xr-x  7 root  root   4096 2010-06-19 01:30 .
drwxr-xr-x 21 root  root   4096 2010-06-04 12:00 ..
lrwxrwxrwx  1 root  root      6 2010-04-05 14:00 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2010-04-05 14:00 cdrom0
lrwxrwxrwx  1 root  root      7 2010-04-05 14:00 floppy -> floppy0
drwxr-xr-x  2 root  root   4096 2010-04-05 14:00 floppy0
drwx------  6 ahmed ahmed 16384 2010-06-19 13:42 general
drwx------  6 ahmed ahmed 16384 1970-01-01 02:00 home
drwx------  6 ahmed ahmed 16384 1970-01-01 02:00 hotline


---

### Post by yetiman64 on 2010-06-19
> **phy4eveything said:**
> **Re: problem in partitions**
         hi yetiman64 
i do it 
total 64
     Quote:
                                                 total 64
drwxr-xr-x  7 root  root   4096 2010-06-19 01:30 .
drwxr-xr-x 21 root  root   4096 2010-06-04 12:00 ..
lrwxrwxrwx  1 root  root      6 2010-04-05 14:00 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2010-04-05 14:00 cdrom0
lrwxrwxrwx  1 root  root      7 2010-04-05 14:00 floppy -> floppy0
drwxr-xr-x  2 root  root   4096 2010-04-05 14:00 floppy0
d**rwx**------  6 **ahmed ahmed** 16384 2010-06-19 13:42 general
d**rwx**------  6 **ahmed ahmed** 16384 1970-01-01 02:00 home
d**rwx**------  6 **ahmed ahmed** 16384 1970-01-01 02:00 hotline                      

You own the folders in here so it should not be a problem to write to them. I suspect the folders may be mounted elsewhere. So again in terminal use 
```
cat /etc/fstab
``` and post back here (**higlight using the "bold" button in the editor the partition you can't access, like I've done with this text**)

---

### Post by phy4eveything on 2010-06-19
ok the problem is not able to access but the problem is i can not deal with the files ( creat folder , cut, copy, past , rename )
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=7b0cedab-ef2d-4c6b-9ad2-cb4af65f7b17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=41838535-eb65-47a6-a6a0-3a8c64ab4450 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


---

### Post by yetiman64 on 2010-06-19
> ok the problem is not able to access but the problem is i can not deal  with the files ( creat folder , cut, copy, past , rename )Yes I understand that is the problem, but first I need to find where the partition is being mounted as what I'm quoting from you above is ownership/permissions related and to give commands to change it require this information ;).

Can you post the full path to the folder you need to create folders in, cut, copy and paste in, for example, "/media/general" is one folder shown up earlier.

Nothing out of order is showing in fstab and you own and have write permissions to the folders in /media (general, home and hotline).

---

### Post by phy4eveything on 2010-06-19
thank you for intersting 
this  apic to view

---

### Post by yetiman64 on 2010-06-19
> **phy4eveything said:**
> thank you for intersting 
this  apic to view

First of all your're welcome, from the pic I see they are in the /media/home folder and you should have write permissions to ALL the subfolders as such.
 
Can you post the output of the command in terminal
```
whoami
```

---

### Post by phy4eveything on 2010-06-19
as a root or user 
this as a user 
> ahmed


---

### Post by yetiman64 on 2010-06-19
> **phy4eveything said:**
> as a root or user 
this as a user

As user is fine, easy fix is:

1. Goto Places menu > Computer > Filesystem > Media folder,

2. Right click on the Home folder, select Properties > Permissions tab.

3. For the owner (ahmed), for "Folder access" set it to "Create and delete files" and for "File access" set it to "Read and write".  You can leave the lower fields blank if you wish.

4. Click on the button at the bottom of the tab "Apply permissions to Enclosed files".

5. When done close the Properties box and the nautilus window. Reopen the nautilus window and check to see if the permissions have changed in the lower level folders.

You should now be able to write in the folders ie. create and delete and rename files etc.

Edit: repeat proceedure for general and hotline folders if necessary.

---

### Post by phy4eveything on 2010-06-19
thank you the problem is solved 
thank you very much for your help and time

---

### Post by yetiman64 on 2010-06-19
> **phy4eveything said:**
> thank you the problem is solved 
thank you very much for your help and time

You're most welcome phy4eveything. Could you mark your thread as solved please? To do so just follow the instructions in link #5 in my sig. Thanks. Yetiman64.

---

