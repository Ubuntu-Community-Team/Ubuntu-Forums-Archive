---
title: "Unable to initiate RSync: Source - QNAP -- Destination - FreeNAS"
date: 2019-07-12
forum: Networking &amp; Wireless
---

### Post by trumanhw2 on 2019-07-12
I'm unable to initiate Rsync at all actually - disregard the title. 

Goal -- Copy QNAP to ZFS (FreeNAS).

---

### Post by TheFu on 2019-07-12
```
$ **rsync** -avz {source} {target}
```
For many people, the easiest answer for rsync is to google "rsync examples" ; it is extremely flexible.

Of course, file and directory **permissions** need to allow reading from the source AND writing to the target. My first guess is that you are having a permissions issue.  There's no way around that problem other than to gain a clear understand of Unix file and directory permissions.  Google for "permissions tutor" ---- Unix, Linux, Ubuntu all use exactly the same permissions model so don't worry if the tutorial is for AIX, Solaris, HP-UX, SunOS, Irix, or any of the Linux variants.  It doesn't matter.  

With rsync, the source and target can either be local storage or remote storage.

There is a GUI for about 10% of what rsync can do, **grsync**.

---

### Post by SeijiSensei on 2019-07-12
Rsync is also a bit persnickety when it comes to defining the source and target.  Suppose you want to copy /home to server:/backup. 

```

cd /
rsync -av home server:/backup

```

If you use 
```

rsync -av home/ server:/backup

```
rsync will copy the individual files in home to the target, but not the directory itself. 

It's always good practice to use the "-n" or "--dry-run" switch before doing a transfer to see exactly which files will be copied.

Rsync has extensive documentation on its [man page]("https://linux.die.net/man/1/rsync").  Use "man rsync".

---

### Post by trumanhw2 on 2019-07-13
Thank you for the help. TRULY. 

Not having a SIMPLE mode is ... so brilliant. Keeps everything SO secure. Bc then -- I just randomly "copy paste" **** I dn't understand...

See? "Secure".  

I could literally make 80% of ALL forum topics for either ubuntu or freenas --** evaporate in 1-year** with two competent developers and my graphic designer. 
And a "real" budget of course. 

Like ONLY people with Asperger's -- devoid of any innate 'theory of mind' contribute to the UI / syntax / and rules. 

In fact, I'd make a beginner / intermediate and "full" version ... so that people didn't have to learn what a group was. What a GID is. and EVERY. other thing... to do ... ANYTHING, in any of these. 

Seriously. **These creators are *RETARDED* geniuses. **

---

### Post by TheFu on 2019-07-13
So, did you solve the issue?

I don't understand the last post.  The words don't fit into ideas I can understand.  Can't tell if you are frustrated or happy.  Groups are necessary for different people or userids to work together while preventing userids outside the group from having access.  EVERY multi-user OS since at least the 1960s has this idea.  The way that businesses solve this is by paying for admins to setup all this stuff for the users.  On Ubuntu, or any multi-user computing system, YOU are the administrator.  If you have multiple computers, then you are the administrator for each of them.  If they are all the same brand, running the same OS, they you would expect them to all work together fairly easily.  But you seem to have 3 different brands of computers running 3 different OSes.   To make them work together, you would want to pick protocols used by all 3 and ensure userids and groupids are mapped correctly between all 3 systems.  It isn't hard, if you setup the users with that in mind at the start.

rsync isn't the only method to accomplish what you've asked, but the initial post didn't contain many details where anyone could provide help.  People trying to help shouldn't have to pull information like a dentist.  Anyway, here goes.  
* which protocols are the storage systems using?  Do you have NFS, CIFS, or is iSCSI used?
* which userid and groups are available on each of the 3 systems?  The output from 'id' on each system is needed.
* what are the permissions for the source files and directories?  An **ls -al** for a few sample directories and files is needed for the source and target.

For example, I have to computers, hadar and istar.  istar is an NFS server.  Hadar is an NFS client.
```
tf@hadar:/D/ebooks$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
istar:/D        3.5T  3.5T   43G  99% /D

tf@hadar:/D/ebooks$ ls -al
total 220
drwxrwxr-x   6 tf tf   4096 May 17 23:32 ./
drwxrwxr-x   9 tf tf   4096 Jul  1 18:36 ../
drwxrwxr-x   3 tf tf   4096 Jan 15  2015 John Schember/
-rw-r--r--   1 tf tf   1030 Dec 13  2007 kindlepid.py
drwxrwxr-x 216 tf tf  12288 Jul  4 14:22 Library/


```
I've ensured that my userid, tf, maps 1-for-1 on both computers.
On hadar: 
```
$ id
**uid=1000(tf) gid=1000(tf)**
groups=1000(tf),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),110(lxd),116(libvirtd),117(lpadmin)
```

On istar:
```
tf@istar:~$ id
**uid=1000(tf) gid=1000(tf)**
groups=1000(tf),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),113(netdev),114(plex),126(libvirtd),128(hts),136(lxd)

```

See the uid 1000 and gid 1000 on both computers?  Those are the same on purpose.  All the other gids mapping isn't important though a case could be made that I should map the plex group on all systems. istar is my plex server, but it is also my Calibre server and NFS server.

On a laptop, posc:```

tf@posc:/home/tf$ id
[B]uid=1000(tf) gid=1000(tf)
[/B]groups=1000(tf),4(adm),24(cdrom),27(sudo),30(dip),44(video),46(plugdev),109(netdev),113(lpadmin),129(sambashare),131(libvirtd)
```
Again see how the uid and gid are both 1000?  When on the home network, it also can access istar's NFS storage.

The fact that the uid=1000 and the gid=1000 is purely coincidence.  The gid could be 1050 or any number between 500 and perhaps 32,000.  Same for the uid.  Those are not specifically tied together, it is just that in Ubuntu the system begins with a uid of 1000 and counts up by 1 for each new userid.  Same goes for the gid assigned to people.  Groups created by packages tend to be below 500, but that isn't important. I never assume any specific number for a group created by a package or installer.

The trick to NFS is having the uid and gid map 1 for 1 across the systems.  There was an attempt to setup a mapping file between systems with NFSv4, but I don't know any one who got that working.   Inside a business, userids and groups are almost always centrally managed using some sort of LDAP, which means there isn't any need to manually make the userids and groupids map across systems. 

I'm pushing the use of NFS here because it is the native and fastest file sharing protocol for general use between Unix systems. It supports native permissions which are extremely important especially if you expect backups to work.

---

### Post by SeijiSensei on 2019-07-13
If you are encountering permissions issues, run rsync as root with sudo.

---

### Post by TheFu on 2019-07-13
sudo might not help with NFS.  By default, remote root accounts don't gain any privileges.  It will help if you've specifically setup ssh between the 2 systems with ssh-keys.  Really, without knowing which protocol the storage is using, we are only guessing ... and spinning our "I wanna help" wheels.

---

### Post by SeijiSensei on 2019-07-13
I generally do TCP transfers like "rsync source server:/directory".  I use NFS but not for backups.

---

### Post by TheFu on 2019-07-13
> **SeijiSensei said:**
> I generally do TCP transfers like "rsync source server:/directory".  I use NFS but not for backups.

+1. Me too, except I tend to "pull" the files, not push them.

---

### Post by trumanhw2 on 2019-07-18
[FONT=book antiqua][SIZE=2]I agree ... I'm can always work on my 'concept' of permissions. 
I'll read up on them after replying to messages today -- though I don't think that's the issue here. 


configured - rsync Daemon on QNAP
allowed+specified - username + password on QNAP 
 
FreeNAS account is consistent with above account on FreeNAS RSync page.  
Trying to copy entire-volume to avoid* any* complexity arising from 'specificity'


I found a thread in which someone discussed creating a password (& log) file as follows:
[/SIZE][/FONT]

[SIZE=1]'--password-file=/mnt/IBM50/ZFS/truman/rsinfo/rsync.pwd --log-file=--password-file=/mnt/IBM50/ZFS/truman/rsync_info/logfile.log'




I click to start it -- and of course, since there's no indices that it's working I look to see if there's any change in the data within the target folder, and there isn't. 

I really have no idea what I should try at this point. [/SIZE]

---

### Post by trumanhw2 on 2019-07-18
Oh - and when trying to start the daemon on FreeNAS to use terminal instead of their GUI ...

'failed to create pid file /var/run/rsyncd.pid file exists'

---

### Post by TheFu on 2019-07-18
At some point, will you provide the exact command, mounts and permissions on both source/targer so someone might see the issue?
My tea leaves aren't showing enough information.

---

