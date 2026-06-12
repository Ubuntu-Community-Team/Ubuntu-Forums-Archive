---
title: "need help mounting network drive"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by whorobj on 2007-02-17
I have a ntfs drive shared on win 2k3 on my server on the same network  as my ubuntu pc. I'm trying to mount the network drive (//server2/media) to (/media/server2).  I've done it before and it mounted perfectly but i did not have read write access, only root did.  It didnt rmeount at startup and i lost the commands.

I put this like in /etc/fstab

[PHP]//192.168.1.21/media /media/server2 smbfs credentials=/home/rob/. smbpasswd,uid=rob,gid=users 0 0[/PHP]

I tried running it in terminal and get this

[PHP]rob@rob-desktop:~$ sudo mount -t smbfs /192.168.1.21/media /media/server2 smbfs credentials=/home/rob/. smbpasswd,uid=rob,gid=users 0 0
Password:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
[/PHP]

I cant figure out whats wrong with it.

I need help on what i put in fstab to gain my user read write access to the drive and mount it at startup.  

ive been to > [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
and it didnt help me, it put me where i am now



so i need to be able to mount
//192.168.1.21/media /media/server2 at startup and grant user rob in the usergroup users read/write access without having to manually do everything one step at a time with sudo from terminal.

help please!

---

### Post by bernied on 2007-02-17
Maybe you just need the double // for the remote location. It will be looking on your local machine otherwise

---

### Post by bernied on 2007-02-17
It also looks like you've got a stray space in that fstab entry, in the filename for the credentials.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> Maybe you just need the double // for the remote location. It will be looking on your local machine otherwise
thats a typo there is a double // ill edit it

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> It also looks like you've got a stray space in that fstab entry, in the filename for the credentials.
tried it with the space fixed (it showed the space in the how to so left it in) and it shows the same thing

---

### Post by bernied on 2007-02-17
And this:
> rob@rob-desktop:~$ sudo mount -t smbfs /192.168.1.21/media /media/server2 smbfs credentials=/home/rob/. smbpasswd,uid=rob,gid=users 0 0doesn't make any sense. As that response told you:
> The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted. 
So, manually:
```
sudo mount -t smbfs //192.168.1.21/media /media/server2
```then smbmount will ask you for your credentials.
Also be sure that the mountpoint location /media/server2 exists on the local machine.

---

### Post by whorobj on 2007-02-17
that does help but i'm still nowhere with how to grant my user read/write access on the share. I need to be able to save to it from the gui and such so i cant manually create folders and files from sudo when i need to, its ridiculous. any ideas on this?

---

### Post by whorobj on 2007-02-17
strange im getting this now > rob@rob-desktop:~$ sudo mount -t smbfs //192.168.1.21/media /media/server2
mount: wrong fs type, bad option, bad superblock on //192.168.1.21/media,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I know the server is active and the share there because i can go to it manually by browsing the network


im thinking it has something to do with root owning the media folder it mounts to

---

### Post by bernied on 2007-02-17
What output do you get from:
```
sudo mount /media/server2
```

That space in the howto is a typo - check the line above, the one without the uid and gid set, that line doesn't have a space in the filename. If you have actually put a space in the filename, then you would need to refer to the file as '/home/rob/.\ smbpasswd' else mount would see that name as two parameters.

Have you checked your credentials file?
```
cat ~/.smbpasswd
```I don't need to see the output, if it looks right to you.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> What output do you get from:
```
sudo mount /media/server2
```
```
rob@rob-desktop:~$ sudo mount /media/server2
mount: unknown filesystem type '-o'
```

Have you checked your credentials file?
```
cat ~/.smbpasswd
```I don't need to see the output, if it looks right to you.
```
rob@rob-desktop:~$ cat ~/.smbpasswd
cd
echo username=administrator > .smbpasswd
echo password=b166er >> .smbpasswd
chmod 777 .smbpasswd

```

....

---

### Post by bernied on 2007-02-17
I would expect this
> mount: wrong fs type, bad option, bad superblock on //192.168.1.21/media,
missing codepage or other errorif you did not have smbfs (thats samba filesystem) support installed.

When you say you've done this before, was it on this install, or is this a new install since then?

If this is the same install, then it is possible that the last time you did not use smbfs, but maybe cifs instead (my understanding is that cifs is the replacement for smbfs, but I don't use it yet). You could try simply changing the smbfs to cifs in the mount command, post the output here.

If this is a new install, then install smbfs
```
sudo apt-get install smbfs
```
then try again

---

### Post by bernied on 2007-02-17
OK, that .smbpasswd file is a mess. It should only have the username and password values, like this:
```
username=administrator
password=b166er
```
nothing else. 
This is what you would have got if you'd run those commands in the howto from a terminal, rather than copying them into a text editor. I guess the howto was not very clear.

---

### Post by bernied on 2007-02-17
And this
> mount: unknown filesystem type '-o'suggests another typo in the fstab entry. Can you post what it looks like now?
You can get it quickly with this command (from a terminal):
```
cat /etc/fstab | grep server2
```

---

### Post by bernied on 2007-02-17
We are getting there, don't worry.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> We are getting there, don't worry.
IT WAS CIFS!!!1 i remember now lol let me try it.

---

### Post by whorobj on 2007-02-17
> rob@rob-desktop:~$ sudo mount -t cifs //192.168.1.21/media /media/server2 cifs credentials=/home/rob/.smbpasswd,uid=rob,gid=users 0 0
Password:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> And this
suggests another typo in the fstab entry. Can you post what it looks like now?
You can get it quickly with this command (from a terminal):
```
cat /etc/fstab | grep server2
```

```
rob@rob-desktop:~$ cat /etc/fstab | grep server2
//192.168.1.21/media /media/server2  -o user=administrator,pass=b166er,uid=rob

```

---

### Post by bernied on 2007-02-17
OK, so just add in the filesystem type (cifs) to the fstab entry, it should now look like this:
```
//192.168.1.21/media /media/server2 cifs -o user=administrator,pass=b166er,uid=rob
```
then try to 
```
sudo mount /media/server2
```again.
This may still not work, as the options for cifs are possibly different to those for smbfs. I'll have a look...

---

### Post by whorobj on 2007-02-17
> rob@rob-desktop:~$ sudo gedit /etc/fstab
rob@rob-desktop:~$ sudo mount /media/server2
[mntent]: line 12 in /etc/fstab is bad
mount: can't find /media/server2 in /etc/fstab or /etc/mtab

>.<

---

### Post by whorobj on 2007-02-17
this is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8d48257b-3a40-425c-b418-473b60f9d055 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=984a9e91-9dac-475e-90ce-349c1b488f46 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

//192.168.1.21/media /media/server2 cifs -o user=administrator,pass=b166er,uid=rob
```

---

### Post by bernied on 2007-02-17
Sorry, should have realised - that '-o' is wrong. One more time:
```
//192.168.1.21/media /media/server2 cifs auto,rw,user=administrator,pass=b166er,uid=rob 0 0
```
(I also added options for auto mount at boot - auto - and read/write - rw - and I added the two zeros at the end, we can talk about those later)

---

### Post by bernied on 2007-02-17
Maybe you've realised by now that the syntax for the mount command, although similar, is not the same as the syntax in the fstab file. It's the same information, but it's written differently. So you can't just copy one to the other.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> Sorry, should have realised - that '-o' is wrong. One more time:
```
//192.168.1.21/media /media/server2 cifs auto,rw,user=administrator,pass=b166er,uid=rob 0 0
```
(I also added options for auto mount at boot - auto - and read/write - rw - and I added the two zeros at the end, we can talk about those later)
ok so that goes in fstab. how to i execute it? im a lil confused. do i do a ```
sudo mount -t cifs //192.168.1.21/media /media/server2

```
?

---

### Post by bernied on 2007-02-17
Just
```
sudo mount /media/server2
```
When you just name the mountpoint (or the device), then the mount command will look for it in fstab. This is a good way to check your fstab entry. Post any errors, as usual.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> Just
```
sudo mount /media/server2
```
When you just name the mountpoint (or the device), then the mount command will look for it in fstab. This is a good way to check your fstab entry. Post any errors, as usual.

OMFG. FINALLY. It worked perfect! Thank you so much, now im happy iwht my ubuntu install :) 
From searching for my problem it looks liek this thread will help a few people with similar problems.

I do have one more question maybe you could help me with. I should be able to use all the functionality of the files on that drive as if they were local correct? ie buring a cd from audio files on the server

---

### Post by whorobj on 2007-02-17
for the people who had the same problem here is the line in my /etc/fstab

//192.168.1.21/media /media/server2 cifs auto,rw,user=administrator,pass=b166er,uid=rob 0 0

---

### Post by bernied on 2007-02-17
Superb! I'm happy too!
> **whorobj said:**
> I do have one more question maybe you could help me with. I should be able to use all the functionality of the files on that drive as if they were local correct? ie buring a cd from audio files on the server
Yes, it should behave as if it were on your local machine - the only difference will be speed, so you can burn files to a cd, if your network is reliable.

Now, go and change the password on that server2, before someone hacks you. And remember to change it in the fstab entry as well.

---

### Post by whorobj on 2007-02-17
> **bernied said:**
> Superb! I'm happy too!

Yes, it should behave as if it were on your local machine - the only difference will be speed, so you can burn files to a cd, if your network is reliable.

Now, go and change the password on that server2, before someone hacks you. And remember to change it in the fstab entry as well.
thanks again

---

