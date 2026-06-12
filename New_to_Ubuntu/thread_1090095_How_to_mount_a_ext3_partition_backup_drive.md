---
title: "How to mount a ext3 partition backup drive"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by neilevan814 on 2009-03-07
I am writing this little how to for myself so I can reference for the future and thought this would be a good way to share as well.

I installed a second hard drive and wated to use it for a sole back up drive for my 3 computers. 
 
First: I formatted the drive as an extended partition and then created a logical ext3 partition to fill the entire drive.  

Next:  I created a directory for this drive in terminal

sudo mkdir /media/<name you choose>  mine is /media/backup_disk

Then:  I manually mounted the partition

sudo mount -t auto /dev/<partition> /media/<name>

<partition> is what is assigned to the logical drive in gparted
Now, you can check in your media directory that you do in fact have your drive mounted.  It is now mounted as root.  You can see this for yourself by running this command in terminal

cd /media/<name> 
$ ls -l

You can now change ownership of the mounted partition to yourself so that you can readily add folders to the partition without using sudo each time by entering this command at the terminal

sudo chown -R <your login name>:<your login name> /media/<name>

Now, so this drive will automatically be mounted for you at boot you must modify your /etc/fstab

First: sudo blkid

Mine looks like this:
/dev/sdb5: UUID="cbbc23cf-3928-41de-ab45-1603c26867ca" TYPE="ext3" 
/dev/sdb6: UUID="d8632395-4532-47e2-a900-3138e706d8a7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="f724a2c7-abb8-409c-9b64-f15b5a0404ff" 
/dev/sdb8: UUID="edf11f9f-22bd-4650-86dd-a6715980b4e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="12e21dce-4369-46ef-89c0-ffb889650c2c" TYPE="ext3" 

locate the /dev/<partition> you want to mount and make note of the UUID and TYPE

Next:  gksudo gedit /etc/fstab
 
add to the bottom of fstab(mine case scenario) note:make sure when you copy the UUID you do NOT add the quote marks to your entry

UUID=12e21dce-4369-46ef-89c0-ffb889650c2c /media/backup_disk ext3 rw,auto,user,exec 0 0

Here is a link to learn what all these fstab options actually mean and are doing for you [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

That is it.  You are done.  The next time you boot, you will see your drive show up on your desktop ready to use.  Hope this helps someone.

---

### Post by taurus on 2009-03-07
When you do the _sudo chown_ thing, you need to include the mount point.

And it's better to use gksudo (or gksu) if you are using gedit.

---

### Post by neilevan814 on 2009-03-07
Thanks taurus for filling in the gaps.  I myself am not sure why people use gksudo gedit, so if you can enlighten me to the reason, that would be much appreciated.

---

### Post by taurus on 2009-03-07
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by neilevan814 on 2009-03-08
Gotcha ..Thanks so if I run an application with a GUI then I should always use gksudo.  If I run an application that functions solely within terminal then it is safe to use sudo.  I will try to remember this as it does seem to be important.  I also fixed the chown section and gksudo section in the how to.

---

### Post by aspergerian on 2009-03-12
My HP Mini 1000 MI has a 60g HD and is loaded with Hardy Heron. Everything seems to be working. Today I used Gparted to create a data-storage area of appx 16g as ext3. That partition became hda3 or sda3. However, that partition is recognized but can't be mounted. I appreciate this specific instructions given in this thread, tried them, but sda3 still won't mount. Not via boot, not via Places. Here's how I followed the instructions:

tcb@tcb1:~$ cd /media/pdf-etc
tcb@tcb1:/media/pdf-etc$ 

tcb@tcb1:~$ sudo blkid
[sudo] password for tcb: 
/dev/sda1: UUID="2ea0f4a4-65f7-4791-8b97-571cbbe623d5" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f30550a8-1b25-4fdb-94bd-79d3de868050" 
/dev/sda3: UUID="e65bce39-ed57-42ad-8f19-c6701511d097" SEC_TYPE="ext2" TYPE="ext3" 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ea0f4a4-65f7-4791-8b97-571cbbe623d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f30550a8-1b25-4fdb-94bd-79d3de868050 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID="e65bce39-ed57-42ad-8f19-c6701511d097 /media/pdf-etc ext3 rw,auto,user,exec 0 0

Suggestions appreciated

---

### Post by taurus on 2009-03-12
> **aspergerian said:**
> My HP Mini 1000 MI has a 60g HD and is loaded with Hardy Heron. Everything seems to be working. Today I used Gparted to create a data-storage area of appx 16g as ext3. That partition became hda3 or sda3. However, that partition is recognized but can't be mounted. I appreciate this specific instructions given in this thread, tried them, but sda3 still won't mount. Not via boot, not via Places. Here's how I followed the instructions:

tcb@tcb1:~$ cd /media/pdf-etc
tcb@tcb1:/media/pdf-etc$ 

tcb@tcb1:~$ sudo blkid
[sudo] password for tcb: 
/dev/sda1: UUID="2ea0f4a4-65f7-4791-8b97-571cbbe623d5" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f30550a8-1b25-4fdb-94bd-79d3de868050" 
/dev/sda3: UUID="e65bce39-ed57-42ad-8f19-c6701511d097" SEC_TYPE="ext2" TYPE="ext3" 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ea0f4a4-65f7-4791-8b97-571cbbe623d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f30550a8-1b25-4fdb-94bd-79d3de868050 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=**[COLOR="DarkRed"]"[/COLOR]**e65bce39-ed57-42ad-8f19-c6701511d097 /media/pdf-etc ext3 rw,auto,user,exec 0 0

Suggestions appreciated

You have an extra **"** for /dev/sda3 in /etc/fstab.  Try to remove that and see if it mounts.

---

### Post by aspergerian on 2009-03-12
Taurus, Removing the extra " helped. The 16.8g partition was mounted during boot. As a test, I tried to drag the file in upper left corner into the 16.8g partition, but permission was denied. THe may be an image attached to this post. My next challenge will be resetting the permission so that I can write to and read from the 16.8g partition. Should I seek answers in other threads or is there a simple solution?

---

### Post by aspergerian on 2009-03-12
I found the thread about partition permission and guessed at a similar solution. 
[http://ubuntuforums.org/showthread.php?t=1093741&highlight=partition+permission](http://ubuntuforums.org/showthread.php?t=1093741&highlight=partition+permission)

Here's what I tried that after rebooting didn't work. I only added the last line in the following: 

gksudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ea0f4a4-65f7-4791-8b97-571cbbe623d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f30550a8-1b25-4fdb-94bd-79d3de868050 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=e65bce39-ed57-42ad-8f19-c6701511d097 /media/pdf-etc ext3 rw,auto,user,exec 0 0
/dev/sda3   /media/pdf-etc   ext3   iocharset=utf8,umask=000   0   0

---

### Post by taurus on 2009-03-12
> **aspergerian said:**
> I found the thread about partition permission and guessed at a similar solution. 
[http://ubuntuforums.org/showthread.php?t=1093741&highlight=partition+permission](http://ubuntuforums.org/showthread.php?t=1093741&highlight=partition+permission)

Here's what I tried that after rebooting didn't work. I only added the last line in the following: 

gksudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ea0f4a4-65f7-4791-8b97-571cbbe623d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f30550a8-1b25-4fdb-94bd-79d3de868050 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=e65bce39-ed57-42ad-8f19-c6701511d097 /media/pdf-etc ext3 rw,auto,user,exec 0 0
**[COLOR="Red"]/dev/sda3   /media/pdf-etc   ext3   iocharset=utf8,umask=000   0   0[/COLOR]**

Edit /etc/fstab and replace the current entry for /dev/sda3 with this one.

```
/dev/sda3   /media/pdf-etc   ext3   defaults   0   2
```
Save it then reboot.  Now, change the ownership of /media/pdf-etc from root to your login name, tcb, so you can write to it anytime you want.

```
sudo chown -R tcb:tcb /media/pdf-etc
ls -la /media/pdf-etc
```

---

### Post by aspergerian on 2009-03-13
Taurus, your last post's directions have enabled me to write to the partitioned "HD" known as pdf-etc and to then delete the test file there written. Your expertise, your clarity of specification, and your time are appreciated. 

This thread presents a solution for two problems: how to mount and how to access and use what has been mounted. Seems to me that this thread merits a "solved". 

Again, Thank you!

---

### Post by neilevan814 on 2009-03-22
Thanks Aspergerian.  I just wanted to say that I am happy that this thread has helped someone.  That makes me happy.  I am glad there are good staff members, like Taurus, floating on these threads to fill in the missing pieces and provide timely assistance, as I did not follow up quickly enough to help you myself.

---

### Post by aspergerian on 2009-03-22
My HP Mini 1000 with actual Hardy Heron (as different from HP's pseudo-Hardy-Heron) didn't automatically mount a SDHC card. I followed the instructions set forth earlier in this thread, and now the SDHC card is mounted and I have permissions to read and write to the SDHC. 

Would that all accurately asked Linux questions had such clearly expressed, precise, and functional solutions presented.

---

### Post by hopelessone on 2009-03-22
Ya Know the community docs have a good one...

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
because if its a backup drive why not set the reserved space to 0% and save space?

> sudo tune2fs -m 0 /dev/sdb1

HTH..

---

### Post by neilevan814 on 2009-03-22
Aspergerian, maybe I am being dense, but could you tell me what an SDHC is???  Thanks.

---

### Post by neilevan814 on 2009-03-22
Hopelessone I will have to read the thread you are pointing to.  I am unfamiliar with that command..Thanks.

---

### Post by neilevan814 on 2009-03-22
hopelessone...thanks for the tip that is a good command to utilize the whole disk, I may do that.  Since it is optional and this thread now has an entry that points to this excellent hard drive installation How To, I won't edit my original post.

---

### Post by aspergerian on 2009-03-22
Secure Digital card - Wikipedia, the free encyclopedia
 
The fact that SDHC format cards have the same physical shape and form factor as ..... SDHC (Secure Digital High Capacity, SD 2.0) is an extension of the SD ...
[http://en.wikipedia.org/wiki/Secure_Digital_card](http://en.wikipedia.org/wiki/Secure_Digital_card)

---

### Post by neilevan814 on 2009-03-22
Thanks for satisfying my curiosity Aspergerian.....glad all is working for you now.

---

