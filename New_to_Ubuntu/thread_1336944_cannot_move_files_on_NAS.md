---
title: "cannot move files on NAS"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2009-11-25
Currently I have Karmic Koala installed on my laptop and accessing a NAS (Synology DS108j) over a wired network.
This is the line in the fstab I have:
```
//192.168.1.41/public /media/public/ cifs nounix,username=xxxx,password=xxxx,file_mode=0777,dir_mode=0777 0 0
```
(Of course I xxxx in place of user name a passwords.)

Every thing seems fine except for a few issues.
Not everytime, but annoyingly often, if I create a new folder in an existing folder and try to move some files to it from that same folder (files not in use anywhere) I get the following error (see attachment)

There are related problems with the 'mount' of the NAS which I feel are related and may provide a hint to the cause and solution for one of you Linux guru's out there.

- Blender will not show me or seem to allow me to write files to the NAS
- GNUcash has a parsing error when trying to open my accounts file after making a copy on my NAS (an important and annoying problem for me)

Can anyone help me

---

### Post by steinzeitmensch on 2009-11-25
Just made a new discovery to this problem. Or more accurately, aonther symptom! This one hurts! Gmail has introduced a new attachment routine which allows for multiple simoltaneous attachments. This new feature will allow me to see files on my NAS but I cannot attach them!

What the hell is going on with my mount?
Can someone help me please?

---

### Post by quinnten83 on 2009-11-25
what happens when you run the mount as root or if you try to move the files as root?
I have a similar problem when running Ubuntu in virtualbox on Windows, where I can not save files to the windows shared folder without being root. So I have to open nautilus-root and then everything is all happy and stuff...
I haven't found a good solution to my problem, but then again, it's not a lifethreaning situation, so I haven't really looked.

---

### Post by steinzeitmensch on 2009-11-25
I have not tried this.
But what I can say is that the problem is intermittent. Sometimes all I have to do is create another folder calling it 'weiojinoeir' (i.e. whatever) and then try to move the files again and usually I will get it to work. Then I will simply rename the folder.
Pain in the **** work around, but got no choice at the moment.
The other symptoms are more acute though, especially the new one with gmail attachments not working at all.

---

### Post by ukripper on 2009-11-25
can you post output ofbelow:
```
mount
```



```
tail -n  200 /var/log/messages
```

---

### Post by steinzeitmensch on 2009-11-25
```
alex@alex-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
//192.168.1.41/public on /media/public type cifs (rw,mand)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)

```

the output for    tail -n  200 /var/log/messages     is too long to put all down here. See the attachment.

---

### Post by steinzeitmensch on 2009-12-08
I am wondering if anyone has any ideas on how I can fix this problem. Or has anyone any advice on other places I could search for help in this problem.

I know it sounds desperate but I am drifting dangerously close to pulling out my old windows disc and ending this Linux experiment.

Someone please help me

---

### Post by ukripper on 2009-12-08
check permissions on your nas drive's mounted directory using below command;
```
ls -al /media/public
```

post here if necessary

---

### Post by steinzeitmensch on 2009-12-08
Hi UKripper

Here is the output you requested

```
alex@alex-laptop:~$ ls -al /media/public
total 4
drwxrwxrwx  9 root root    0 2009-12-08 04:32 .
drwxr-xr-x  5 root root 4096 2009-12-08 14:20 ..
drwxrwxrwx  7 root root    0 2009-10-04 12:50 ART
drwxrwxrwx  5 root root    0 2009-11-26 14:42 AV MEDIA
drwxrwxrwx  3 root root    0 2009-08-08 11:53 BACKUPS
drwxrwxrwx  8 root root    0 2009-11-08 20:53 BIZ
drwxrwxrwx 10 root root    0 2009-10-14 11:03 FAMILY
drwxrwxrwx 19 root root    0 2009-10-27 16:31 #recycle
drwxrwxrwx  1 root root    0 2009-10-05 10:16 TEMP SHARE FOLDER

```

---

### Post by steinzeitmensch on 2009-12-15
Could this problem have anything to do with my upgrade to Ubuntu 9.10?
Seems that this was the start of most of my issues!
This problem is confounding me because *another* application that I heavily use and had no problems with accessing and writing files to my NAS has failed as of the last few days! QCAD.

---

### Post by kellemes on 2009-12-15
Having a ds207+ myself I have this problem often also..
When I create a folder from the Synology webinterface I seem to be able to write to that folder without trouble. Have you tried this?

---

### Post by steinzeitmensch on 2009-12-15
Hi and thanks for the tip.
I just tried this. I guess you were talking about enabling the 'file station' function and using this web interface to the NAS to create a folder.
I did this to test of that folder acted any differently.
Since this copy/move problem seems to be intermittent, I did not detect it in my test.

This test though did nothing to alleviate the problem that programs that could access my NAS, and now cannot. i.e. they now either cannot see it (QCAD), or see it but cannot retrieve files from it (Gmail with attaching and Blender).

The other program that cannot interact with the NAS at all is GNUCash.

By the way, if creating the folder in the NAS were to have solved the problems, this would only have been a diagnostic step, since it would only represent a poor workaround, what with having to go the web interface of the NAS to do any filing work.

I am sorry to say that all in all, my frustration is reaching a point that for all its shortcomings, Windows is looking better and better. Or to be kinder to Linux, it is seeming to me to be further and further away from being ready for mass market use.

At the moment (and in this I think I speak for the masses) I just do not have the time to make lengthy investigations or trials to discover the problem.
So I plead with the Linux guru's for some assistance in this seemingly basic and vital function of any computer i.e. mounting of drives!.
Luckily (and with heavy irony) I also have no time at the moment to switch back to windows.

Thanks again for you input to this issue, but it remains nowhere nearer to resolution.

---

### Post by eriktheblu on 2009-12-15
I had a problem writing to my NAS a while back after upgrading to Karmic.

Adding the noperm option to the FSTAB seemed to fix it.

Not saying it will work, but easy solution if it does.

---

### Post by ukripper on 2009-12-15
> **steinzeitmensch said:**
> 
```
//192.168.1.41/public /media/public/ cifs nounix,username=xxxx,password=xxxx,file_mode=0777,dir_mode=0777 0 0
```
(Of course I xxxx in place of user name a passwords.)


first unmount your NAS :
```
sudo umount /media/public
```
ok now ,can you replace your fstab entry and comment out the previous one with this:
```
//192.168.1.41/public /media/public cifs rw,_netdev,noperm,nounix,user=<username>,password=<password>,file_mode=0777,dir_mode=0777 0 0
``` 


and then run this command 
```
sudo mount -a
```

---

### Post by steinzeitmensch on 2009-12-15
Sorry but no cigar :(

of all the things that I can definitively check, there has been no change with this edit of the fstab.
The file moving seems to work but this is an intermittent problem anyway and I am getting the feeling that this is a different case now because it seems to be a nautilus problem. I never seem to have this problem with with Thunar or directly in the terminal.

Anyone else out there can shed any new light on this one please.

btw: any 'plain english' guides to cifs and the options?

All the sites I find on the net seem to assume a level of Linux knowledge that I do not have.

---

### Post by ukripper on 2009-12-15
This is a good starter - [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]](https://help.ubuntu.com/community/MountWindowsSharesPermanently])

---

### Post by ankans on 2009-12-23
Hi,

Ever since upgrading to Karmic, I am not able to attach any files from the Windows Folders into gmail. I can view them and open them in my computer- also attaching them in thunderbird is not a problem but Gmail sends the mail without the attachments.
I tried attaching files from non mounted drives and they went fine. I also tried the noperm option in /etc/fstab, but that didn't help.
Any clues, anyone?

---

### Post by steinzeitmensch on 2009-12-23
The change with Gmail may also be caused from Gmail and not from Karmic. Gmail has changed something in their mail so that users can attach multiple files simoltaneously. This may also be a cause. My problem is also Gnucash and Blender not being able to see files on the NAS.

---

### Post by ukripper on 2009-12-24
Try this option - add "**[COLOR="Red"]noserverino[/COLOR]**"  in your fstab 

Taken from here :[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
> 
KARMIC: Files owned by root / "The folder contents could not be displayed"
Note for KARMIC users encountering this error:
There is a bug affecting some users (particularly those with NAS devices like the Timecapsule) which gives the same symptoms as this problem. Bug report is here: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/406466](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/406466)

Fix is simple, just add the "noserverino" option to the mount command like so:
Code:

//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

Thanks to Dareus for posting the fix for this problem.

---------####---------

Permissions are always dr-xr-xr-x (read only) no matter how the share is mounted. Please see this Microsoft support document: [http://support.microsoft.com/kb/326549/](http://support.microsoft.com/kb/326549/)

Thanks to HyugaRicdeau for discovering the fix for that troublesome problem.

---------####---------


---

