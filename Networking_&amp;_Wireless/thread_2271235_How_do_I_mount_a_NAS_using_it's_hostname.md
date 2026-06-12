---
title: "How do I mount a NAS using it's hostname?"
date: 2015-03-28
forum: Networking &amp; Wireless
---

### Post by robert169 on 2015-03-28
Hi,

Posted this in a Mythbuntu forum but thought it might be better here. 

I am going absolutely bonkers with a small but frustrating problem. I know how to mount a network share using fstab and an IP address, but no matter what I try I cannot get the mount to work with the host name as opposed to the IP. I want to do this because the NAS I want to mount has a dynamically assigned IP and so just giving a specific IP wont work 100% of the time. My ubuntu version is 12.04.2 LTS.

The output of smbtree is

```
[COLOR=#000000]
root@R2D2:/home/robert# smbtree
Enter root's password: 
MSHOME
    \\R2D2                   R2D2 server (Samba, Mythbuntu)
    \\MEDIANAS               NSA310
    \\COMPUTING-3
[/COLOR]
```

[COLOR=#000000]My fstab looks like the following[/COLOR]

```
[COLOR=#000000]
  GNU nano 2.2.6                                File: /etc/fstab                                                                      


## /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=cb137ce6-094f-4df7-a40b-b17c9ac89894 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=895C-E511  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=d9a61550-3796-4c12-ae0b-7457947606af none            swap    sw              0       0


#mount for nas
//MediaNAS/video /media/NAS cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0


#mount for NAS music
//MediaNAS/music /media/NASMusic cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0


#mnount for admin
//MediaNAS/admin /media/Admin cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0
[/COLOR]
```
When I run mount -a I simply get the following

```
[COLOR=#000000]
root@R2D2:/home/robert# mount -a
mount error: could not resolve address for MediaNAS: Unknown error
mount error: could not resolve address for MediaNAS: Unknown error
mount error: could not resolve address for MediaNAS: Unknown error[/COLOR]
Can anyone shed any light on this problem please?
```

---

### Post by bab1 on 2015-03-28
> **robert169 said:**
> Hi,

Posted this in a Mythbuntu forum but thought it might be better here. 

I am going absolutely bonkers with a small but frustrating problem. I know how to mount a network share using fstab and an IP address, but no matter what I try I cannot get the mount to work with the host name as opposed to the IP. I want to do this because the NAS I want to mount has a dynamically assigned IP and so just giving a specific IP wont work 100% of the time. My ubuntu version is 12.04.2 LTS.

The output of smbtree is

```
[COLOR=#000000]
root@R2D2:/home/robert# smbtree
Enter root's password: 
MSHOME
    \\R2D2                   R2D2 server (Samba, Mythbuntu)
    \\MEDIANAS               NSA310
    \\COMPUTING-3
[/COLOR]
```

[COLOR=#000000]My fstab looks like the following[/COLOR]

```
[COLOR=#000000]
  GNU nano 2.2.6                                File: /etc/fstab                                                                      


## /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=cb137ce6-094f-4df7-a40b-b17c9ac89894 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=895C-E511  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=d9a61550-3796-4c12-ae0b-7457947606af none            swap    sw              0       0


#mount for nas
//MediaNAS/video /media/NAS cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0


#mount for NAS music
//MediaNAS/music /media/NASMusic cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0


#mnount for admin
//MediaNAS/admin /media/Admin cifs uid=robert,username=admin,password=1234,iocharset=utf8,sec=ntlm  0  0
[/COLOR]
```
When I run mount -a I simply get the following

```
[COLOR=#000000]
root@R2D2:/home/robert# mount -a
mount error: could not resolve address for MediaNAS: Unknown error
mount error: could not resolve address for MediaNAS: Unknown error
mount error: could not resolve address for MediaNAS: Unknown error[/COLOR]
Can anyone shed any light on this problem please?
```

The command *smbtree* is not providing all the information you need to*_ mount the share_* from the NAS.  If it was correct it would show this format: //NETBIOS_NAME/SHARE_NAME.  Since is does not you get the error when you try and mount the share.

Let's see what a little debug shows.  Post the output of this command```
smbtree -d3
```

---

### Post by robert169 on 2015-03-28
Here you go, I have no bloody clue what half of it means though - always eager to learn

```
root@R2D2:/home/robert# smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The security=share option is deprecated
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
MSHOME
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\R2D2           		R2D2 server (Samba, Mythbuntu)
Connecting to host=R2D2
name_resolve_bcast: Attempting broadcast lookup for name R2D2<0x20>
resolve_hosts: Attempting host lookup for name R2D2<0x20>
	\\MEDIANAS       		NSA310
	\\COMPUTING-3  
```

---

### Post by bab1 on 2015-03-28
> **robert169 said:**
> Here you go, I have no bloody clue what half of it means though - always eager to learn

```
root@R2D2:/home/robert# smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The security=share option is deprecated
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
MSHOME
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\R2D2           		R2D2 server (Samba, Mythbuntu)
Connecting to host=R2D2
name_resolve_bcast: Attempting broadcast lookup for name R2D2<0x20>
resolve_hosts: Attempting host lookup for name R2D2<0x20>
	\\MEDIANAS       		NSA310
	\\COMPUTING-3  
```

There seems to be a login failure (SPNEGO login failed: Logon failure).  The host can be found (by NETBIOS NAME) but the user is not authenticated.  You shouldn't use a root login for accessing Samba shares.  I would use the normal users login even if you are testing.

I notice you are using *security=share* instead of *security=**user***.  This could be the problem if the permissions on the share are wrong.  I'm not sure that Samba will allow the root login access in this instance.

Samba is really a collection of tools.  The CLI tool smbtree is more like browsing to the share rather than using smbclient to go directly to the share via IP address.  Can you browse to the share via the GUI?

Once again you can see that the NETBIOS NAME is resolved correctly but the user is denied access.

Edit:  It would help to know if the shares were mounted when you used smbtree.  If not I would mount the shares anyway you can and run smbtree -d3 again.

---

### Post by robert169 on 2015-03-28
Can't browse to the share via the GUI. Am using Thunar and when I select the NAS under Network I get an error saying 'Failed to retrieve share list from server'.

I mounted the NAS by editing fstab and making use of the IP address. The output from smbtree -d3 is now

```
root@R2D2:/home/robert# smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The security=share option is deprecated
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
MSHOME
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\R2D2           		R2D2 server (Samba, Mythbuntu)
Connecting to host=R2D2
Connecting to 127.0.1.1 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
	\\MEDIANAS       		NSA310
Connecting to host=MEDIANAS
name_resolve_bcast: Attempting broadcast lookup for name MEDIANAS<0x20>
resolve_hosts: Attempting host lookup for name MEDIANAS<0x20>
	\\COMPUTING-3    
```

---

### Post by robert169 on 2015-03-28
Quick edit from the last post, noticed that you wanted me to change the security to 'user' in my hosts file. Did that and reordered the name resolve order to 

```
name resolve order = hosts lmhosts wins bcast

```
The output of smbtree -d3 is now

```
robert@R2D2:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter robert's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
MSHOME
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\R2D2                   R2D2 server (Samba, Mythbuntu)
Connecting to host=R2D2
resolve_hosts: Attempting host lookup for name R2D2<0x20>
        \\R2D2\recordings         TV Recordings
        \\R2D2\videos             Videos
        \\R2D2\music              Music
        \\R2D2\pictures           Pictures
        \\R2D2\IPC$               IPC Service (R2D2 server (Samba, Mythbuntu))
    \\MEDIANAS               NSA310
    \\COMPUTING-3
```

---

### Post by bab1 on 2015-03-28
> **robert169 said:**
> Quick edit from the last post, noticed that you wanted me to change the security to 'user' in my hosts file. Did that and reordered the name resolve order to 

```
name resolve order = hosts lmhosts wins bcast

```
The output of smbtree -d3 is now

```
robert@R2D2:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter robert's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
MSHOME
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to host=192.168.1.4
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\R2D2                   R2D2 server (Samba, Mythbuntu)
Connecting to host=R2D2
resolve_hosts: Attempting host lookup for name R2D2<0x20>
        \\R2D2\recordings         TV Recordings
        \\R2D2\videos             Videos
        \\R2D2\music              Music
        \\R2D2\pictures           Pictures
        \\R2D2\IPC$               IPC Service (R2D2 server (Samba, Mythbuntu))
    \\MEDIANAS               NSA310
    \\COMPUTING-3
```
The change to security = user seemed to help on R2D2 a lot.  We are displaying the shares.  Can you browse to these shares.  I don't use Thunar so I have no idea of its capabilities.  Also I would have left the name resolve order at ***name resolve order = hosts bcast***.  There is no lmhosts or wins used or needed. 

Have you added yourself to the Samba database on MEDIANAS?  What OS and configuration is this host?

I assume that there is no output past the line that has \\COMPUTING-3.  Are there shares on that host?  What OS and configuration have you used there?

---

### Post by robert169 on 2015-03-29
Um now I am really confused.

So came back downstairs this morning and ran smbtree -d3 again and got a much shorter output

```
robert@R2D2:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter robert's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>



```

The only thing I noticed which has changed is my IP, the IP is dynamically assigned so yesterday I think it was 192.168.1.4, today it is 192.168.1.10.

What is really odd is that those shares we saw yesterday (on R2D2) are the ones on this machine. So why cant I see them today in Thunar or in the output from smbtree?    As an addition, yesterday I could see three networked devices in Thunar, R2D2 (the machine I am working on), the NAS and COMPUTING-3 (which I don't think has any shares on it).

I have also jumped on my ipad this morning and my girlfriends computer and both devices can see the MediaNAS machine? Bit confused as to my the linux box is doing. Why cant I now see any shares, whether they be local or external?

---

### Post by bab1 on 2015-03-29
> **robert169 said:**
> Um now I am really confused.

So came back downstairs this morning and ran smbtree -d3 again and got a much shorter output

```
robert@R2D2:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::96de:80ff:fe52:6519%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.10 bcast=192.168.1.255 netmask=255.255.255.0
Enter robert's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>



```

The only thing I noticed which has changed is my IP, the IP is dynamically assigned so yesterday I think it was 192.168.1.4, today it is 192.168.1.10.

What is really odd is that those shares we saw yesterday (on R2D2) are the ones on this machine. So why cant I see them today in Thunar or in the output from smbtree?    As an addition, yesterday I could see three networked devices in Thunar, R2D2 (the machine I am working on), the NAS and COMPUTING-3 (which I don't think has any shares on it).

I have also jumped on my ipad this morning and my girlfriends computer and both devices can see the MediaNAS machine? Bit confused as to my the linux box is doing. Why cant I now see any shares, whether they be local or external?
I need to see the complete Samba configuration file.  Post the output of ```
cat /etc/samba/smb.conf
```

It may be that Thunar itself is part of the problem.  I would install an app called Gigolo.  This app provides the browsing capabilities that Thunar lacks natively.
The app can be installed with these commands```
sudo apt-get update
sudo apt-get install gigolo
```

A slightly different tool is *smbclient*.  It can list shares of a specific host.  Post the output of this```
smbclient -d3 -L R2D2
```

---

### Post by papibe on 2015-03-29
Hi robert169.

My first thought is this could be a problem about the system not resolving addresses rather than a samba configuration.

Could you run these commands, and post back the output?
```
apt-cache policy winbind 

cat /etc/nsswitch.conf 

ping MediaNAS

nslookup MediaNAS

dig MediaNAS

nm-tool
```
Regards.

---

