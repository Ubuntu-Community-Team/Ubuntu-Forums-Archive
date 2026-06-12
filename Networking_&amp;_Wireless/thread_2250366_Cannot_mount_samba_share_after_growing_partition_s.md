---
title: "Cannot mount samba share after growing partition size"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by jabeavers on 2014-10-28
I have had an operational samba server for years. I have been able to connect to the server shares with my laptop for a long time. Recently, I grew one partition on my laptop SSD while shrinking the swap partition on the same drive. Immediately after doing that, I cannot mount shares from my laptop, but I can mount shares from windows. I thought it might be different versions between the server and the laptop, so upgraded my server to 14.04 (same as my laptop), but still no joy.

I could not find anything in samba logs, but I found this in dmseg:

```
[ 3071.172400] FS-Cache: Netfs 'cifs' registered for caching
[ 3071.172486] Key type cifs.spnego registered
[ 3071.172494] Key type cifs.idmap registered
[ 3071.184002] ------------[ cut here ]------------
[ 3071.184025] WARNING: CPU: 3 PID: 3804 at /build/buildd/linux-3.13.0/fs/cifs/transport.c:313 smb_send_rqst+0x201/0x260 [cifs]()
[ 3071.184028] Send length mismatch(send_length=72 smb_buf_length=2164260932)
[ 3071.184030] Modules linked in: nls_utf8 cifs snd_hrtimer pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) autofs4 rfcomm bnep nfsd auth_rpcgss nfs_acl nfs lockd sunrpc binfmt_misc fscache snd_hda_codec_hdmi snd_hda_codec_realtek asus_nb_wmi asus_wmi sparse_keymap uvcvideo arc4 videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel snd_hda_codec snd_hwdep ath9k intel_rapl snd_pcm x86_pkg_temp_thermal intel_powerclamp ath9k_common ath9k_hw snd_page_alloc snd_seq_midi ath snd_seq_midi_event mac80211 coretemp ath3k btusb bluetooth snd_rawmidi kvm_intel nouveau kvm i915 cfg80211 snd_seq snd_seq_device snd_timer mxm_wmi crc32_pclmul snd joydev serio_raw ttm soundcore lpc_ich drm_kms_helper mei_me drm mei i2c_algo_bit parport_pc ppdev mac_hid wmi video lp parport btrfs xor raid6_pq libcrc32c psmouse r8169 mii
[ 3071.184106] CPU: 3 PID: 3804 Comm: mount.cifs Tainted: G           OX 3.13.0-37-lowlatency #64-Ubuntu
[ 3071.184108] Hardware name: ASUSTeK Computer Inc. N53SV/N53SV, BIOS N53SV.214 08/10/2011
[ 3071.184110]  00000000 00000000 db1a9d5c c1657a78 db1a9d9c db1a9d8c c105840e fd973720
[ 3071.184116]  db1a9db8 00000edc fd973648 00000139 fd9503b1 fd9503b1 db1a9e18 81000044
[ 3071.184121]  db1a9df4 db1a9da4 c1058463 00000009 db1a9d9c fd973720 db1a9db8 db1a9dec
[ 3071.184126] Call Trace:
[ 3071.184134]  [<c1657a78>] dump_stack+0x48/0x69
[ 3071.184139]  [<c105840e>] warn_slowpath_common+0x7e/0xa0
[ 3071.184148]  [<fd9503b1>] ? smb_send_rqst+0x201/0x260 [cifs]
[ 3071.184155]  [<fd9503b1>] ? smb_send_rqst+0x201/0x260 [cifs]
[ 3071.184159]  [<c1058463>] warn_slowpath_fmt+0x33/0x40
[ 3071.184165]  [<fd9503b1>] smb_send_rqst+0x201/0x260 [cifs]
[ 3071.184170]  [<c165df62>] ? _raw_spin_lock_bh+0x12/0x60
[ 3071.184177]  [<fd95043c>] smb_sendv+0x2c/0x40 [cifs]
[ 3071.184183]  [<fd950471>] smb_send+0x21/0x30 [cifs]
[ 3071.184190]  [<fd93bf44>] generic_ip_connect+0x2e4/0x3d0 [cifs]
[ 3071.184196]  [<fd93fda7>] cifs_mount+0x687/0x970 [cifs]
[ 3071.184202]  [<fd92ff36>] cifs_do_mount+0x86/0x480 [cifs]
[ 3071.184207]  [<c1168a2d>] ? __kmalloc_track_caller+0x2d/0x200
[ 3071.184212]  [<c112c565>] ? __get_free_pages+0x25/0x40
[ 3071.184215]  [<c117fc31>] mount_fs+0x31/0x170
[ 3071.184219]  [<c114002f>] ? __alloc_percpu+0xf/0x20
[ 3071.184223]  [<c1197d59>] vfs_kern_mount+0x49/0xd0
[ 3071.184227]  [<c1199f09>] do_mount+0x1e9/0x950
[ 3071.184230]  [<c1199c0f>] ? copy_mount_options+0x2f/0x100
[ 3071.184234]  [<c119a90c>] SyS_mount+0x7c/0xb0
[ 3071.184237]  [<c166498d>] sysenter_do_call+0x12/0x12
[ 3071.184239] ---[ end trace a65225f9939d7f2c ]---
[ 3071.186286] CIFS VFS: Error connecting to socket. Aborting operation.
[ 3071.186485] CIFS VFS: cifs_mount failed w/return code = -5
```

The two lines that seem most pertinent to me are:
"Send length mismatch(send_length=72 smb_buf_length=2164260932)" and,
"CIFS VFS: Error connecting to socket. Aborting operation."

Any help would be appreciated.

John

---

### Post by bab1 on 2014-10-28
> **jabeavers said:**
> I have had an operational samba server for years. I have been able to connect to the server shares with my laptop for a long time. Recently, I grew one partition on my laptop SSD while shrinking the swap partition on the same drive. Immediately after doing that, I cannot mount shares from my laptop, but I can mount shares from windows. I thought it might be different versions between the server and the laptop, so upgraded my server to 14.04 (same as my laptop), but still no joy.

I could not find anything in samba logs, but I found this in dmseg:

```
[ 3071.172400] FS-Cache: Netfs 'cifs' registered for caching
[ 3071.172486] Key type cifs.spnego registered
[ 3071.172494] Key type cifs.idmap registered
[ 3071.184002] ------------[ cut here ]------------

[ 3071.186286] CIFS VFS: Error connecting to socket. Aborting operation.
[ 3071.186485] CIFS VFS: cifs_mount failed w/return code = -5
```

The two lines that seem most pertinent to me are:
"Send length mismatch(send_length=72 smb_buf_length=2164260932)" and,
"CIFS VFS: Error connecting to socket. Aborting operation."

Any help would be appreciated.

JohnHow are you mounting the share?  Via fstab?

From the Ubuntu server, post the output of this command ```
smbtree -d3
```...and also > cat /etc/fstab

---

### Post by jabeavers on 2014-10-28
No, I don't use fstab for this. I TRIED using automount, but could never get it to work. At some point (after an update), automount grabbed my directories I was trying to mount to, but I have sinced disabled automount, so it does not mess with my directories. I mount with a shortcut to a mount command that runs in a terminal:
```
sudo mount -t cifs -o username=xxxxxxx,uid=1000,gid=1000 //lss/WebRoot /lss/Webroot/
```

The above worked great for, at least, a year.

I ran smbtree twice, once as root:
```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "enable privileges" option is deprecated
Unknown parameter encountered: "force create mask"
Ignoring unknown parameter "force create mask"
Unknown parameter encountered: "force directory mask"
Ignoring unknown parameter "force directory mask"
params.c:pm_process() - Processing configuration file "/etc/samba/conf.d/smb.conf.LSS"
Processing section "[global]"
added interface eth1 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter software's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LSSFILES<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.90 ( 192.168.0.90 )
Connecting to 192.168.0.90 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\               		LSS-Laptop-linux server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb8223f90] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name <0x20>
Ignoring unknown parameter "force create mask"
Ignoring unknown parameter "force directory mask"
Segmentation fault (core dumped)

$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "enable privileges" option is deprecated
Unknown parameter encountered: "force create mask"
Ignoring unknown parameter "force create mask"
Unknown parameter encountered: "force directory mask"
Ignoring unknown parameter "force directory mask"
params.c:pm_process() - Processing configuration file "/etc/samba/conf.d/smb.conf.LSS"
Processing section "[global]"
added interface eth1 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LSSFILES<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.90 ( 192.168.0.90 )
Connecting to 192.168.0.90 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\               		LSS-Laptop-linux server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb8243d70] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name <0x20>
Ignoring unknown parameter "force create mask"
Ignoring unknown parameter "force directory mask"

```

Here is fstab, as well as some other, seemingly, important information:
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=e6dbb955-a67f-4143-9d18-2cbaa7b6c8d4 /               ext4    noatime,errors=remount-ro 0       1
# /data was on /dev/sda1 during installation
#UUID=7755553c-a79b-49a9-8c32-250ad23f8fef /data           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5a33aa41-2d6e-4ef6-9a30-374fd4026a47 none            swap    sw              0       0

$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Oct 28 07:30 5a33aa41-2d6e-4ef6-9a30-374fd4026a47 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 28 07:30 e6dbb955-a67f-4143-9d18-2cbaa7b6c8d4 -> ../../sda3

$ sudo fdisk -l /dev/sda
Disk /dev/sda: 32.0 GB, 32000000000 bytes
255 heads, 63 sectors/track, 3890 cylinders, total 62500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000109f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        60401664    62498815     1048576   82  Linux swap / Solaris
/dev/sda3            2048    60399615    30198784   83  Linux

Partition table entries are not in disk order

```

---

### Post by bab1 on 2014-10-28
> **jabeavers said:**
> No, I don't use fstab for this. I TRIED using automount, but could never get it to work. At some point (after an update), automount grabbed my directories I was trying to mount to, but I have sinced disabled automount, so it does not mess with my directories. I mount with a shortcut to a mount command that runs in a terminal:
```
sudo mount -t cifs -o username=xxxxxxx,uid=1000,gid=1000 //lss/WebRoot /lss/Webroot/
```

The above worked great for, at least, a year.

I see you have lots of non-standard configuration.  Although you don't specifically mention it it appears you have also moved from Samba v3 to Samba v4.  This change happened with Ubuntu 14.04.  The *smbd* and *nmbd* daemons (server processes) have been completely rewritten for Samba v4.  There is some incompatibility.  Some of the errors shown may be part of that.  I will highlight in red the problems I see in the output below.  I'll comment in-line and at the bottom.
> 
I ran smbtree twice, once as root:
```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
[COLOR="#FF0000"]WARNING: The "enable privileges" option is deprecated
Unknown parameter encountered: "force create mask"
Ignoring unknown parameter "force create mask"
Unknown parameter encountered: "force directory mask"
Ignoring unknown parameter "force directory mask"[/COLOR]

[COLOR="#FF0000"]params.c:pm_process() - Processing configuration file [/COLOR][COLOR="#EE82EE"]***"/etc/samba/conf.d/smb.conf.LSS"***[/COLOR]<--Why use a smb.conf file at this location and with this name?????
Processing section "[global]"
added interface eth1 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter software's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d> 
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LSSFILES<0x1d> 
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.90 ( 192.168.0.90 )
Connecting to 192.168.0.90 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	[COLOR="#FF0000"]\\               		LSS-Laptop-linux server (Samba, Ubuntu)[/COLOR]<-- no NETBIOS NAME
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
[COLOR="#FF0000"]name_resolve_bcast: Attempting broadcast lookup for name <0x20>[/COLOR]<--again no NETBIOS NAME
[COLOR="#FF0000"]samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb8223f90] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name <0x20> [/COLOR]<--one more time with no NETBIOS NAME
Ignoring unknown parameter "force create mask"
Ignoring unknown parameter "force directory mask"
[COLOR="#FF0000"]Segmentation fault (core dumped)[/COLOR]<--total failure

$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "enable privileges" option is deprecated
Unknown parameter encountered: "force create mask"
Ignoring unknown parameter "force create mask"
Unknown parameter encountered: "force directory mask"
Ignoring unknown parameter "force directory mask"
params.c:pm_process() - Processing configuration file "/etc/samba/conf.d/smb.conf.LSS"
Processing section "[global]"
added interface eth1 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LSSFILES<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LSSFILES<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.90 ( 192.168.0.90 )
Connecting to 192.168.0.90 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\               		LSS-Laptop-linux server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb8243d70] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name <0x20>
Ignoring unknown parameter "force create mask"
Ignoring unknown parameter "force directory mask"

```


These are essentially the same.  The errors mean that *smbd* (Samba) is misconfigured and has deprecated and unknown parameters in the smb config file.  It also looks like you are using a non-standard location and file name for the configuration ( Processing configuration file "/etc/samba/conf.d/smb.conf.LSS"). 

The bottom line is that Samba can't resolve the host name to the NETBIOS NAME and therefore fails.  But it fails miserably so I feel there are other problems too.  It's entirely posible that the smbd daemon is not running at all.  We can check that.  Post the output of this command ```

pgrep -l mbd

```... this should list 2 smbd and 1 nmbd daemons running.

What I need now is the entire configuration file that Samba is using.  Why is Samba using a non-standard location and file name?  Maybe you should post both the */etc/samba/conf.d/smb.conf.LSS * and the */etc/samba/smb.conf* files with these commands```

cat  /etc/samba/conf.d/smb.conf.LSS

cat /etc/samba/smb.conf

```
I'm wondering what method of hostname resolution is being used.  Post the output of these commands
```

hostname

cat /etc/hosts

```
Did you employ a 3rd party (not Samba or Ubuntu) configuration tool?

---

### Post by jabeavers on 2014-10-28
$ pgrep -l mbd
946 smbd
1470 nmbd
1473 nmbd


The config is different from usual, because I wanted my server to include different config files based on the request from the user. For example, if the user requests //lss... then it will include the smb.conf.LSS file, and if the user requests //videos.... it will include smb.conf.VIDEOS.

I commented the offending lines of config, but it worked fine before I grew the partition on my SSD; it still did not mount. I can mount shares on my android phone (andSMB app) and windows, but I don't have a linux computer besides my laptop that will boot to test it with. I honestly think it is a problem on the client side, not the server side.

```
$ cat /etc/samba/smb.conf
[global]
        netbios name = LSS
	netbios aliases = DATA VIDEOS
#        enable privileges = Yes
        log file = /var/log/samba/%m.log
        max log size = 50
        smb ports = 139
        name resolve order = lmhosts bcast wins host
#        client signing = No
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=16384 SO_SNDBUF=16384
        load printers = No
        printcap cache time = 750
        lock directory = /var/cache/samba
#        force create mask = 0775
#        force directory mask = 0775
#	username map = /etc/samba/smbusers
#	encrypt passwords = yes
        wins support = yes
	disable spoolss = yes
        include = /etc/samba/conf.d/smb.conf.%L

$ cat /etc/samba/conf.d/smb.conf.lss
[global]
	workgroup = LSSFILES
#	netbios name = LSS
	server string = LSS Domain - Samba %v
	logon path = \\LSS\Profiles\%u
	domain logons = Yes
	security = user
	os level = 50
	preferred master = Yes
	domain master = Yes
        ldap ssl = No
        add machine script = /usr/sbin/useradd -d /dev/null -g 900 -s /bin/false -M %u
        encrypt passwords = yes
#	force group = developers
	create mask = 775
	directory mask = 775
	time server = yes
	username map = /etc/samba/smbusers
	client signing = No
	wins support = yes	


[netlogon]
	comment = Network Logon Service
	path = /etc/samba/netlogon
	browseable = No

[homes]
	comment = Home Directories
	browseable = no
	writable = yes

[Profiles]
	path = /data/profiles/
	create mode = 0600
	directory mode = 0700
	writable = yes
	browseable = No
	csc policy = disable

[Settings]
	path = /data/LSS/settings
	create mode = 0600
	directory mode = 0700
	writable = yes
	browseable = no
	csc policy = disable

[Documents]
	path = /data/LSS/LSS Documents
	valid users = webdev, software, designer, root
	read only = No

[PC Repair]
	path = /data/LSS/PC Repair
	read only = No
	create mask = 0777
	directory mask = 0777

[WebRoot]
	path = /data/LSS/vhosts/docroot
	valid users = webdev, software, designer, root
	read only = No

[Server Settings]
	path = /data/LSS/Settings
	valid users = webdev, software, designer, root
	read only = No

[Backups]
	path = /data/LSS/Backups
	read only = No

[Wells]
	path = /data/LSS/LSS Documents/Software Design/Documents/Projects/JL Wells Projects/New Wells Manager/Tests/WellsDataRoot
	read only = No

[Other]
	path = /data/Other
	read only = no

[Apps]
	path = /data/LSS/applications/
	read only = no
	available = yes
#	share modes = yes
	locking = yes
	oplocks = yes

[Archives]
	path = /archives
	read only = no
```

I x'ed out my network ip's (I think the "reverse DNS workaround" section is an example):
```

$ hostname
lss

$ cat /etc/hosts
127.0.0.1	localhost
#127.0.1.1	lss
192.168.xx.xx	lss cloud.xxxxxxxxxxxxxx.com
192.168.xx.xx     LSS-Linux
192.168.xx.xx    Home-Desktop
192.168.xx.xx	xxxxxxxxxxxxxx.com

# reverse DNS workaround
192.168.1.100	pc0
192.168.1.101	pc1
192.168.1.102	pc2
192.168.1.103	pc3
192.168.1.104	pc4
192.168.1.105	pc5

# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
::1        localhost.localdomain    localhost
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

John

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> $ pgrep -l mbd
946 smbd
1470 nmbd
1473 nmbd


This means the daemons are running.  That's a good thing.  Have you rebooted the server to see if the daemons loaded correctly?  Probably not a high percentage call, but worth the effort to try.
> 
The config is different from usual, because I wanted my server to include different config files based on the request from the user. For example, if the user requests //lss... then it will include the smb.conf.LSS file, and if the user requests //videos.... it will include smb.conf.VIDEOS.

I commented the offending lines of config, but it worked fine before I grew the partition on my SSD; it still did not mount. I can mount shares on my android phone (andSMB app) and windows, but I don't have a linux computer besides my laptop that will boot to test it with. I honestly think it is a problem on the client side, not the server side.

The client side of Samba has never been a problem.  The default smb.conf file is fine.  There is nothing to configure on the client.  If the client worked before it should be fine now.  All the searching is performed on the server side.  If fact you can run smbtree -d3 from the server itself.  When doing that the server is also the client.  Smbtree is just a command line tool to browse the network for shares.  The -d switch sets the debug level presented to the screen.

Some observations after seeing the smb.conf files you are using; The WINS configuration is not being used at all.  The response below shows the bcast response when **smbd**  looking for the workgroup```
**name_resolve_bcast:** Attempting broadcast lookup for name LSSFILES<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
```...this works okay.  I believe that the host with the IP address of 192.168.0.4 is the Master Browser.

Next is the search for the Samba server by NETBIOS NAME to find the IP address```
name_resolve_bcast: Attempting broadcast lookup for name <0x20><--again no NETBIOS NAME
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb8223f90] mpx_fde[(nil)] fd[12] - disabling
```...since it can't find the METBIOS NAME it quits the routine.

In the end the search fails ```

resolve_hosts: **Attempting host lookup** for name <0x20> <--one more time with no NETBIOS NAME
Ignoring unknown parameter "force create mask"
Ignoring unknown parameter "force directory mask"
Segmentation fault (core dumped)<--total failure

```...this is the only time I have ever seen a segmentation fault for Samba.  :-(
> 

I x'ed out my network ip's (I think the "reverse DNS workaround" section is an example):

Is it really that important?  The IP addresses are used by most folks in their networks.  My network uses the same as yours.  In fact the IP addresses are listed in the debug info above anyway.   

For the most part the lookups are using bcast to find the NETBIOS NAMES and still not finding them in the MB or employing the WINS server that you have configured.
> 
```

$ hostname
lss

$ cat /etc/hosts
127.0.0.1	localhost
#127.0.1.1	lss
192.168.xx.xx	lss cloud.xxxxxxxxxxxxxx.com
192.168.xx.xx     LSS-Linux
192.168.xx.xx    Home-Desktop
192.168.xx.xx	xxxxxxxxxxxxxx.com

# reverse DNS workaround
192.168.1.100	pc0
192.168.1.101	pc1
192.168.1.102	pc2
192.168.1.103	pc3
192.168.1.104	pc4
192.168.1.105	pc5


```

John
What I would do is use a default smb.conf file in the default location and set this```

netbios name = <some-netbios-name>  # less than 15 characters
name resolve order = bcast

```...where <netbios-name> is whatever name you pick.  Then I would add a test share at the bottom of the smb.conf file. One of the shares you are using now is fine.

Then restart the smbd and nmbd deamons with ```
sudo service smbd restart

sudo service nmbd restart
```

The run smbtree again```
smbtree -d3
```... you can add debug up to 10 I believe.  It will provide a mind boggling amount or debug info.  More than we will need however.

If this now shows the Ubuntu server by //<netbios-name> then we know the partition work you have done is okay.  You can then delve into what happened, or just keep adding parts back until something fails.

I'm interested in helping diagnose this and the answers to this problem along with what the solution will be, so post back her the results of the tests and we can continue to a resolution.

---

### Post by jabeavers on 2014-10-29
I will do tests and report, but, I just wanted to clarify, that the repartitioning was done on the laptop (client) not the server. Just making sure that was clear. Also, the original dmesg output I posted was on the client, not the server.

I'll post reports of the tests soon.

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> I will do tests and report, but, I just wanted to clarify, that the repartitioning was done on the laptop (client) not the server. Just making sure that was clear. Also, the original dmesg output I posted was on the client, not the server.

I'll post reports of the tests soon.

This was not at all clear. It changes everything in my mind.  I'll have to think about that for a while.  I'll go back and re-read the thread.

If the server has not been changed then the tests mean very little except for the error messages about the deprecated parameters.

[COLOR="#0000FF"]Edit: After re-reading the first post I still believe the problem is basically the same.  It is a name resolution problem. [/COLOR]  So without changing anything on the server  let's try this command from the laptop (the samba client)```

smbclient -L <netbios-name of server>

```

---

### Post by jabeavers on 2014-10-29
Well, I'm convinced it is the server, now, because I can't mount the share on the server, either (I remembered I can do that to test). However, I THINK I was able to do that just a few weeks ago, but that is just a guess, at this point. It could have been before I upgraded to 14.04 (again, just a guess).

Here's the output from my laptop:

```
$ smbclient -U software -L LSS
Enter software's password: 
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	Documents       Disk      
	PC Repair       Disk      
	WebRoot         Disk      
	Server Settings Disk      
	Backups         Disk      
	Wells           Disk      
	Other           Disk      
	Apps            Disk      
	Archives        Disk      
	IPC$            IPC       IPC Service (LSS Domain - Samba 4.1.6-Ubuntu)
	software        Disk      Home Directories
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            

```

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> Well, I'm convinced it is the server, now, because I can't mount the share on the server, either (I remembered I can do that to test). However, I THINK I was able to do that just a few weeks ago, but that is just a guess, at this point. It could have been before I upgraded to 14.04 (again, just a guess).

Here's the output from my laptop:

```
$ smbclient -U software -L LSS
Enter software's password: 
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	Documents       Disk      
	PC Repair       Disk      
	WebRoot         Disk      
	Server Settings Disk      
	Backups         Disk      
	Wells           Disk      
	Other           Disk      
	Apps            Disk      
	Archives        Disk      
	IPC$            IPC       IPC Service (LSS Domain - Samba 4.1.6-Ubuntu)
	software        Disk      Home Directories
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            

```

Yes you can be both a client and the server on one host.  You still have to resolve the netbios names however.  You still are using netbios over tcp (NBT)

I don't see the all the information I thought I would see.  Where is the workgroup LSSFILES that should be listed under WORKGROUP at the bottom.  I don't see the Master Browser under Master either.  Here is what my listing looks like ```

smbclient -L malibu
Enter bab's password: 
Domain=[BEACH] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	public          Disk      Shared Data
	vfs             Disk      Test VFS Data
	IPC$            IPC       IPC Service (malibu server (Samba, Ubuntu))
	PDF             Printer   PDF
	HP-LaserJet-2200 Printer   LaserJet 2200
	bab            Disk      Home Directories
	maui            Disk      
Domain=[BEACH] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	MALIBU               malibu server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	BEACH                MALIBU

```

[COLOR="#0000FF"]Edit: At this point it's probably best if we step back and reassess the entire situation.  With that in mind I feel It will be better if we start with confirming the server is running correctly.  I would do that by running a very simple smb.conf file and seeing if all the clients can see the shares and connect to them.  There should be no need to manually mount the share on the Ubuntu laptop via a mount command or fstab.[/COLOR]

---

### Post by jabeavers on 2014-10-29
After removing the include from smb.conf, I get the following:

[CODE]
$ smbclient -U software -L LSS
Enter software's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Samba 4.1.6-Ubuntu)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	                     LSS-Laptop-linux server (Samba, Ubuntu)
	DATA                 Samba 4.1.6-Ubuntu
	LSS                  Samba 4.1.6-Ubuntu
	VIDEOS               Samba 4.1.6-Ubuntu

	Workgroup            Master
	---------            -------
	WORKGROUP            
[\CODE]

So, it is picking up the server name when not including, but not when it does include.....

---

### Post by jabeavers on 2014-10-29
> Where is the workgroup LSSFILES that should be listed under WORKGROUP at the bottom.

I don't know. I even changed the config file to have the info:

```

[global]
	workgroup = LSSFILES
        netbios name = LSS
	netbios aliases = DATA VIDEOS
#        enable privileges = Yes
        log file = /var/log/samba/%m.log
        max log size = 50
        smb ports = 139
        name resolve order = bcast
#        client signing = No
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=16384 SO_SNDBUF=16384
        load printers = No
        printcap cache time = 750
        lock directory = /var/cache/samba
#        force create mask = 0775
#        force directory mask = 0775
#	username map = /etc/samba/smbusers
#	encrypt passwords = yes
        wins support = yes
	disable spoolss = yes
#        include = /etc/samba/conf.d/smb.conf.%L

```

Here is what smbclient gave:
```
$ smbclient -L LSS
Enter software's password: 
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Samba 4.1.6-Ubuntu)
Domain=[LSSFILES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            

```

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> After removing the include from smb.conf, I get the following:

```
$ smbclient -U software -L LSS
Enter software's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Samba 4.1.6-Ubuntu)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	                     LSS-Laptop-linux server (Samba, Ubuntu)
	DATA                 Samba 4.1.6-Ubuntu
	LSS                  Samba 4.1.6-Ubuntu
	VIDEOS               Samba 4.1.6-Ubuntu

	Workgroup            Master
	---------            -------
	WORKGROUP           
``` 
[\CODE]

So, it is picking up the server name when not including, but not when it does include.....

The only thing I can say about that is that earlier statements in the conf file are wiped out by later statements regarding the same parameter.  By that I mean that only the LAST statement counts as in```

workgroup = first



workgroup = last 

```...results in the workgroup being LAST.  This is why I said to simplify the smb.conf file.

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> I don't know. I even changed the config file to have the info:


You have to restart the smbd daemon each time you make a change ```
sudo service smbd restart
```

---

### Post by jabeavers on 2014-10-29
> You have to restart the smbd daemon each time you make a change 

Yes. I do.

---

### Post by bab1 on 2014-10-29
I think we are missing thoughts of each others posts.  Go back and re read the last 2 or 3 posts.

I think you need to re-assess what you have here.  Start with a simple smb.conf file and we can check the resolution issues.  Go back to post #6.  At the bottom of that post is my recommended config used to diagnose this.

---

### Post by jabeavers on 2014-10-29
Ok.........

After making changes to config files, I've been running $ sudo service samba restart, which has been returning no output. When I look at /etc/init.d/samba, it says:
```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          samba
# Required-Start:    smbd nmbd
# Required-Stop:     smbd nmbd
# Default-Start:     
# Default-Stop:      
# Short-Description: ensure Samba daemons are started (nmbd and smbd)
### END INIT INFO

set -e

# start nmbd, smbd and samba-ad-dc unconditionally
# the init scripts themselves check if they are needed or not
case $1 in
	start)
		/etc/init.d/nmbd start
		/etc/init.d/smbd start
		/etc/init.d/samba-ad-dc start
		;;
	stop)
		/etc/init.d/samba-ad-dc stop
		/etc/init.d/smbd stop
		/etc/init.d/nmbd stop
		;;
	reload)
		/etc/init.d/smbd reload
		;;
	restart|force-reload)
		/etc/init.d/nmbd "$1"
		/etc/init.d/smbd "$1"
		/etc/init.d/samba-ad-dc "$1"
		;;
	status)
		status=0
		NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null || true`
		SERVER_ROLE=`samba-tool testparm --parameter-name="server role"  2>/dev/null | tail -1 || true`
		if [ "$SERVER_ROLE" != "active directory domain controller" ]; then
			if [ "$NMBD_DISABLED" != "Yes" ]; then
				/etc/init.d/nmbd status || status=$?
			fi
			/etc/init.d/smbd status || status=$?
		else
			/etc/init.d/samba-ad-dc status || status=$?
		fi
		exit $status
		;;
	*)
		echo "Usage: /etc/init.d/samba {start|stop|reload|restart|force-reload|status}"
		exit 1
		;;
esac

```

So, it SHOULD be restarting smbd and nmbd, but it seems it was not...... :[
I ran sudo service smbd (and nmbd) restart, and I was able to mount //lss/Other, which is in the default smb.conf file:
```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LSSFILES
   netbios name = LSS

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Other]
	path = /data/Other
	read only = no


```

So, it seems, at least part of, my problem was that the services were not be restarted correctly. :mad:
Maybe I am missing something, but it sure seems like it should work when doing service samba restart (I did restart each individually before, when you said to above, but changed back to restarting samba at some point.)

Anyway. I'll play around with config (and restarting the way that works) and await your further instructions.

---

### Post by jabeavers on 2014-10-29
Got it working, again, by using the default smb.conf (the ucf-dist version) and adding the include statement from my previous setup. It allowed me to mount my shares, again.....

Thanks for your help!

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> Got it working, again, by using the default smb.conf (the ucf-dist version) and adding the include statement from my previous setup. It allowed me to mount my shares, again.....

Thanks for your help!
Glad to hear you got it running properly.  The proper way to restart the smbd daemon is ```
sudo service ***smbd *** restart
```  The term samba (as in: service samba restart) is incorrect.  Maybe that was your problem all along.  But it all is working correctly now; right?

---

### Post by jabeavers on 2014-10-29
It wasn't my entire problem, because my original config stopped working and wouldn't work, even after a proper restart. I had to update my smb.conf file for it to start working correctly.

---

### Post by bab1 on 2014-10-29
> **jabeavers said:**
> It wasn't my entire problem, because my original config stopped working and wouldn't work, even after a proper restart. I had to update my smb.conf file for it to start working correctly.

If Samba is working properly now you should mark this thread as "solved".  ;-)

---

