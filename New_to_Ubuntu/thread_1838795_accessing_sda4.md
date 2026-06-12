---
title: "accessing sda4"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by lancearmstrong on 2011-09-04
[SIZE=4]i have installed ubuntu for the first time currently there is no other os in my laptop
i created the partitions manually as follows
1) sda1 --- 500 mb --- beginning ---- ext4 ----- /boot----PRIMARY)
2) sda5 --- 2gb ------- beginning ----- swap----- ( LOGICAL )
3) sda3 --- 150gb ---- beginning ---- ext4 ----- /----( PRIMARY )
4)sda4 ---- 167gb ---- beginning --- ext4 ---- /home----( LOGICAL )

the installation was successful 
but in places ---> computer only  cd drive and file system are shown and sda3 -- home has lost+found moreover only 137 gb is free what happened to the rest .. 
 
i am unable to access sda4 seems like all the memory is lost i checked in terminal it is saying 
even sda4 has lost+found 1 gb rest is free

please help how do i access sda4 there seems to be no folder showing that partition as in windows where my computer shows all the partitions 


[/SIZE]

---

### Post by Frozen Forest on 2011-09-04
Have you tried to mount the drive?

[PHP]
sudo mkdir /media/sda4 # create dir
sudo mount /dev/sda4 /media/sda4/ # mount sda4 in the folder /media/sda4
[/PHP]

---

### Post by Wim Sturkenboom on 2011-09-04
Under places, you should have something like home folder;that should be a subdirectory of the /home directory.
Under filesystem, you should have /home. That is the home directory.

If everything went OK during install, the home partition should be mounted on /home

You can use the mount command in a terminal to see what is mounted.


Note
Please use punctuations; make text easier to read
Please don't format text without a reason; this makes you post more difficult to read

---

### Post by lancearmstrong on 2011-09-04
firstly thanks a tonne for the reply

yeah i ran both the commands in terminal a folder got created in filesystem - media with name sda4
it contains lost+found folder and another folder with my user name . the folder with my user name again contains all the files present in file system

i would like to know if the partitions would be visible in places-- computer or not 
because as soon as i click computer i can see 2 icons 1) cd drive and another 2) file system the issue is that the file system is showing only 137gb freee what happened to the rest....

i created 4 partitions on the whole as mentioned above  
i checked the directory in terminal of sda4 its showing free space but in computer i can't see the folder

---

### Post by Wim Sturkenboom on 2011-09-04
Just wanted to edit my post to say thast it's normal that you don't see it in places->computer.

As you already replied, yes, it's normal ;)

---

### Post by Wim Sturkenboom on 2011-09-04
Are you talking about 150GB versus 137GB?

The Ubuntu install is approximate 5GB (I guess). Further space is reserved for the root user so that user can get intothe system if the HD is (nearly) full. That is about 5%, so in your case about 7.5GB.

---

### Post by lancearmstrong on 2011-09-04
ohk thanks for the reply one issue is solved i understood why it is showing only 137 gb ...

but what about the rest 167 gb  how can i access it .... it isn't showing any folder for that  ..........

i tought ubuntu shows all the partitions similar to windows once u click computer .

and what is lost+found i tried to access it in terminal but its showing no permission..

---

### Post by Wim Sturkenboom on 2011-09-04
As said earlier, the mount command should reveal if it's used

```

wim@desktop-01:~$ mount
/dev/sda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
**/dev/sda9 on /home type ext3 (rw)**
/dev/sdb1 on /photos type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fortyfourgalena/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fortyfourgalena)
wim@desktop-01:~$ 

```My home partition is /dev/sda9 and its mountpoint is the home directory. So if you have *_your_* /dev/sda4 mounted, you can use it.

Linux does not show the partitions as windows shows drives with drive letters. Partitions get mounted somewhere and are therefore part of the filesystem.

---

### Post by lancearmstrong on 2011-09-04
Thank you .....:P

---

### Post by Wim Sturkenboom on 2011-09-04
Pleasure; please mark your thread as solved using the thread tools just above the first post on this page.

Just a note. Although it's technically correct to mount /dev/sda4 on /media/sda4, it should not be necessary for your home partition.

Further /media is intended for things that get automatically mounted (e.g. an usb memory stick).
/mnt (mnt is in this case short for mount) is a better place for (semi-)permanently mounting partitions.

---

