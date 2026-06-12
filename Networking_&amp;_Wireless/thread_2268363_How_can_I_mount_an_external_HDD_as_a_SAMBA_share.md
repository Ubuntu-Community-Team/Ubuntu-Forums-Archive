---
title: "How can I mount an external HDD as a SAMBA share?"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2015-03-08
Afternoon, everybody.

*Mods; if this is in the wrong forum, please feel free to re-locate. Thanks!*

I've been running Ubuntu 14.04 LTS for almost a year, and have been Windows-free for all that time.

With bab1's help a few months ago, I got SAMBA up-and-running. I'm not using it for Windows sharing; it's being used between 2 Linux boxes (the other one running Puppy Linux); but since Puppy has a SAMBA client built-in, I just thought it was the easiest way to go.....and it works beautifully.

Now; I have an external 500 GB Seagate HDD, permanently installed as part of the system. It's always plugged-in, and never gets disconnected.....in fact, it's 'fixed' to the top of my tower.

I would like to be able to mount the Seagate as a SAMBA share. I've used the share '/media/paul/Seagate#1', which is the path shown in Nautilus for it; but Ubuntu says the drive doesn't exist! Which is strange, as it's constantly in use, and shows up perfectly under the Samba-TNG share set-up I have between 2  Puppy boxes (I'm dual-booting with Puppy on this Compaq desktop, and have Puppy on another laptop.

The share I have set for it in /etc/samba/smb.conf is as follows:-

```
[Seagate#1]        
        comment = Seagate HDD
        path = /media/paul/Seagate#1
        writeable = yes
;       browseable = yes
        valid users = paul
```

Doing a bit of research, I find that I may need to have the 'ntfs-3g' driver installed, for this to work? Or am I projecting here.....since Ubuntu obviously DOES 'see' it, as & when it's accessed on a regular basis through Nautilus?

Any advice on this one would be appreciated. :)


Regards,

Mike.

---

### Post by TheFu on 2015-03-08
Is the USB drive formatted NTFS or with a Linux file system?
Is the USB drive mounted through the /etc/fstab - it should be. I'd avoid mounting it under the /media location and I'd avoid using "#" in the name or the location. Funny characters have a way of screwing things up.

Then you can add a stanza to the /etc/samba/smb.conf to share it as you like.

---

### Post by Mike_Walsh on 2015-03-08
@ TheFu:-

Thanks for the suggestion. I agree, you're probably right about the use of 'funny' characters.....but 'Seagate#1' is what Ubuntu itself named the drive, the day it was installed; and since it works like that, I've simply left it alone. 

'If it ain't broke, etc...'

The drive is formatted as NTFS; it's a holdover from my Win XP days (which I waved bye-bye to nearly a year ago now, without shedding a single tear!).....but it does contain several hundred GB's of data which I do NOT want to lose. Since I don't have a larger drive , or one of equivalent size, I can't transfer the data, re-format, and transfer everything back; haven't got the space currently.

I've had a look in /etc; I appear to have TWO fstabs. one is simply fstab, and the other is fstab. (with a dot after it). Is that normal? Regardless, the Seagate is not mounted in either of them, so....what would you suggest as the next step?


Regards,

Mike. :)

---

### Post by TheFu on 2015-03-08
There is no "ubuntu itself" - there's the way it has been done for 30 yrs, then there are some new ways that us old-timers don't like (gvfs) which isn't fully implemented to work with everything the OS can do.  I think THAT is the issue you are having.

I have no idea why you'd have a "fstab." - that is not the file that matters. Ignore it completely. It does not mean anything to the system.  Close enough doesn't work usually with linux - either is it exactly correct or it is wrong and ignored regardless of what a human may see.

Next steps:
> Is the USB drive mounted through the /etc/fstab - it should be. I'd avoid mounting it under the /media location and I'd avoid using "#" in the name or the location. Funny characters have a way of screwing things up.

Then you can add a stanza to the /etc/samba/smb.conf to share it as you like. 

---

### Post by bab1 on 2015-03-08
> **Mike_Walsh said:**
> Afternoon, everybody.

*Mods; if this is in the wrong forum, please feel free to re-locate. Thanks!*

I've been running Ubuntu 14.04 LTS for almost a year, and have been Windows-free for all that time.

With bab1's help a few months ago, I got SAMBA up-and-running. I'm not using it for Windows sharing; it's being used between 2 Linux boxes (the other one running Puppy Linux); but since Puppy has a SAMBA client built-in, I just thought it was the easiest way to go.....and it works beautifully.

Now; I have an external 500 GB Seagate HDD, permanently installed as part of the system. It's always plugged-in, and never gets disconnected.....in fact, it's 'fixed' to the top of my tower.

I would like to be able to mount the Seagate as a SAMBA share. I've used the share '/media/paul/Seagate#1', which is the path shown in Nautilus for it; but Ubuntu says the drive doesn't exist! Which is strange, as it's constantly in use, and shows up perfectly under the Samba-TNG share set-up I have between 2  Puppy boxes (I'm dual-booting with Puppy on this Compaq desktop, and have Puppy on another laptop.

The share I have set for it in /etc/samba/smb.conf is as follows:-

```
[Seagate#1]        
        comment = Seagate HDD
        path = /media/paul/Seagate#1
        writeable = yes
;       browseable = yes
        valid users = paul
```

Doing a bit of research, I find that I may need to have the 'ntfs-3g' driver installed, for this to work? Or am I projecting here.....since Ubuntu obviously DOES 'see' it, as & when it's accessed on a regular basis through Nautilus?

Any advice on this one would be appreciated. :)


Regards,

Mike.

Hi @Mike_Walsh and @TheFu,

I'd like to chime in here.  I'm feeling verbose this morning.  I'll try and address some of the issues here.

The device (external 500 GB Seagate HDD) is not what is mounted to the local machines file system.  The partition on the drive isn't what is mounted either, although most folks talk about "mounting the partition.  The file system on the partition is what is mounted into the existing local machines file system at a mount point  The ntfs-3g module (driver) is what is used to translate NTFS style file system methods to Linux.  The ntfs-3g package is installed by default on Ubuntu.

How the local file system is mounted might be of some importance, but only in the context of the options used.  You can mount the file system with the options of your choice using the mount command (mount -t ntfs etc) or via fstab (the conf file for the mount command) or by *udev* which uses the options the Gnome devs think is best.  They all use the mount command however so it might not be such a big deal in the long run.  The best way to tell is to look at how it is mounted now.  Pos the output of this command from the Ubuntu terminal```
mount
```...Note that this all has to do with the local machines file system.  

The remote mounting of the designated directory via Samba is something else again.  In this instance you are mounting a portion of the remote hosts file system to the machine you are at.  This could be the Puppy Linux machine.  In this case the mount command would use the mount.cifs routines (mount -t cifs). and NOT the ntfs-3g routines.  In this instance the method to mount the file foreign file system uses *mount*   via fstab or the CLI *mount* command or via ***gvfs*** which also uses the mount command.  The difference is in the options used.

All of this is to say we are talking about 2 distinct different issues; local file system mounts and remote host file system mounts.  In addition you are using 2 different SMB/CIFS applications that are not always compatible.  I believe that Samba is compatible with Samba-TNG but not the other way around.  I would configure Samba and forget about Samba-TNG.

I agree with what @TheFu says about using strange characters in your directory name.  I don't think you should use that character in the share name either.  It's just more consistent to stick to letters and numbers.

Let's see what is going on here with Samba.  From the Ubuntu host post the output of ```
smbtree -d3
```

Sorry for the long winded post.  I am writing also for all the others that make read this at a later date.

---

### Post by bab1 on 2015-03-08
> **Mike_Walsh said:**
> 

The drive is formatted as NTFS; it's a holdover from my Win XP days (which I waved bye-bye to nearly a year ago now, without shedding a single tear!).....but it does contain several hundred GB's of data which I do NOT want to lose. Since I don't have a larger drive , or one of equivalent size, I can't transfer the data, re-format, and transfer everything back; haven't got the space currently.

I've had a look in /etc; I appear to have TWO fstabs. one is simply fstab, and the other is fstab. (with a dot after it). Is that normal? Regardless, the Seagate is not mounted in either of them, so....what would you suggest as the next step?


Regards,

Mike. :)
Leave the drive alone for right now.  You can mount it via Samba with not problems.  You may have to manually mount it or via fstab but NTFS drives are not a problem for Samba.

Don't worry about the second fstab file either.  That may have been form what we did earlier.  We can deal with that later on.  I usually have folks make a backup of fstab as smb.conf.bak or some such.

---

### Post by Mike_Walsh on 2015-03-08
Hallo, bab1. Sorry to be a while getting back to you; it being the weekend, and my niece's wedding coming up next week, and the garden needs a sort-out.....need I go on?

Now then; you've asked me for two outputs. Firstly, the output of 

```
 mount 
```

is as follows:-

```
paul@mic-w:~$ mount/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=paul)
/dev/sdf1 on /media/paul/Slacko 5.7 type ext3 (rw,nosuid,nodev,uhelper=udisks2)
paul@mic-w:~$  
```


I hope that means more to you than it does me! I'm guessing it's got SOMETHING to do with permissions, but as for the rest of it.....

And secondly, the output from

```
 smbtree -d3 
```

is as follows:-

```
 paul@mic-w:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: Ignoring invalid value 'share' for parameter 'security'
added interface eth0 ip=192.168.1.67 bcast=192.168.1.255 netmask=255.255.255.0
Enter paul's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
Connecting to 192.168.1.67 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
Connecting to 192.168.1.67 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\MIC-W          		mic-w
resolve_lmhosts: Attempting lmhosts lookup for name MIC-W<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MIC-W<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MIC-W<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\MIC-W\Mike's-Stuff   	
		\\MIC-W\WorkForce320@192.168.1.65	EPSON-Epson-Stylus-SX218
		\\MIC-W\EPSON-Epson-Stylus-SX218	EPSON Epson Stylus SX218
		\\MIC-W\WorkForce320   	EPSON-Epson-Stylus-SX218
		\\MIC-W\print$         	Printer Drivers
		\\MIC-W\Documents      	General Docs.
		\\MIC-W\Mike's Stuff   	Mike's Stuff!
		\\MIC-W\Pictures       	Piccies!
		\\MIC-W\Videos         	Vidz!
		\\MIC-W\HomeShare      	Collection
		\\MIC-W\New 'buntu Wallpapers	New 'papers
		\\MIC-W\Home           	Home Folder
		\\MIC-W\Seagate#1      	Seagate HDD
		\\MIC-W\IPC$           	IPC Service (mic-w)
PUPGROUP
resolve_lmhosts: Attempting lmhosts lookup for name PUPGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name PUPGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name PUPGROUP<0x1d>
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
	\\PUPSERVER:D    		Puppy Samba-TNG Server
resolve_lmhosts: Attempting lmhosts lookup for name PUPSERVER:D<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PUPSERVER:D<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PUPSERVER:D<0x20>
resolve_hosts: getaddrinfo failed for name PUPSERVER:D [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PUPSERVER:D<0x20>
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
Segmentation fault (core dumped)
paul@mic-w:~$
```


PUPSERVER is the name of the Samba-TNG server on the Puppy laptop, in case you're wondering. My Compaq desktop is dual-booting Ubuntu AND Puppy. When I use the laptop (which runs Puppy), I normally run Puppy on the Compaq, too.....and I have both boxes set up as server AND client, so I can use them whichever way round I want. It's only because the way the Puppy devs have set up Samba-TNG to work, it's an absolute piece of cake to get it running. Hope that makes THAT clear.

Over to you...


Regards,

Mike. ;)

---

### Post by Mike_Walsh on 2015-03-08
Hi again, bab1.

Thought you might just be interested to see the smb.conf file from Puppy's Samba-TNG server.
It's minute compared to regular SAMBA.

```
 [global]dns proxy = no
max log size = 50
domain master = no
domain logons = no
workgroup = pupgroup
netbios name = pupserver
server string = Puppy Samba-TNG Server
security = user
;map to guest = Bad Password
;printcap name = cups
load printers = yes


[Pupshare:C]
path = /root
writable = yes


[printers]
path = /tmp
printable = yes
guest ok = yes


[Seagate:C]
path = /mnt/sdb1
read only = yes


[Home:C]
path = /mnt/sda3
read only = yes
```


And that's ALL there is to it! It's a modified version of Samba-TNG, cut down to suit the minimal coding requirements of the Puppy devs.....and it's the work of a gentleman from Stratford, Ontario, in Canada; goes by the handle of rcrsn51. He's a 'regular' of long-standing on the Puppy Forums, and specialises in networking, wireless, and printing. And he's damn good at what he does...!

Anyway, there you have it. SO simple...yet it works, and does all I ask of it. It allows me to access Puppy's root folder, the external Seagate, and my /home partition in Ubuntu.

BTW; I'd forgotten about the earlier 'fun & games' when we set SAMBA up originally. We DID set a backup of 'smb.conf'....that probably IS where the second one's come from.


Regards,

Mike. :)

---

### Post by bab1 on 2015-03-08
> **Mike_Walsh said:**
> Hallo, bab1. Sorry to be a while getting back to you; it being the weekend, and my niece's wedding coming up next week, and the garden needs a sort-out.....need I go on?

Now then; you've asked me for two outputs. Firstly, the output of 

```
 mount 
```

is as follows:-

```
paul@mic-w:~$ mount

gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse [COLOR="#FF0000"](rw,nosuid,nodev,user=paul)[/COLOR]

paul@mic-w:~$  
```

I hope that means more to you than it does me! I'm guessing it's got SOMETHING to do with permissions, but as for the rest of it.....

The above (in red) is the mount parameters for the USB connected Disk.  Who is paul?  Post the output of ```
df -h
```
> 
And secondly, the output from

```
 smbtree -d3 
```

is as follows:-

```
 paul@mic-w:~$ smbtree -d
...
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\MIC-W          		mic-w
resolve_hosts: Attempting host lookup for name MIC-W<0x20>

NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	
	[COLOR="#0000FF"]**	\\MIC-W\Seagate#1      	Seagate HDD**[/COLOR]
		\\MIC-W\IPC$           	IPC Service (mic-w)
PUPGROUP
resolve_lmhosts: Attempting lmhosts lookup for name PUPGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name PUPGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name PUPGROUP<0x1d>
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
[COLOR="#FF0000"]cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
	\\PUPSERVER:D    		Puppy Samba-TNG Server

cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE[/COLOR]

paul@mic-w:~$
```
The above in blue shows the Seagate HDD with the NTFS file system.  It's mounted and visible.  The above in red shows the attempted login to PUPSERVER:D that fails due to...; who knows at this point??  I can tell you that if you can't login then you won't be able to view the share.  My best guess is that the user is not a PUBSERVER:D user or a Samba-TNG user on that machine.  Therefore the user can't login.  But I don't know that for sure.  Once again, who is Paul (not the Walrus).

I'm not sure if this will work from PUPSERVER:D but it is worth a try.  Post the output of this (if sudo doesn't work then you must be root)```
sudo pdbedit -L

```

In any event you have a login failure not a disk configuration failure.  he user on Samba doesn't look like they have permissions.

I wonder what this looks like from the terminal of PUPSERVER:D.  From that terminal post the output of```
smbtree -d3
```

---

### Post by bab1 on 2015-03-08
> **Mike_Walsh said:**
> Hi again, bab1.

Thought you might just be interested to see the smb.conf file from Puppy's Samba-TNG server.
It's minute compared to regular SAMBA.

```
 [global]dns proxy = no
max log size = 50
domain master = no
domain logons = no
workgroup = pupgroup
netbios name = pupserver
server string = Puppy Samba-TNG Server
security = user
;map to guest = Bad Password
;printcap name = cups
load printers = yes


[Pupshare:C]
path = /root
writable = yes


[printers]
path = /tmp
printable = yes
guest ok = yes


[Seagate:C]
path = /mnt/sdb1
read only = yes


[Home:C]
path = /mnt/sda3
read only = yes
```


And that's ALL there is to it! It's a modified version of Samba-TNG, cut down to suit the minimal coding requirements of the Puppy devs.....and it's the work of a gentleman from Stratford, Ontario, in Canada; goes by the handle of rcrsn51. He's a 'regular' of long-standing on the Puppy Forums, and specialises in networking, wireless, and printing. And he's damn good at what he does...!

Anyway, there you have it. SO simple...yet it works, and does all I ask of it. It allows me to access Puppy's root folder, the external Seagate, and my /home partition in Ubuntu.

BTW; I'd forgotten about the earlier 'fun & games' when we set SAMBA up originally. We DID set a backup of 'smb.conf'....that probably IS where the second one's come from.


Regards,

Mike. :)
Most of what is in the smb.conf file on Ubuntu is documentation or slight tweaking of the default parameters.  IDK what the default params are for Puppy, but you can create a 5 line 1 share smb.conf file for Ubuntu and it will work.  The devs just decided it would be better to leave in all the comments.

The parameter *security = user* may be part of the problem along with commenting out this: *;map to guest = Bad Password*.  If the directory permissions are wrong then no login and no guest logins allowed.  Also, the parameter *security = share* is not used anymore.  You can see the complaint in the first few lines of the smbtree output

Post the output of > ls -l /mnt

---

### Post by Mike_Walsh on 2015-03-08
Hi again, bab1.

'Paul' is me! Mike's my first name, but the family have never used it.....always used my middle name, which is Paul. Confuses the HELL out of people.....

Quite possibly the log-in attempt failed at that particular point in time because the Pupserver wasn't running. The peculiarity of my old Dell laptop is that although the TP-Link wireless adapter that I use does indeed work very well, it doesn't auto-connect; I have to manually get things going at the start of a session. I've pretty much got into a routine for doing that, but I also have to remember to start Samba-TNG, too! The gentleman from Ontario has written an autostart script for Samba-TNG, but it does rather depend on the connection being up & running... 

Go figure.

I'm turning in for the night; it's after 1 am here in the UK, and I've got an early start in the morning. However, if you're about tomorrow, I'll get those outputs back to you ASAP. The Puppy terminal doesn't use 'sudo', despite 'Tahrpup' being based on 'Trusty'; the oddity of Puppy is that the user runs as root ALL the time, yet it's reckoned to be PERFECTLY safe. It's not a true multi-user O/S, unlike most Linux systems. Sounds strange, doesn't it?

Have a look at this, and you'll see what I mean...

[http://puppylinux.com/technical/root.htm](http://puppylinux.com/technical/root.htm)

I'll catch you tomorrow; apologies for abandoning you right in the middle of things! Talking of which, when's the best time to catch you? It gets a wee bit confusing, figuring out the difference in time zones...! I need to add about 8-9 hours onto whenever suits you..... Great living in an interconnected world, ain't it? :lol:


Regards,

Mike. ;)

---

### Post by bab1 on 2015-03-08
> **Mike_Walsh said:**
> Hi again, bab1.

'Paul' is me! Mike's my first name, but the family have never used it.....always used my middle name, which is Paul. Confuses the HELL out of people.....

Quite possibly the log-in attempt failed at that particular point in time because the Pupserver wasn't running. The peculiarity of my old Dell laptop is that although the TP-Link wireless adapter that I use does indeed work very well, it doesn't auto-connect; I have to manually get things going at the start of a session. I've pretty much got into a routine for doing that, but I also have to remember to start Samba-TNG, too! The gentleman from Ontario has written an autostart script for Samba-TNG, but it does rather depend on the connection being up & running... 

Go figure.


Two things come to mind... 
1.  Sometimes the computer problem is the operator
2.  This doesn't seem to show how Puppy is simple to me
> 

I'm turning in for the night; it's after 1 am here in the UK, and I've got an early start in the morning. However, if you're about tomorrow, I'll get those outputs back to you ASAP. The Puppy terminal doesn't use 'sudo', despite 'Tahrpup' being based on 'Trusty'; the oddity of Puppy is that the user runs as root ALL the time, yet it's reckoned to be PERFECTLY safe. Sounds strange, doesn't it?

Have a look at this, and you'll see what I mean...

[http://puppylinux.com/technical/root.htm](http://puppylinux.com/technical/root.htm)

I'll catch you tomorrow; apologies for abandoning you right in the middle of things! Talking of which, when's the best time to catch you? It gets a wee bit confusing, figuring out the difference in time zones...!


Regards,

Mike. ;)
I have friends in Liverpool so I go through this all the time.  I live in GMT -8.  I have to get up early for the Rugby matches.

The link to Puppy's explanation of their use of for the root user is interesting.  It doesn't minimize the security implications of using root for general use.  In fact it shows that the implications are the same as any other distro.  If not there would be no use for the users *spot* and *fido*.  Fido is nothing more than an unprivileged user in any other Linux installation.  Spot is a user that has applications run and less privileged.  The typical distro just has you login as an unprivileged user and use sudo or su if you want to run something as root.  You need root powers far less than you think.  But six of anything to some is a half dozen to others.

I'm so used to Debian/Ubuntu that I don't even think about other distro solutions.  So who am I to talk to the point anyway.  I'll admit it, I'm biased.  :-)

Send the info and we can comment.

---

### Post by Mike_Walsh on 2015-03-09
Evening, bab1.

Sorry for the delay; busy, busy, busy.....

Now, then: output of 

```
 df-h 
```

is as follows:-

```
paul@mic-w:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   17G   31G  36% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G   12K  1.5G   1% /dev
tmpfs           295M  1.2M  294M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G   84K  1.5G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sda3        59G   42G   15G  75% /home
/dev/sdg1       7.1G  4.7G  2.1G  70% /media/paul/Slacko 5.7
/dev/sdf5        50G   52M   47G   1% /media/paul/ec714e0c-c94f-4860-9f46-1afd5d5839e5
/dev/sdf1       250G  111G  140G  45% /media/paul/Seagate #1
paul@mic-w:~$ 
```

As for the other two, bear with me and we'll see if there's any output from Puppy...

Huh. Rather what I suspected. Output of

```
pdbedit -L [COLOR=#ff0000]or[/COLOR]
(sudo pdbedit -L)
```

gives

```
 bash: pdbedit -L: command not found [COLOR=#ff0000]or[/COLOR]
(sudo: pdbedit -L: command not found)
```

I'll confess, at this stage I know very little of bash for day-to-day usage (except what I use for installing stuff, or doing updates, etc.), so.... I'm none the wiser as to whether Puppy uses a different version..... 

I'll try the other one:-

```
 smbtree -d3 [COLOR=#ff0000]or[/COLOR]
(sudo smbtree -d3)
```

gives, again:-

```
 bash: smbtree -d3: command not found [COLOR=#ff0000]or[/COLOR]
(sudo: smbtree -d3: command not found)
```

So; I don't know what you were hoping to find out, but I can't help you on that score, unfortunately.

What ought we to try next, d'you think?


Regards,

Mike.:confused:

---

### Post by bab1 on 2015-03-09
> **Mike_Walsh said:**
> Evening, bab1.

Sorry for the delay; busy, busy, busy.....

Now, then: output of 

```
 df-h 
```

is as follows:-

```
paul@mic-w:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   17G   31G  36% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G   12K  1.5G   1% /dev
tmpfs           295M  1.2M  294M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G   84K  1.5G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sda3        59G   42G   15G  75% /home
/dev/sdg1       7.1G  4.7G  2.1G  70% /media/paul/Slacko 5.7
/dev/sdf5        50G   52M   47G   1% /media/paul/ec714e0c-c94f-4860-9f46-1afd5d5839e5
/dev/sdf1       250G  111G  140G  45% /media/paul/Seagate #1
paul@mic-w:~$ 
```

Note the local mount of the Seagate drive is this ```

/dev/sdf1       250G  111G  140G  45% /media/paul/[COLOR="#FF0000"]**Seagate #1**[/COLOR]
```...there is a space int the path at the end (in red)[

The share definition does not reflect that ```
[Seagate#1]        
        comment = Seagate HDD
        path = /media/paul/[COLOR="#0000CD"]**Seagate#1**[/COLOR]
        writeable = yes
;       browseable = yes
        valid users = paul
```...note that there is no space in the path (blue).  These have to match.  The share does not reflect the real path of the directory you are sharing.  Is it *_Seagate #1_* or *_Seagate#1_*.  I hate spaces for just this reason,

> 

As for the other two, bear with me and we'll see if there's any output from Puppy...

Huh. Rather what I suspected. Output of

```
pdbedit -L [COLOR=#ff0000]or[/COLOR]
(sudo pdbedit -L)
```

gives

```
 bash: pdbedit -L: command not found [COLOR=#ff0000]or[/COLOR]
(sudo: pdbedit -L: command not found)
```

I'll confess, at this stage I know very little of bash for day-to-day usage (except what I use for installing stuff, or doing updates, etc.), so.... I'm none the wiser as to whether Puppy uses a different version..... 

I'll try the other one:-

```
 smbtree -d3 [COLOR=#ff0000]or[/COLOR]
(sudo smbtree -d3)
```

gives, again:-

```
 bash: smbtree -d3: command not found [COLOR=#ff0000]or[/COLOR]
(sudo: smbtree -d3: command not found)
```

So; I don't know what you were hoping to find out, but I can't help you on that score, unfortunately.

What ought we to try next, d'you think?


Regards,

Mike.:confused:
This means that none of the diagnostic tools are supplied with Puppy.  I don't have any experience with the disto so I'm not much help in this area.  You have to either: change the name of the mounted directory to eliminate the space (e.g. Segate#1) or change the share definition to include a space.  I don't know if  that is possible as the space is what is use to denote the ending of the description.

Will this allow you remote access?  I don't know that either.  Normally Samba requires a Samba user and a Linux user or a Samba guest user has to be defined.  What is the Samba guest user in Puppy?

Try changing the directory name to Segate#1 and see what gives...

---

### Post by Mike_Walsh on 2015-03-09
Hi there. 

Oh, DEAR. What were you saying about the user sometimes being the problem? I hadn't noticed I'd done that; I sometimes wonder, as I get older, whether I am in fact slightly dyslexic...

Yes, you're right, of course. Spaces don't work very well for naming conventions in Linux. 'Seagate #1' is what Ubuntu defined it as the day I installed it, and, as I said near the start of the thread, since it's always worked, I've simply let well alone...

Okay. This is where I show my ignorance of bash. What's the way to rename a directory (in this case, the Seagate hard drive), via the terminal? I don't mind confessing ignorance, and am always happy to learn how things are done.


Regards,

Mike.

---

### Post by bab1 on 2015-03-09
> **Mike_Walsh said:**
> Hi there. 

Hah! What were you saying about the user sometimes being the problem? I hadn't noticed I'd done that; I sometimes wonder, as I get older, whether I am in fact slightly dyslexic...

Yes, you're right, of course. Spaces don't work very well for naming conventions in Linux. 'Seagate #1' is what Ubuntu defined it as the day I installed it, and, as I said near the start of the thread, since it's always worked, I've simply let well alone...

Okay. This is where I show my ignorance of bash. What's the way to rename a directory (in this case, the Seagate hard drive), via the terminal? I don't mind confessing ignorance, and am always happy to learn how things are done.


Regards,

Mike.

You are not changing the label of the Drive.  You are changing the name of a file system directory.  The directory you are sharing.  It happens to be the first (root) directory of the only partition on the physical drive.  

Show me the output of ```
ls -l /media/paul
```...this is the directory just above the Segate#1 directory.

---

### Post by TheFu on 2015-03-09
Having a normal user run as root on a networked OS is asking for trouble.  We've seen that from other vendors.  I will not use puppy due to this. I think DSL was the same - TinyCorePlus uses a different account with sudo capabilities (but tinycore uses a strange packaging/install solution).

Whenever I'm forced to use a different distro, that is when I really miss APT.

Spaces in mounts, directories, filenames, .... anything ... I convert to some other character too.  After all, How can we be positive it isn't "  " (2 spaces)?  Or a {tab}{space} or some other odd combination of unprintable characters?  I wasn't always of this belief, but after being burned a few times and wasting hours, days, weeks over something dumb like this - I don't do it anymore.  Much of what was trying to say initially (and in many other posts here) are my "best practices" ... not necessarily the only possible why that things can work.  Just because something "works", that doesn't mean it is a good idea.

---

### Post by Mike_Walsh on 2015-03-09
@ TheFu:-

I don't know whether you've had a look at the Puppy link, but Barry Kauler (the Australian developer of Puppy back in 2003) seems to be firmly of the opinion that if someone WANTS to hack your machine, they WILL find a way to do it, regardless of whatever you do to make it secure...

He's probably right. However, you CAN set passwords, or public keys, with the Puppy version of Samba-TNG; I haven't bothered, to be honest, since I'm simply using it between two boxes on a local area network, where I'm the only user anyway.....and the entire neighbourhood is 99% retirees, who have NO interest in hacking other people's machines.....


@ bab1:-

Okay. The output from

```
 ls -l /media/paul 
```

is as follows:-

```
 paul@mic-w:~$ ls -l /media/paultotal 32
drwxr-xr-x 3 root root  4096 Jan 27 00:04 ec714e0c-c94f-4860-9f46-1afd5d5839e5
drwx------ 1 paul paul 24576 Mar  6 20:38 Seagate #1
drwxr-xr-x 2 root root  4096 Mar  9 19:50 Slacko 5.7
paul@mic-w:~$ 
```


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-03-09
@bab1:-

Actually, now I think about it, that space has been there in Nautilus ever since about August last year; ever since I discovered about the tune2fs -L command, and did

```
 sudo tune2fs -L "Seagate #1" /dev/sdb1 
```

on it.....

So that's my OWN fault. I've NO idea WHY I put a space in there. And this, despite the fact that we don't use the '#' symbol for numbering in the UK..! I guess I must be 'picking up' on the large American user-base that Ubuntu has... :)


Regards,

Mike. :oops::D

---

### Post by bab1 on 2015-03-09
> **Mike_Walsh said:**
> @bab1:-

Actually, now I think about it, that space has been there in Nautilus ever since about August last year; ever since I discovered about the tune2fs -L command, and did

```
 sudo tune2fs -L "Seagate #1" /dev/sdb1 
```

on it.....


Regards,

Mike. :oops::D

I don't see how that would work.  Tune2fs is for ext partitions.  Have you formatted the drive partition ext4?

[COLOR="#0000FF"]Edit:  It would be what I would do.[/COLOR]

[COLOR="#0000FF"]Edit 2:  Here is what happens if you try and re-label a FAT partition[/COLOR]
```
 sudo tune2fs -L music-stick /dev/sdb1
tune2fs 1.42.9 (4-Feb-2014)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

```
[COLOR="#0000FF"]You just can't relabel any old partition.  The formatting determines what application you use.[/COLOR]

---

### Post by Mike_Walsh on 2015-03-09
@bab1:-

I know I did SOMETHING similar, although it might have been something different, too. I certainly won't argue the point; if you're positive it couldn't work, it MUST have been something different. I know I've used it to 'label' all of my Linux directories. I believe I found the solution that I DID use on askubuntu.com.....

Regardless, how can I go about getting rid of the space? I much prefer learning here on the forums, since y'all such a friendly & helpful bunch of folks..! :)


Regards,

Mike.

---

### Post by bab1 on 2015-03-09
> **Mike_Walsh said:**
> @bab1:-

I know I did SOMETHING similar, although it might have been something different, too. I certainly won't argue the point; if you're positive it couldn't work, it MUST have been something different. I know I've used it to 'label' all of my Linux directories. I believe I found the solution that I DID use on askubuntu.com.....

Regardless, how can I go about getting rid of the space? I much prefer learning here on the forums, since y'all such a friendly & helpful bunch of folks..! :)


Regards,

Mike.
What is the link to the solution you used before?  I'm curious.

---

### Post by TheFu on 2015-03-10
"linux label ntfs disk" - find a reputable source.
[http://manpages.ubuntu.com/manpages/oneiric/man8/ntfslabel.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/ntfslabel.8.html)

---

