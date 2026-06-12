---
title: "editing fstab to mount network ntfs drive at startup"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by ukmh on 2006-10-06
I'm trying to mount an ntfs network drive at startup. My machine is running Dapper, the networked machine is running XP.
I have read & followed the guides within this thread:
[http://www.ubuntuforums.org/showthread.php?t=248656&highlight=mount+network+windows+drive](http://www.ubuntuforums.org/showthread.php?t=248656&highlight=mount+network+windows+drive)

But still get this error message:
wrong fs type, bad option, bad superblock on //192.168.15.50/Data,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

The windows machine contains 2 physical drives, the second drive is split in 2 logical drives [in windows speak - Windows (C)  Data (D)  Download (E)]
The drive I am trying to mount is Data (D). I can see the drive fine from Ubuntu, even access it (full read/write, all fine) but can't get it to mount at startup.
Here is the relevant fstab line I'm using:
//192.168.15.50/Data    /media/Data smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
I'm wondering if this line is wrong with regard to the //ipaddress/directory part (although IP is correct and I already tried the directory as Data (D) but ubuntu didn't like the space in that name.

If anyone could suggest anything or tell me where I have gone blitheringly wrong I would be most grateful.
Matt.

---

### Post by rccharles on 2006-10-07
> **ukmh said:**
> 
wrong fs type, bad option, bad superblock on //192.168.15.50/Data

This is a big guess, but doesn't Windows handle casing differently than Linux?

Maybe there is something wrong with the casing of Data?  

Did you try the mount command?

Robert

---

### Post by rccharles on 2006-10-07
> **rccharles said:**
> 
Maybe there is something wrong with the casing of Data?  


I'd try all upper case DATA and all lower case data

I am guessing...

Robert

---

### Post by ukmh on 2006-10-12
rccharles - thx very much for the suggestion. I'll try that as soon as I get time.

---

### Post by dannyboy79 on 2006-10-12
> **ukmh said:**
> I'm trying to mount an ntfs network drive at startup. My machine is running Dapper, the networked machine is running XP.
I have read & followed the guides within this thread:
[http://www.ubuntuforums.org/showthread.php?t=248656&highlight=mount+network+windows+drive](http://www.ubuntuforums.org/showthread.php?t=248656&highlight=mount+network+windows+drive)

But still get this error message:
wrong fs type, bad option, bad superblock on //192.168.15.50/Data,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

The windows machine contains 2 physical drives, the second drive is split in 2 logical drives [in windows speak - Windows (C)  Data (D)  Download (E)]
The drive I am trying to mount is Data (D). I can see the drive fine from Ubuntu, even access it (full read/write, all fine) but can't get it to mount at startup.
Here is the relevant fstab line I'm using:
//192.168.15.50/Data    /media/Data smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
I'm wondering if this line is wrong with regard to the //ipaddress/directory part (although IP is correct and I already tried the directory as Data (D) but ubuntu didn't like the space in that name.

If anyone could suggest anything or tell me where I have gone blitheringly wrong I would be most grateful.
Matt.

This link has helped every single person I have given it to. In fact someone even copied the whole thing and pasted it into the ubuntu forums. It just works. Check it out. [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by shakma on 2007-02-08
Hi!  Old-ish thread, but I have a partial solution.

I was getting the same message, and it turned out I didn't have the "smbfs" package installed!

Search Synaptic for "smbfs" and mark the Ubuntu approved one.  

Now, however, I get the message:

jon@edubuntu:~$ sudo mount -t smbfs //saint/APPS/ /home/teacher/saint/ -o credentials=/home/jon/.smbpasswd 
5492: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

I (jon) am the "admin" as it were here at work, and I'm trying to mount the Windows share to the general (teacher) account.  Any advice?  

P.S.  The *actual* Windows share I want to mount has a space in the name!  ("Teacher Docs")  Any advice on dealing with such a name (other than renaming the Windows directory, which I can't do) would be MUCH appreciated!

Peace.

---

### Post by rccharles on 2007-02-08
> **shakma said:**
> 
Now, however, I get the message:

jon@edubuntu:~$ sudo mount -t smbfs //saint/APPS/ /home/teacher/saint/ -o credentials=/home/jon/.smbpasswd 
5492: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

I (jon) am the "admin" as it were here at work, and I'm trying to mount the Windows share to the general (teacher) account.  Any advice?  

P.S.  The *actual* Windows share I want to mount has a space in the name!  ("Teacher Docs")  Any advice on dealing with such a name (other than renaming the Windows directory, which I can't do) would be MUCH appreciated!

Peace.

Did you try the GUI interface?

places > network servers  

.....

You could try putting quotes around "Teacher Docs" when you use the mount command.

Robert

---

