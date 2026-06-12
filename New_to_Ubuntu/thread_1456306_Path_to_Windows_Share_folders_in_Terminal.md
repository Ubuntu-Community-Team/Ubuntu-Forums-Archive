---
title: "Path to Windows Share folders in Terminal"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Rocket J Squirrel on 2010-04-17
In Terminal, what's the format for a path to a Windows folder? I can see the mounted folders in Nautilus but can't figure out how to ls them or cp files to them in Terminal.

---

### Post by Paqman on 2010-04-17
It's just the path to whatever point in the filesystem you've mounted them to. If they're showing up on your desktop that'll be in /media

---

### Post by IndyGunFreak on 2010-04-17
> **Rocket J Squirrel said:**
> In Terminal, what's the format for a path to a Windows folder? I can see the mounted folders in Nautilus but can't figure out how to ls them or cp files to them in Terminal.

Another thing you can do... Open a terminal, and Navigate Nautilus to the folder you want to know the path to... Drag/Drop either the folder, or a file that's in the folder, into the terminal, and the path will come up.  Obviously if you drop a file, the file name will be on the end of the path, but I'm sure you get the point.

IGF

---

### Post by undecim on 2010-04-17
Just because you can see the disks in nautilus doesn't mean they are mounted. Click on them in nautilus to mount them, then they should show up in /media/

---

### Post by Rocket J Squirrel on 2010-04-17
Thanks, all.

/media only shows two cdroms

But if I drag and drop a folder from Nautilus into a Terminal I find this path:

'/home/jackelliott/.gvfs/mikeother on diskstation/folder1'

It works, I can $ ls '/home/jackelliott/.gvfs/mikeother on diskstation/folder1' and see the contents. 

What's up with that .gvfs directory?

---

### Post by HermanAB on 2010-04-17
Nautilus is trying to be helpful and makes a temporary mount point for you.

To see what is mounted:
$ mount

To see what is in /media:
$ ls /media

---

### Post by 3rdalbum on 2010-04-17
> **Rocket J Squirrel said:**
> Thanks, all.

/media only shows two cdroms

But if I drag and drop a folder from Nautilus into a Terminal I find this path:

'/home/jackelliott/.gvfs/mikeother on diskstation/folder1'

It works, I can $ ls '/home/jackelliott/.gvfs/mikeother on diskstation/folder1' and see the contents. 

What's up with that .gvfs directory?

Gnome mounts things in ~/.gvfs, because that's the name of the subsystem that provides its virtual filesystems (GVFS).

---

### Post by Rocket J Squirrel on 2010-04-17
Everyone: thanks for pitching in here and helping me figure this out. It's not quite sorted, though. Here are things I am seeing:

1. A mounted Windows share shows up on my desktop (see Desktop.png screenshot).

2. When I browse to the desktop in Nautilus, the shares are not displayed as being on the desktop (see Nautilus.png,) although they do show in the left pane, so maybe that's to avoid recursion or something. 

So leaving all that aside for a moment, 

3. **HermanAB**: _$ ls /media_ only shows two cdroms, and _$ mount_ does not show the mounted shares:

```
jackelliott@TheJackUbuntuNetbook:~$ ls /media
cdrom  cdrom0

jackelliott@TheJackUbuntuNetbook:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/jackelliott/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jackelliott)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```[B]
undecim[/B]: Thanks for the tip. The two folders are mounted as I can browse them in Nautilus yet, as can be seen above, mount does not display them. 
[B]
3rdalbum[/B], would we expect Gnome to mount things in .gvfs yet not be able to see them with the mount command?

---

### Post by mcduck on 2010-04-19
"mount" command doesn't include things that are mounted by other means than mount command itself (or that are defined in /etc/fstab).

So no, it's not even supposed to list shares mounted using gvfs. Still, as you can see, your Windows share *is* mounted, and it *is* accessible in ~/.gvfs, exactly like 3rdalbum suggested. It doesn't show in ~/Desktop because it's not there. Gnome just kindly gives you a desktop icon for easier access to the mounted share, just like you get icons for removable drives and CD's even though they aren't actually mounted into your desktop.

Ignore the "mount" stuff here, it's not relevant to this question, and people who have suggested that probably assumed that you had mounted your Windows share in /etc/fstab instead of using Gnome's ability to access network locations.

---

### Post by VCoolio on 2010-04-19
You can mount network shares to a folder of your choice like this:
```
sudo mount -t cifs //server/share /media/whereever -o guest,rwx,iocharset=utf8,file_mode=0777,dir_mode=0777
```
Make sure the mount point folder (/media/whereever in the above example) exists. You can use the /etc/fstab file to mount shares automatically.

---

### Post by Morbius1 on 2010-04-19
You can also create a symbolic link from the .gvfs directory to a "non hidden" directory.

mkdir /home/jackelliott/SMB
ls -s /home/jackelliott/.gvfs /home/jackelliott/SMB

[COLOR=Blue]EDIT:
[/COLOR][COLOR=Blue]Mr. Squirrel you are correct that was a sloppy typo. It should have been:

ln -s /home/jackelliott/.gvfs /home/jackelliott/SMB
[/COLOR] 
for example.

---

### Post by Crazedpsyc on 2010-04-19
if they aren't mounted you don't have to mount them, just use the location "smb://WORKGROUP/" unless you have renamed your windows workgroup. make sure you have Samba installed or this won't work. in windows go to the network information page which is linked form the main network page you can get to from your start menu.

---

### Post by Crazedpsyc on 2010-04-19
if they aren't mounted you don't have to mount them, just use the location "smb://WORKGROUP/" unless you have renamed your windows workgroup. make sure you have Samba installed or this won't work. in windows go to the network information page which is linked form the main network page you can get to from your start menu, and it will tell you the name of your workgroup.

---

### Post by Rocket J Squirrel on 2010-04-19
Thank you, everyone. A lot to digest here.

_Crazedpsyc_, I'm not sure I understand. My Windows workgroup is CCIRCLE and I can browse the network within Nautilus. But your suggestion isn't giving what I expect:
```

jackelliott@TheJackUbuntuNetbook:~$ ls smb://CCIRCLE/
ls: cannot access smb://CCIRCLE/: No such file or directory
```
I'm probably doing something wrong.

_Morbius1_, I like your symbolic link suggestion. I wasn't aware that ls had that option, man says that the -s option is for listing file sizes. 

_mcduck_, thanks for explaining.

_VCoolio_, quite a bit of CLI to study there. I also took a look at /etc/fstab and it looks formidable.

So, unless anyone is unclear on what I'm after here, I'm going to be writing a backup scrip that is meant to save the backup on a shared folder on a Windows network. It would be swell if the script could check that the share is up and running before doing the backup, and if not, mount the share. The whole thing will be a shell script so I reckon I need the full path to the share, which was the intent of this thread: what's the path, man?

Path man fever.

---

### Post by mcduck on 2010-04-19
> **Rocket J Squirrel said:**
> 
So, unless anyone is unclear on what I'm after here, I'm going to be writing a backup scrip that is meant to save the backup on a shared folder on a Windows network. It would be swell if the script could check that the share is up and running before doing the backup, and if not, mount the share. The whole thing will be a shell script so I reckon I need the full path to the share, which was the intent of this thread: what's the path, man?

Path man fever.
The full path is the one you have yourself posted here:

"/home/jackelliott/.gvfs/mikeother on diskstation/folder1"

To see if the share is mounted you can simply check if that directory exists. And to mount a share from a script using gvfs you'd use the "gvfs-mount"-command instead of "mount". Of course there's no reason why you'd *have to* use gvfs, you can just as well mount your share from /etc/fstab or manually/from a script with "mount" instead, it's just a question of what you prefer.

---

### Post by Rocket J Squirrel on 2010-04-19
Right, thanks, mcduck. .gvfs will work for me just fine. 

IRT the suggested symbolic link, I reckon that Morbius1 typoed "ln" into "ls". 

Out of curiosity, I ran 

```
jackelliott@TheJackUbuntuNetbook:~$ ln -s /home/jackelliott/.gvfs /home/jackelliott/SMB
```Which ran without error. But SMB appears to be empty:

```
jackelliott@TheJackUbuntuNetbook:~$ ls .gvfs
mikeother on diskstation  storage central on diskstation

jackelliott@TheJackUbuntuNetbook:~$ ls SMB
jackelliott@TheJackUbuntuNetbook:~$
```

---

### Post by Morbius1 on 2010-04-19
You're right that was a typo, should have been "ln -s". 

I use this method myself. Let me see if I can reproduce your problem.

---

### Post by Morbius1 on 2010-04-19
OK, my mistake - not having a good day here.

**ls -a SMB **will give you the listing. You need the -a because the link is to a hidden directory. So you haven't really gained anything.

Instead of this:
> ln -s /home/jackelliott/.gvfs /home/jackelliott/SMBTry this:
```
ln -s /home/jackelliott/.gvfs/"mikeother on diskstation" /home/jackelliott/SMB
```and 
```
ln -s /home/jackelliott/.gvfs/"storage central on diskstation" /home/jackelliott/SMB
```

---

### Post by Rocket J Squirrel on 2010-04-19
Thanks, Morbius1, your revised code gave the desired result. 

VCoolio, I tried your mount command with this result:

```
jackelliott@TheJackUbuntuNetbook:~$ sudo mount -t cifs //diskstation/._Jacks%20Ubuntu /home/jackelliott -o guest,rwx,iocharset=utf8,file_mode=0777,dir_mode=0777h

mount: wrong fs type, bad option, bad superblock on //diskstation/._Jacks%20Ubuntu,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg provided:

```
[37491.594716]  CIFS VFS: No username specified
[37491.594736]  CIFS VFS: cifs_mount failed w/return code = -22
```

man ln didn't give any info about username, and there isn't a man entry for CIFS. 

Bit by bit I will chip away at this. Thanks to all who have contributed suggestions!

---

### Post by VCoolio on 2010-04-20
Sorry Squirrel, if I have problems like that I mess around and read around (like you do now), but I'm not very good at debugging specific problems others have. But [here]("http://ubuntuforums.org/showthread.php?t=288534") is the link to a howto thread I used.

---

### Post by Rocket J Squirrel on 2010-04-20
Well, VCoolio, I do appreciate that you took a stab at it! Thanks for your help! And thanks for the link.

---

### Post by dazza5000 on 2012-01-11
> **IndyGunFreak said:**
> Another thing you can do... Open a terminal, and Navigate Nautilus to the folder you want to know the path to... Drag/Drop either the folder, or a file that's in the folder, into the terminal, and the path will come up.  Obviously if you drop a file, the file name will be on the end of the path, but I'm sure you get the point.

IGF

bro - this drag and drop tip is hot - thank you!

---

