---
title: "xsession lasted less then 10 seconds - can't log in"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by piergen on 2011-04-21
I suddenly got problems logging into Xubuntu.
I get notified that the xsession lasted less then 10 seconds. And I can not log on into xfce desktop. 

When I mark to see the error I get this:
> Unable to access file /home/username/.iceauthority: No such file or directory                      Don't know how to replace the file.
Btw this is not a permission issue that chmod will solve cause the file is really gone.

I tried to log in with failsafe mode, and I am able to start a terminal.
I tried to run this:

```
sudo startx
```Which resulted in this: **Result: Allready Running on desplay:0**

So then I tried this:

```
sudo startxfce4
```That worked and I was able to start a graphical desktop, not the same as last time cause there are things missing but at least I got a working box, and it seems  everything works fine, except that the graphic session is initiated via  terminal, so if terminal get closed either by misstake or whatever  desktop goes down.

But this is not a good way to log in, and also it seems like the .iceauthority is actually an imprtent file, even though it is not clear to me excactly what this file does. But it seems it has something to do with permissions and ownership and so on. 

So I would like to know what I could do to rectify this matter. So I can log in to desktop like normal, and be sure the xubuntu runs like it is supposed to.

**Any ideas how to solve this?**

Googling didnt help me even though many others had xsession issues those seemed to be related to permission or full tmp folder/disk.

---

### Post by piergen on 2011-04-22
I just discovered that I do have another .ICEauthority. That is a hidden file in the /home/username directory. But this file is actually named ICEauthority-n. I guess this must have been created by the failsafe session? 


Btw, I fear that the whole session is now run as root with full privileges  rather then as my username with limited privileges.. This is because I had to use the SUDO command to start xfce4 via terminal. 
And if this is correct I am actually running security on the same level as windows at the moment. Any breach in security would give up root access and that could be fatal.

How can I fix this? - seems all post about this issue is several years old and was caused by change of ownership to the .ICEauthority file. With me system things are different. 
The whole file have vanished. How can I make Xubuntu recreate the file? 

Or if there is no clever terminal commands that can fix this - will I boot disk/rescue disk help? I don't know how to tackle this problem. Pls help.

---

### Post by piergen on 2011-04-22
IS there any log-files that might shed some light on why this has happened?
If so what logfile should I look for? 

If there is anything I could post here in order for you Linux masters to give me pointers and advices I will do so immediately as long as you tell me what to post.

---

### Post by The Cog on 2011-04-23
What I suggest you do is to boot to the log-in screen. Rather than log in there, press Ctrl-Alt-F1 to get to a command prompt. You should be able to log in here. Then use the command 
```
rm .ICEauthority
``` to delete the file. 
Then use Alt-F7 to return to the login prompt. You should be able to log in normally now. 

The .ICEauthority file is automatically re-created as you log in. The only reason I can think that you might not have access to it is that you have at some point been running GUI apps with the sudo command, which runs them as root. This could then make the .ICEauthority file be owned by root, and prevent you as a normal user accessing the file again. If you ever want to run GUI apps as root, you should launch them with **gksu** rather thatn **sudo**, and that should provent the problem re-occurring.

---

### Post by piergen on 2011-04-23
Will not help me to run:

```
rm .ICEauthority
```

Because the file does NOT excist. Rather I have a filed named .ICEauthority-n

And deleting the file I_do_have does not work. After all when I reboot OS will once more look for the missing file.

Btw I have like most people run some graphical apps via terminal ie firefox. But I do not run the apps as a superuser, so I just would run this code:

```
firefox
```

and as far as I have read on various websites over the past days that should not cause any problems. 

At the moment my main consern is to know if the way I now log into the system have any impact on the level of security for the pc? I mean I start xfce4 via gnome failsafe terminal, and here I must use the sudo for things to work. Will the whole session be as root/superuser/admin?

---

### Post by The Cog on 2011-04-23
Hmm. The usual problem is that root ends up owning .ICEauthority. 

The only other thing I can think of is that maybe there is a problem with your home directory such that it cannot recreate that file. No such file or directory implies that your home directory doesn't exist. Can you do **ls -l /home** and verify that the correct username directory exists there, and that your user has rights to it?

Do you normally use a separate /home partition? If so, use the mount command and verify that it has in fact been mounted. One possible reason for your home directory not existing is that the /home partition has not mounted at boot the way it should. If this is the case, running fsck on the offending partition might fix the problem (I've had that happen to me a few times).

---

### Post by piergen on 2011-04-23
home directory excist.
When I run [B]ls -l /home
[/B]I get three different directories listed and myusername is oneof them.

Thing is when I right click on the home directory and check owner root is actually owner.
What do I do next?


Hmm looking at others /home directory I can see those have the file I am missing.
Which I find a bit strange because the error message was something like this:

> Unable to access file /home/username/.iceauthority: No such file or directory 			 		

And according to the error message system is looking inside myusername directory rather then inside it's parent folder the home directory.
If you look at the link below there it appears that the .ICEauthority files is placed inside home directory. I am not sure why the outputs are different here.

[http://ubuntuforums.org/showpost.php?p=6534195&postcount=5](http://ubuntuforums.org/showpost.php?p=6534195&postcount=5)

Here are the output of mine:

```
~# ls -l /home
total 32
drwx------  2 root  root  16384 2008-07-04 02:41 lost+found
drwxr-xr-x  2 root  root   4096 2008-08-13 15:15 my_iso
drwxr-xr-x 75 myusername myusername 12288 2011-04-23 10:08 myusername


```But do remember I used this to be able to log into desktop:

```
sudo startxfce4
```So for all I know the desktop I now see might be root desktop and root might have ownership to all data because of the way I logged in - does this make any sense at all? Or am I maybe overthinking this?

---

### Post by The Cog on 2011-04-24
It does make sense, and you are not overthinking things. sudo startxfce4 will be (I think) starting the login as root, not as myusername. The command **pwd** will print your current working directory, and I guess that when you log in this way, you are placed in /root. This is not the right way to go about things, and it would be better to find the reason that normal logins are failing.

The entry for /home/myusername looks correct to me. It is owned by you, and I would expect for there not to be a problem creating /home/myusername/.ICEauthority by the login process. 

The existence of /home/lost+found tells me that /home is indeed on a separate partition. lost+found is created by fsck (similar to DOS chkdisk) when a partition is checked. Since you can see that file, I presume that the /home partition has been succesfully mounted.

So I wonder why the error message saying /home/myusername/ doesn't exist. Maybe you don't have rights to enter /home (in which case, you wouldn't be able to see /home/myusername). Can you please do
```
ls -ld /home
``` and post the results, to make sure that /home has the correct permissions. Mine looks like
```
drwxr-xr-x 5 root root 4096 2010-10-14 21:07 /home
``` so it is owned by root, but others can read and enter it.

A further test might be to change your ID into myusername and then create the file by hand:
```
su myusername
touch /home/myusername/.ICEauthority
```
and see if you get any errors there.

P.S.
Your home directory is /home/myusername, not /home. /home is the directory that contains all the home directories of all the users, and this is true even if you have only configured one user.

---

### Post by piergen on 2011-04-24
Not exactly clear for me what you mean about this: > Do you normally use a separate /home partition?

I have a four disk raid 0 setup in a software raid. So the /home is not on a separate disk. I have a couple of samba shared sub-directories in my home directory. Those are available on home network as before.
The file structure seems to be just as before this happened. What I mean is that I can still see and access all directories and all my user created files like before. My photos, music, and documents are still accessible.  

I attached a screen shot of file structure if needed.

I followed your steps and here are the outputs:

**pwd:**
```
root@quadcore:~# pwd
/home/username
```[B]ls -ld /home:
[/B]```
root@quadcore:~# ls -ld /home
drwxr-xr-x 6 root root 4096 2008-11-30 18:28 /home
```[B]su myusername...
[/B]```
root@quadcore:~# su myusername touch /home/myusername/.ICEauthority
/usr/bin/touch: /usr/bin/touch: cannot execute binary file
```Btw, running a **su **in terminal I expected to be asked for password, cause I believe **su** is a legacy way of sudo still used in some Linux distributions. I wonder why I was not prompted for password, could that be the reason why it failed?

---

### Post by piergen on 2011-04-25
Anyone that can get anything out of this?
I can not believe I must do a new full install to fix this. Surely there must be a way to fix this matter?
Any tips and thought will be highly appreciated. If you need more info in order to give pointers pls let me know and I will post what you need asap. Really would like to put an end to this today, I have spent way too much time and energy already to bite the bullet and do a new install.

---

### Post by antony.s on 2011-04-25
Your su command is incorrect , and I think it is better to use sudo anyway, so try

```
sudo -u myusername touch /home/myusername/.ICEauthority
```

---

### Post by The Cog on 2011-04-25
This:
> su myusername
touch /home/myusername/.ICEauthority
was intended to be two separate commands. But you can do it with one command, either wtih sudo or with su, e.g.
> su -c '/home/myusername/.ICEauthority' myusername
and actually, doing it with one command would avoid the confusion of being left with a command prompt in myusername's id.

Can we confirm that the /home has actually mounted corectly, bu posting the output of the command **mount**? I wonder if it is mounting read-only. But the error message from trying to create .ICEauthority will also provide useful info.

---

### Post by piergen on 2011-04-25
Thx for your replies.
I tried both methods ending with the same result:

Below I forst did the **su myusername** and it changed froom root to myusername. 
But the rest did not work.

```
root@quadcore:~# su myusername
myusername@quadcore:~$ touch /home/myusername/.ICEauthority
touch: cannot touch `/home/myusername/.ICEauthority': No such file or directory
```And also tried the sudo way:

```
root@quadcore:~# sudo -u myusername touch /home/myusername/.ICEauthority
sudo: unable to resolve host quadcore
touch: cannot touch `/home/myusername/.ICEauthority': No such file or directory
```

> 
Can we confirm that the /home has actually mounted corectly, bu posting the output of the command **mount**?

Sure here we go:

```
root@quadcore:~# mount
/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/md0 on /home type ext3 (rw,relatime)
/dev/sdb1 on /tmp type ext3 (rw,relatime)
/dev/sda3 on /usr type ext3 (rw,relatime)
/dev/sda2 on /var type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdi1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

---

### Post by The Cog on 2011-04-25
OK, let's try it in pieces. Change to myusername and then try to get into your home directory step by step and see where it fails:
> su myusername
cd /
cd home
cd myusername
touch .ICEauthority
This should tell us what it thinks doesn't exist.

---

### Post by JKyleOKC on 2011-04-25
> **piergen said:**
> Btw, running a **su **in terminal I expected to be asked for password, cause I believe **su** is a legacy way of sudo still used in some Linux distributions. I wonder why I was not prompted for password, could that be the reason why it failed?The prompt you show indicates that you are, in fact, logged in as root. That's why you were not asked for a password. Actually, when logged in as root you don't need to use su or sudo at all to have full access. That's why it's dangerous.

As for su being legacy, actually it's the backend. The "sudo" command calls on "su" to do the change. While most folk think it means "super user" it actually means "switch user" and can be used to create a sub-session as any other system user. The "su yourusername" command suggested was intended to do exactly that, and had it asked for a password, the one it wanted would have been yours. But since you were running as root, it made the switch automatically.

As you show, the last character of the prompt changed from "#" to "$" when you ran the command. This, together with the name change, tells you that you are now running as yourself rather than as root.

I'll stay out of the way and let The Cog help you with the original problem, since I've never encountered it myself. I just jumped in to give a little more info about "su"...

---

### Post by piergen on 2011-04-25
Ok here we go here are the output:

As you see I am able to enter or drill down in directories all the way to /myusername. However the .ICEauthority does not exist.
If I use ie Thunar and makes it show hidden files I can see all system files as well. But what I can not see is the .ICEauthority file. I do however have a file 

```
root@quadcore:~# su myusername
myusername@quadcore:~$ cd /
myusername@quadcore:/$ cd home
myusername@quadcore:/home$ cd myusername
myusername@quadcore:~$ touch .ICEauthority
touch: cannot touch `.ICEauthority': No such file or directory
myusername@quadcore:~$
```

**But when I did a ls -la** I actually got a better view of the content of my /home/myusername directory. And guess what showed up?
Turns out i actually do have two files, and the "missing" one is actually stripped of ownership, etc. Could the lack of ownership be the reason the touch command did not work?

```
-?????????  ? ?     ?           ?                ? .ICEauthority
-rw-------  1 root  root      163 2011-04-24 10:53 .ICEauthority-n
```Will a chmod give me ownership of the file and will things be ok if I do have proper ownership?

I really wonder what might have caused this?

---

### Post by The Cog on 2011-04-25
That's a new one on me. You've definitely found the cause of your problems, but I don't think I know what it means. My first reaction would be to try and delete it, but I don't know if that will work. Similarly, chown and chmod might work, but I have a feeling they won't. I would certainly use .I<Tab> rather than use the full file name, just in case there are unprintable characters in the name - using tab will expand them properly even if you can't see them.

If not, I would be inclined to do the following as root:
Create a new directory for myusername and give ownershop over:
> mkdir /home/myusername-new
chown myusername:myusername myusername-new
Now move everything except .ICEauthority to myusername-new. You can do this with nautilus drag&drop between two windows (use Ctrl-H to turn on the showing of hidden files) or from the command line with the **mv** command. Nautilus will be quicker and easier.
Then rename /home/myusername to /home/myusername-old and then rename /home/myusername-new to /home/myusername. That way you effectively have a new home directory without that pesky file in it. You might be able to just delete myusername-old but if it's file system corruption, you may not be able to delete it even then, so just leave it there.

---

### Post by piergen on 2011-04-25
So I tried to change ownership, and I tried yet another trick but none worked:

```
root@quadcore:~# su myusername
myusername@quadcore:~$ sudo chown myusername /home/myusername/.ICEauthority
sudo: unable to resolve host quadcore
chown: cannot access `/home/myusername/.ICEauthority': No such file or directory
myusername@quadcore:~$ sudo chown myusername:myusername .ICEauthority
sudo: unable to resolve host quadcore
chown: cannot access `.ICEauthority': No such file or directory
myusername@quadcore:~$ sudo chown myusername /home/myusername/.ICEauthority
sudo: unable to resolve host quadcore
chown: cannot access `/home/myusername/.ICEauthority': No such file or directory
myusername@quadcore:~$ cd /
myusername@quadcore:/$ cd home
myusername@quadcore:/home$ cd myusername
myusername@quadcore:~$ sudo chmod 0644 .ICEauthority
sudo: unable to resolve host quadcore
chmod: cannot access `.ICEauthority': No such file or directory
myusername@quadcore:~$
```As you see I tried different stuff from websites I browsed and yet no solution that work. I am getting very frustrated and hot headed now. 

Others have fixed their problems I can see so surely this must be fixable in some way?

I find it strange that I can not see the file using Thunar, even if I make Thunarshow hidden files. But when listing all files in terminal that dang file show up anyway, how come that is at all possible?

---

### Post by The Cog on 2011-04-25
If sudo is busted, then you will have to try the chown and chmod commands as root. Since you are switching from root to myusername by using the command **su myusername** in the first place, you can revert to being root just by exiting the myusername sub-shell again. with the command **exit**. su doesn't actually change your identity, it launches a child sub-shell in the new user's identity.

As for sudo not being able to resolve the name quadcore, well that must be the name of your PC given in the file /etc/hostname. There should be a corresponding entry in /etc/hosts like this:
```
127.0.1.1 quadcore
```

---

### Post by piergen on 2011-04-25
> **The Cog said:**
> If sudo is busted, then you will have to try the chown and chmod commands as root. Since you are switching from root to myusername by using the command **su myusername** in the first place, you can revert to being root just by exiting the myusername sub-shell again. with the command **exit**. su doesn't actually change your identity, it launches a child sub-shell in the new user's identity.

As for sudo not being able to resolve the name quadcore, well that must be the name of your PC given in the file /etc/hostname. There should be a corresponding entry in /etc/hosts like this:
```
127.0.1.1 quadcore
```

Fixed the /etc/hosts and added 127.0.0.1 quadcore

But now I see you have written 127.0.1.1 - did I do it correct or should it actually be 127..0.1.1 like you wrote?
TEsted rebooting after, and at leat I can boot vie gnome failsafe like before, but If I have made it wrong I will change it one more time.

---

### Post by The Cog on 2011-04-25
I don't know why they put 127.0.1.1 - maybe to avoid a name collision with localhost which is always 127.0.0.1. I don't think it's that important, but 127.0.1.1 is what the installer actually uses. This is mine:
> 127.0.0.1	localhost.localdomain	localhost
::1	StevesPC	localhost6.localdomain6	localhost6
127.0.1.1	StevesPC

---

### Post by piergen on 2011-04-26
Ok now that part is fixed, I now have two hosts:

```
127.0.1.1 quadcore
127.0.0.1 localhost
# 127.0.1.1 quadcore.lan quadcore.private.lan

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.0.0.1 tester_u_dhcp
```

---

### Post by nebileix on 2011-04-26
A faster menthod will be to try create new user and see if the same problem occurs.

Backup and transfer your files according.

---

### Post by piergen on 2011-04-26
> **nebileix said:**
> A faster menthod will be to try create new user and see if the same problem occurs.

Backup and transfer your files according.

If I can't resolve this matter and find out what caused this and why .ICEauthority was stripped of ownership etc I really think a new install will be better. 

Making a new user sure that is fast, but all the settings and so on that was done to my account will be done over again, and then I rather start from scratch with a new kernel and brand new release as well. 

But I still hope I manage to resolve this without a clean install.

---

### Post by nebileix on 2011-04-26
Have u tried deleting the .ICEauthority from livecd? Maybe u can do a fsck before doing that.

---

### Post by piergen on 2011-04-26
I have not tried to delete file from a livecd. When I do fsck will I need to do that from livecd or could I do it directly from the terminal now?
Here are my partition, I run a 4 disk software rid 0 setup. Don't know if that matters.

```
Device:        Directory:
/dev/sda4        /
/dev/sda1        /boot
/dev/md0        /home
/dev/sdb1        /tmp
/dev/sda3        /usr
/dev/sda2        /var
```

To save som time is there a way I can run fsck without having the fsck to run for all partitions? Cause that will take forever. 
How do I unmount /home from terminal? And can doing so in any ways make matters worst? I mean so that I can not mount /home anymore.

And what command can I use to only check md0?

```
shutdown -r -F now
```
So the -r will reboot and the -F will cekck disks. But how can I force only check of /md0?

---

### Post by The Cog on 2011-04-26
You could run
> sudo fsck /dev/md0
from a live CD.

Or since you are logging in as root, you should be able to unmount /home and then do the fsck like this (You can't unmount a drive when you are using it for your working directory or holding files open):
> umount /dev/md0
fsck /dev/md0
mount /dev/md0

---

### Post by nebileix on 2011-04-27
> **piergen said:**
> I have not tried to delete file from a livecd. When I do fsck will I need to do that from livecd or could I do it directly from the terminal now?
Here are my partition, I run a 4 disk software rid 0 setup. Don't know if that matters.

```
Device:        Directory:
/dev/sda4        /
/dev/sda1        /boot
/dev/md0        /home
/dev/sdb1        /tmp
/dev/sda3        /usr
/dev/sda2        /var
```

To save som time is there a way I can run fsck without having the fsck to run for all partitions? Cause that will take forever. 
How do I unmount /home from terminal? And can doing so in any ways make matters worst? I mean so that I can not mount /home anymore.

And what command can I use to only check md0?

```
shutdown -r -F now
```
So the -r will reboot and the -F will cekck disks. But how can I force only check of /md0?

Hold on the shift key after system post and go into recovery mode

---

### Post by piergen on 2011-04-27
> **The Cog said:**
> You could run

from a live CD.

Or since you are logging in as root, you should be able to unmount /home and then do the fsck like this (You can't unmount a drive when you are using it for your working directory or holding files open):

Hmm can't umount home no matter what I try. I get return message that home is busy. 
I even tried it from singel???? whatever it is called, but from there it seems I must be root to umount /home. 

It is too long ago since the system was sat up, and I can not longer remember root password. I will try to see if I can find a way to recreate root password. Or maybe I can create new account with root privileges?

---

### Post by piergen on 2011-04-27
The recovery trick did work - thx.
umount worked fine. Then i did fsck /dev/md0

And I was expecting a really lengthy prcocess - like whenever system does a fsck by itself on boot. Rather in a second I got this line:
```
fsck 1.40.8 (13-Mar-2008)
/dev/md0: clean, 102270/91578368 files, 212573053/366285952 blocks
```Then I mounted and rebooted. 

When I got into desktop - yes same way as before via gnome failsafe and sudo startxfce4 I went to see the logs in var.  In fsck I see two files and here are the output:

```
checks:
Log of fsck -C3 -R -A -a 
Wed Apr 27 08:27:24 2011

fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 74/122880 files, 179515/489948 blocks
/dev/sdb1: clean, 14/917504 files, 70656/3660811 blocks
/dev/sda3: clean, 223182/6086656 files, 1003596/24316385 blocks (check in 3 mounts)
/dev/md0: clean, 102270/91578368 files, 212573053/366285952 blocks
/dev/sda2: clean, 9060/12214272 files, 536891/48827559 blocks

Wed Apr 27 08:27:26 2011

checkroot:
Log of fsck -C3 -a -t ext3 /dev/sda4 
Wed Apr 27 08:27:24 2011

fsck 1.40.8 (13-Mar-2008)
/dev/sda4: clean, 25113/12214272 files, 739552/48829567 blocks

Wed Apr 27 08:27:24 2011
```Ok glad to see that the drive where ok, but why is the log showing the date of 13 th of march 2008?

Feels like something is not right here. From what I have seen before the fsch takes a very long time, now it was over in seconds?
**So can now I trust that the /home is not corrupted?**

What would be the next step or the next thing I could try to fix this matter?

---

### Post by nebileix on 2011-04-27
That date should be the fsck version date i guess.

So can u mount /dev/md0 in recovery mode and delete the .ICEauthority?

---

### Post by piergen on 2011-04-27
> **nebileix said:**
> That date should be the fsck version date i guess.

So can u mount /dev/md0 in recovery mode and delete the .ICEauthority?

Yes I will try that right away. Didn't even think to try that while I was in recovery mode :)

---

### Post by piergen on 2011-04-27
Sorry to report that the outcome of rm /home/myusername/.ICEauthority was the same even from recovery mode. I got the same:

```
rm: cannot remove '/home/stian/.ICEauthority' no such file or directory
```

But as before if I do a ls -la I sure can see that file. 
Even if the file is stripped of all rights there most be possible to manually delete it? Or possible rename it?

---

### Post by nebileix on 2011-04-27
U might need to check layer above /dev/md0. I mean ur raid.

---

### Post by piergen on 2011-04-27
> **nebileix said:**
> U might need to check layer above /dev/md0. I mean ur raid.


Can yo elaborate pls cause I am not understanding this. Do you mean I need to run fsck on other partitions? 

We have confirmed /home is not corrupted, why would I need to check other partiotions or layers to solve this? I don't understand.

---

### Post by The Cog on 2011-04-27
I am wondering how the system got into this state. I am beginning to think maybe a re-install might be the safest move. We know that sudo was busted due to misconfiguration of files on the root partition, and we know that there is something amiss with at least on file on the /home partition. You do have to wonder what else is wrong.

One thing though, can you try the command
> getfacl /home/user/myusername/*
I expect an error saying that package acl is not installed, but a strange acl setting might explain the problem.

Also, try using tab completion when trying to delete the file, rather than typing the full name, just in case there are invisible characters in the name.

---

### Post by piergen on 2011-04-27
Here it is exactly as I typed into terminal.
First when I tried it the way it was posted here I was root and I got an error as you will see below. Then I used su myusername and that seemed to work. I have tried so many things over the past week that I could have forgotten to do measures like changing from root to myusername on other commands I have run. If this does not make any sense to you I will try everything from the beginning tonight both as root and myusername. I am not very good with computers or code so it could even be that I have messed up the code somehow, or used wrong path ie relative vs absolute. In fact I don't even know for sure what the term means. But I have tried to use the most sensible way about the commands posted here in the thread and I have mostly used copy and paste into terminal to be sure I avoid typos. But maybe some commands was written in a short way or not exactly as it should be run in terminal and then that could explain some of the errors?

```
root@quadcore:~# getfacl /home/user/myusername/* 
getfacl: /home/user/myusername/*: No such file or directory
root@quadcore:~# su myusername
myusername@quadcore:~$ getfacl /home/user/myusername/* 
getfacl: /home/user/myusername/*: No such file or directory
myusername@quadcore:~$ getfacl /home/myusername
getfacl: Removing leading '/' from absolute path names
# file: home/myusername
# owner: myusername
# group: myusername
user::rwx
group::r-x
other::r-x

myusername@quadcore:~$

```

---

### Post by nebileix on 2011-04-27
i mean u need to troubleshoot ur raid. might be due to ur raid.

---

### Post by piergen on 2011-04-27
Hmm how can that be? All the fsck seems fine. I can access all my files. 
The samba shares works fine, and the two vm's that run under vmware are fine. 
Something messed up one file, how can that be related to the raid?

---

### Post by The Cog on 2011-04-27
I owe you an apology, I didn't type that command right. If I could touch-type properly, I'd have been looking at the screen and seen that I was typing rubbish. The command I had in mind was > getfacl /home/myusername/*  but it proves the point that getfacl is installed (it's not in the default install so someone has installed it afterwards). getfacl is part of the acl package that allows configuring advanced access control lists to files and folders. If you didn't install it, and I guess from the trouble you are having that it's not something you would choose to install, I am beginning to think that an intruder is messing with your system. 

I'd be interested to see the output fromn getfacl, but I am more keen to know if you have been tinkering or whether someone else has been there.

---

### Post by piergen on 2011-04-27
Np The Cog. It is I that should say thank you for taking the time. 

Here are the output:

```
root@quadcore:~# getfacl /home/user/myusername/* 
getfacl: /home/user/myusername/*: No such file or directory
root@quadcore:~# su myusername
myusername@quadcore:~$ getfacl /home/user/myusername/* 
getfacl: /home/user/myusername/*: No such file or directory
myusername@quadcore:~$ getfacl /home/myusername
getfacl: Removing leading '/' from absolute path names
# file: home/myusername
# owner: myusername
# group: myusername
user::rwx
group::r-x
other::r-x

myusername@quadcore:~$
```

But I did not like what you said about tinkering in my system. How can I detect if someone messes around in my system?

---

### Post by piergen on 2011-04-27
In recovery mode I run fsck -fkv  /dev/md0

**Fsck fixed several errors including removing the .ICEauthority.**
It is now possible to log in like normal. 

If I now do a ls -la this show up :)

```
-rw-------  1 root  root      328 2011-04-27 20:42 .ICEauthority
```But when I checked the logs in /var/logs/fsck I could not see anything new in the logs? Does fsck not write to logs when doing a fsck -fkv in recovery mode?


**Off-topic:**
Now I just must fix the desktop. After the fixes from fsck was done I was able to log into my desktop like I normally do. Except I was missing all menus and panels. 

Also I have had a good learning experiance here, cause I have learned alot and also found out that all my backups are worthless if I loose me primary account cause myusername is owner of all my backups and I could not even read those files from another account even though they are on a external drive. I will fix the backups as well before I struggle with the desktop cause those are most importent to me. 

I surely would not have taken the time to read and learn all that I have absorbed over the past week if it was not for all the headache with the .iceauthority.  So now I can make a better backup routine, make sure permissions of that backup is ok and make sure that the next install I do will be more flawless. Thx all for taking the time.

---

### Post by JKyleOKC on 2011-04-27
> **piergen said:**
> If I now do a ls -la this show up :)

```
-rw-------  1 root  root      328 2011-04-27 20:42 .ICEauthority
```This shows that the file is owned by root rather than by your username, so you should use "chown" to restore yourself as the owner. If you're logged in as root (the prompt will show you if this is the case) just type ```
chown you:you .ICEauthority
```with your user name replacing "you" in both places. The permissions of r/w for the owner and none for anyone else are correct. And after you fix this, you may find that your desktop is back to normal without having to do anything else!

EDIT: Be sure that you are in your home directory, not in /root, when you do this!!! It appears quite likely that the desktop you are getting to is that of root, rather than your own. The command "pwd" will tell you exactly where you are.

---

### Post by The Cog on 2011-04-27
That's good news. So it looks as though it was just a bit of filesystem corruption after all. And I have learned that there are fsck options beyond those shown in man fsck.

As for the presence of facl, it occurs to me that I'm using xubuntu and not ubuntu. Can anyone confirm whether the **acl** package is installed by default on Ubuntu these days? Maybe my paranoia was showing.

---

### Post by piergen on 2011-04-27
> **The Cog said:**
> That's good news. So it looks as though it was just a bit of filesystem corruption after all. And I have learned that there are fsck options beyond those shown in man fsck.

As for the presence of facl, it occurs to me that I'm using xubuntu and not ubuntu. Can anyone confirm whether the **acl** package is installed by default on Ubuntu these days? Maybe my paranoia was showing.


The -fkv I am not enturly sure about, but if I got it correct  f=forcing even if log ok, K=bad sector or disc blocks. And the v=verbose I thought was going to put it all into log files. But I guess I was wrong on that part cause the logs are blank. So for the v parameter I have no idea what it mean. 

Hmm btw I am using xubuntu as well. Alltough it is a bit old, I am still on 8.04 LTS Hardy.
I am still wondering about the tinkering part, you really think my system has been compromised? How can I check that and what would I need to keep an eye on in the future?

---

### Post by The Cog on 2011-04-27
v means verbose (more words on what it's doing), but it only outputs to the console.

I don't know about tinkering. I don't think that Hardy had the acl package installed by default. The oldest install I've got lying around is Lucid 10.04 so I can't be sure of that though. Is it possible that you installed the package some time in the past, while trying things out? You've had a couple of years to do experimenting.

---

### Post by piergen on 2011-04-27
> **The Cog said:**
> v means verbose (more words on what it's doing), but it only outputs to the console.

I don't know about tinkering. I don't think that Hardy had the acl package installed by default. The oldest install I've got lying around is Lucid 10.04 so I can't be sure of that though. Is it possible that you installed the package some time in the past, while trying things out? You've had a couple of years to do experimenting.

Can't remember the **acl** package but more often then not one does not pay attention when doing a sudo apt-get installs, and there are very often lots of dependencies. So that is probably why?

It was really to bad the errors from fsck didn't get logged, cause I am sure you would know what it meant and maybe even what caused corruption in the first place. Could a sudden power-out during boot down but before system was halted have caused problems? We had a power out last week. What else can cause problems like this?

---

### Post by The Cog on 2011-04-28
> Could a sudden power-out during boot down but before system was halted have caused problems? We had a power out last week. What else can cause problems like this?It most certainly could, and power cust like that are probably the most common cause of filesystem corruption.

---

### Post by JKyleOKC on 2011-04-28
FWIW, I don't find the getfacl program on my Xubuntu Lucid installation but I do find that a package named "libacl1" has been installed somewhere along the way. Can't find any documentation about it, however.

---

### Post by nebileix on 2011-04-28
> **piergen said:**
> Hmm how can that be? All the fsck seems fine. I can access all my files. 
The samba shares works fine, and the two vm's that run under vmware are fine. 
Something messed up one file, how can that be related to the raid?

Great to hear that u solve the ICEauthority problem.

Your file system was not force to check previously. That why it dun check those which are clean. Where u force check on the second attempt, then it found the problem.

It could be raid related as your data is split or mirror across multiple disk(didnt really know what raid u used), therefore, the sync might have error on that particular file when u had that power failure. *Maybe someone with more knowledge on that could explain or u can go read about it.

---

