---
title: "does smb is the right way to share files with kodi on another device?"
date: 2017-06-06
forum: Networking &amp; Wireless
---

### Post by ronjjjg8885 on 2017-06-06
can you link me to a guide?

thanks

---

### Post by TheFu on 2017-06-06
Only with Windows and only if you don't use DLNA.
For Unix systems, use NFS.

---

### Post by ronjjjg8885 on 2017-06-06
thank you
i've found this page.
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

so i did :
> [COLOR=#333333][FONT=monospace]sudo apt-get install nfs-kernel-server[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]
[/FONT]
[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]
[/FONT]
[/FONT][/COLOR]


then got stuck because i don't know how to edit the exports file. i mean i know how to open it with nano but i don't know how to tell the HD (i've SSD as the main drive) address.
so i need to know what to type in the file.

i've a music folder in the HD and a video folder.
any idea?

---

### Post by SeijiSensei on 2017-06-06
Suppose your network runs in the address space from 192.168.1.1 to 192.168.1.254.  On the server you would have entries in /etc/exports like
```
/path/to/music/folder    192.168.1.0/24(options)
```
For options, I usually choose
```
/path/to/music/folder    192.168.1.0/24(rw,async,fsid=0,no_root_squash,no_subtree_check)
```
I need "no_root_squash" so the "root" user, the one you become via sudo, can mount the exported share.  On a hard-wired network, you might choose "sync" rather than "async" to protect against the possibility of data loss.  Over wifi, I prefer async as it's much faster, but my server runs on a UPS so I'm not worried about data loss due to a power outage.

If you're exporting multiple shares off the same server, increment the fsid value for each additional share, "fsid=1", "fsid=2", etc.

You'll need to install the package nfs-common on any client machines as well.

---

### Post by TheFu on 2017-06-06
no_root_squash allows root on a client machine to act like root on the remote storage files and directories. It is not enabled by default for security reasons.  For media storage, it might make sense to export as read-only to prevent accidental (or kids) media deletions.

I don't use subnets in the exports either.  Some clients might not be trusted, so I really don't want to allow them access.  Putting in specific server hostnames on a network where all systems have known, agreed, names, is easy.  Just list them and their options on the same line. The options for each client can be different.

---

### Post by SeijiSensei on 2017-06-06
I have two or three machines that access those shares on my home network.  I use no_root_squash so I can mount them to a location under /media yet enforce permissions by username.  My $HOME is on the local drive.  I don't have young kids at home.

The same reasoning applies to my permitting the entire subnet.  I don't have any machines that should be blocked from connecting to my server.  I also want all my virtual machines to see it, and they use bridging with DHCP by default to get their addresses.  Enabling the subnet grants access to new VMs right away.

---

### Post by TheFu on 2017-06-06
Never had an issue with userids having access across NFS, except root (which is desirable).  Just keep the uids and gids matched, which is easy for end users, but harder for daemon accounts.

I never mount anything permanent under /media/. 

I will admit to messing with the uid mapping for static html files.  It is nice to have a read-only mount on the web server, but still have all the files owned by www-data, but easily edited on another box using a different userid.

Just goes to show that the simplicity of Unix can be bent to do some handy things.  We just need to be aware of choices that impact security.
Redhat recommends [against using no_root_squash]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security_Guide/sect-Security_Guide-Securing_NFS-Do_Not_Use_the_no_root_squash_Option.html"). Of course, there are always exceptions.

---

### Post by sp40140 on 2017-06-06
You are on right track with NFS.
However, samba is more widely supported (compared to NFS) but less secure.
If you have mobile devices, you can get samba to connect, but tough with NFS.
NFS/SAMBA depends on your use case. If you are doing only Kodi, NFS is just fine.

---

### Post by ronjjjg8885 on 2017-06-10
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)
i've followed Installation & Configuration but my libreelec will only access the user folder and not allow to access the files.

what went wrong in your opinion?

i really want it to work already.

tnx

---

### Post by SeijiSensei on 2017-06-10
Show us the results of these commands:
```
sudo mount | grep nfs
```

Navigate to the directory above where the NFS share is mounted and run
```
ls -l
```
then go down a level into the directory where the files are stored and run that command again.

---

### Post by ronjjjg8885 on 2017-06-11
sudo mount | grep nfs
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)



 ls -l
total 132
drwxr-xr-x   2 root root  4096 &#1497;&#1493;&#1504;  6 01:19 bin
drwxr-xr-x   3 root root  4096 &#1497;&#1493;&#1504;  7 02:28 boot
drwxr-xr-x   2 root root  4096 &#1497;&#1493;&#1504;  6 01:13 cdrom
drwxr-xr-x  20 root root  4180 &#1497;&#1493;&#1504; 11 21:34 dev
drwxr-xr-x 144 root root 12288 &#1497;&#1493;&#1504; 11 21:36 etc
drwxr-xr-x   4 root root  4096 &#1497;&#1493;&#1504;  6 01:14 home
lrwxrwxrwx   1 root root    32 &#1497;&#1493;&#1504;  7 02:27 initrd.img -> boot/initrd.img-4.8.0-54-generic
lrwxrwxrwx   1 root root    32 &#1497;&#1493;&#1504;  6 01:21 initrd.img.old -> boot/initrd.img-4.8.0-53-generic
drwxr-xr-x  25 root root  4096 &#1497;&#1493;&#1504;  7 18:15 lib
drwxr-xr-x   2 root root  4096 &#1497;&#1493;&#1504;  6 01:19 lib64
drwx------   2 root root 16384 &#1497;&#1493;&#1504;  6 01:11 lost+found
drwxr-xr-x   4 root root  4096 &#1497;&#1493;&#1504;  6 15:46 media
drwxr-xr-x   2 root root  4096 &#1508;&#1489;&#1512; 15 22:18 mnt
drwxr-xr-x   3 root root  4096 &#1497;&#1493;&#1504;  7 18:16 opt
dr-xr-xr-x 256 root root     0 &#1497;&#1493;&#1504; 11 21:33 proc
drwx------   5 root root  4096 &#1497;&#1493;&#1504;  6 15:23 root
drwxr-xr-x  29 root root   960 &#1497;&#1493;&#1504; 11 21:34 run
drwxr-xr-x   2 root root 12288 &#1497;&#1493;&#1504;  6 15:22 sbin
drwxr-xr-x   2 root root  4096 &#1497;&#1504;&#1493; 14 17:06 snap
drwxr-xr-x   2 root root  4096 &#1508;&#1489;&#1512; 15 22:18 srv
dr-xr-xr-x  13 root root     0 &#1497;&#1493;&#1504; 11 21:33 sys
drwxrwxrwt  11 root root 36864 &#1497;&#1493;&#1504; 11 21:35 tmp
drwxr-xr-x  11 root root  4096 &#1508;&#1489;&#1512; 15 22:30 usr
drwxr-xr-x  14 root root  4096 &#1508;&#1489;&#1512; 15 22:43 var
lrwxrwxrwx   1 root root    29 &#1497;&#1493;&#1504;  7 02:27 vmlinuz -> boot/vmlinuz-4.8.0-54-generic
lrwxrwxrwx   1 root root    29 &#1497;&#1493;&#1504;  6 01:21 vmlinuz.old -> boot/vmlinuz-4.8.0-53-generic




ls -l
total 4
drwx------ 27 ron ron 4096 &#1497;&#1493;&#1504; 11 21:34 ron


i don't see a "code" button so i just added the text that way

---

### Post by SeijiSensei on 2017-06-12
You haven't mounted the NFS share.  On my machine, "mount | grep nfs" returns entries like:

```
myserver:/home on /media/myserver type nfs (rw,wsize=32678,rsize=32678,addr=192.168.100.100)
```

You don't appear to have any mounted shares.  Did you install **nfs-common** on the client?  Do you have entries in the client's fstab to mount the remote shares?  E.g,

```
myserver:/home    /media/myserver   nfs  defaults 0 0
```

This should all have been spelled out in the [Ubuntu NFS guide]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). Did you read that?

---

### Post by ronjjjg8885 on 2017-06-12
i've libreelec on the client side.
i typed the commands in my pc because this is what i thought you wanted.

anyhow. your link says that:
> [COLOR=#333333][FONT=Ubuntu]Ubuntu Before deploying NFS you should be familiar with:[/FONT][/COLOR]

[LIST]
[*=left]Linux file and directory permissions
[*=left]Mounting and detaching (unmounting) filesystems
[/LIST]


but i am not familiar with these subjects yet.

i just thought it is much simpler.

anyhow.
now following the link. i typed that command resulted in...

> sudo mount --bind /home/users /export/usersmount: special device /home/users does not exist





the link is so confusing by the way.
i don't know what to do....

---

### Post by TheFu on 2017-06-12
Post your /etc/exports from the NFS server and the /etc/fstab from the clients.

Please use code tags, so things line up.  "Go Advanced" has a button, but you can use any quote tag, then replace with "code" inside.

Unix file and directory permissions are core to the security model. It is critical to understand those if you want anything to work on a multi-user system.  Work through a tutorial, spend the 45 minutes to gain that understanding.  Do it in a play directory ... somewhere under /tmp/foo/whereever.

---

### Post by ronjjjg8885 on 2017-06-14
at the end...
someone else has told me that it is not nessesarily possible to use it with openelec so _i switched to smb and it is working well._

i still have few more questions tho.

---

### Post by TheFu on 2017-06-14
So you are posting questions to the Ubuntu Forums.  We will assume "ubuntu" unless you tell us something different.  Kodi runs on Ubuntu.

Post #15 is the first place "openelec" is mentioned. That is an important detail, which would have been very helpful in the 1st post. I know NFS works well with kodi on arm and x86 platforms on a wired network. Better than samba.

BTW, some people have stuttering issues using Samba during playback, but not everyone. Hopefully, you are in the 2nd group.

Be careful with hearsay suggestions. [http://wiki.openelec.tv/index.php/Mounting_network_shares](http://wiki.openelec.tv/index.php/Mounting_network_shares) says to use the native Kodi method with NFS. That link recommends against using OS-level file shares unless you want to record TV to a network disk.

---

### Post by ronjjjg8885 on 2017-06-24
ok
soon after i left the thread i've tried to really use smb by installing it on my ubuntu.

i almost succeeded.
i mean, the samba is well installed (i think), but i could not create a proper symlink.

when i create a symlink from my hard drive i get the a music folder inside the music folder. and i can't have access to it from the raspberry pi. i can only access the main music folder.
so i need to know how to make the content of the music folder shown with symlink instead of just making another folder in it.
i know it's a very simple change, but i don't know how it's done, or where to put the slash mark exactly.

i'm already about a month without my files being accessible from the pi.

thanks

---

### Post by TheFu on 2017-06-24
To my knowledge, samba doesn't suppose symlinks without disabling some very important security features. In short, it is dangerous.  "wide-links" (or something close) is the option.

If you have a PI and Ubuntu, why use anything except NFS?  It is faster and supports all the native permissions. It supports symlinking too.

---

### Post by ronjjjg8885 on 2017-06-24
first. i really barely have knowledge about linux.
second. i've been told more than once that nfs is not supported on the pi if i use libreelec.

if you know otherwise please let me know.

from what i understand you are saying that symlinks and samba are not a good pair and that i should consider something called 'wide-links'. is that right?

---

### Post by TheFu on 2017-06-24
Let me look it up ...
smb.conf:  ```
wide links = yes
```
I'd look at the manpage carefully before using it.

```
           If is not recommended to enable this option unless you fully
           understand the implications of allowing the server to follow
           symbolic links created by UNIX clients. For most normal Samba
           configurations this would be considered a security hole and setting
           this parameter is not recommended.
```
is from the manpage. The grammar errors are direct too. ;) Be very careful.

I didn't review the entire thread. Sorry.

---

### Post by ronjjjg8885 on 2017-06-25
what should i do then if i still need to share music from my hard disk and not from the ssd? (ubuntu to openelec on the pi 2)

---

### Post by ronjjjg8885 on 2017-07-01
because you people mentioned the risks i want to take the steps to rewind to how it was.

i did that:
```
sudo apt-get remove --purge samba
```

what else should i do?

---

### Post by SeijiSensei on 2017-07-01
Read this first: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Then read it again until it makes sense.

Install nfs-kernel-server on the server.  Edit /etc/exports as I described above.  

Install nfs-common on all the clients and mount the exported share.

---

### Post by ronjjjg8885 on 2017-07-08
wait a moment.
didn't we said that nfs will not be suitable at some point?
isn't there some pre-made guide for this whole procedure that i so need?

edit:
i purged the samba library but i don't know if all the dependent samba libraries were also been removed.
how can i check?

---

