---
title: "SMB shares fail to mount during boot up, hangs booting"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2013-11-18
Hi guys,
I've been dealing with this issue for a while by just using noauto on the cifs fstab entries but i am sick of mounting the drives after booting is finished and restarting dropbox (since the dropbox app is linked to 1 of those shares and complains since it's not there) everytime i turn on my computer so I guess I'll finally ask for help. Whats weird is that i just removed the noauto option from the following fstab entries
```

//192.168.0.5/fat32	/media/fat32	cifs	_netdev,noexec,credentials=/etc/samba/.credentials,nounix,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
//192.168.0.50/public	/mnt/circle	cifs	_netdev,noexec,username=daniel,password=,nounix,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```
and now the computer doesn't hang permanently anymore (it used to which is why I added the noauto option) but it does make it hang for about 1 minute before it continues.
When I boot up Xubuntu 12.04.3 running kernel 3.7.0-030700-generic I see the following errors which is when it hangs
```

CIFS VFS: Error connecting to socket. Aborting operation
[   16.876072] CIFS VFS: cifs_mount failed w/return code = -101
[   16.876538] CIFS VFS: Error connecting to socket. Aborting operation
[   16.876615] CIFS VFS: cifs_mount failed w/return code = -101
[   16.930552] NFS: Registering the id_resolver key type
[   16.930565] Key type id_resolver registered
[   16.930566] Key type id_legacy registered
[   16.946148] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.952197] CIFS VFS: Error connecting to socket. Aborting operation
[   16.952395] CIFS VFS: Error connecting to socket. Aborting operation
[   16.952472] CIFS VFS: cifs_mount failed w/return code = -101
[   16.952722] CIFS VFS: cifs_mount failed w/return code = -101
[   17.059344] CIFS VFS: Error connecting to socket. Aborting operation
[   17.059419] CIFS VFS: cifs_mount failed w/return code = -101
[   17.060055] CIFS VFS: Error connecting to socket. Aborting operation
[   17.060135] CIFS VFS: cifs_mount failed w/return code = -101

```
It's almost as if it's trying to mount the shares before the network it up. The boot process continues after around 1 minute. Is there anything I should fix in my fstab? I know it's not a huge deal to wait an extra 1 minute but that's not the point, it should be booting up correctly and quickly. Any help would be appreciated.

---

### Post by TheFu on 2013-11-18
In your fstab entry, the zeros at the end of each line mean something.
**man fstab** to learn what they mean. I think you want to modify the 6th field.

---

### Post by dannyboy79 on 2013-11-19
incorrect but thanks for trying to help me. The sixth field (fs_passno) is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.

---

### Post by Morbius1 on 2013-11-19
You could add yet another option to your list in addition to noauto: [COLOR=#0000cd]**users**[/COLOR]

Then create a new addition to your "Application Autostart" list in "Session and Startup" that mounts the partition ( without sudo ) at every login instead of every boot: 
```
mount /media/fat32
```
The network should be up by then if that's the problem.

Or you could get the mount out of fstab altogether and use [AutoFS]("http://ubuntuforums.org/showthread.php?t=2185189"). Then it will mount automatically when the mount point is accessed.

---

### Post by TheFu on 2013-11-19
> **dannyboy79 said:**
> incorrect but thanks for trying to help me. The sixth field (fs_passno) is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.

Perhaps I didn't understand the original question?  Delaying when the OS looks for devices will give them time to come online.  For non-core-OS partitions - like a USB3 drive for backups, I use "2" so the OS doesn't look until a little later.  For remote OS mounts, I manually do those when needed with a script (not the best solution for you or me). My backup script verifies that the mount point is actually mounted before continuing.

I do like the idea of **autofs** from @Morbius1 - when he writes, I listen.

---

### Post by dannyboy79 on 2013-11-19
> **TheFu said:**
> Perhaps I didn't understand the original question?  Delaying when the OS looks for devices will give them time to come online.  For non-core-OS partitions - like a USB3 drive for backups, I use "2" so the OS doesn't look until a little later.  For remote OS mounts, I manually do those when needed with a script (not the best solution for you or me). My backup script verifies that the mount point is actually mounted before continuing.

I do like the idea of **autofs** from @Morbius1 - when he writes, I listen.
if a value of zero is used, fsck will assume that the filesystem does not need to be checked. something just doesn't seem correct, the system should not be running the mount all command until after the network is only, is that true or not? do you guys have network shares that get auto mounted by your fstab?

thanks for the tips morbius, i will look into those options.

as i said, its working but it goes hang the boot process.

---

### Post by Morbius1 on 2013-11-19
> do you guys have network shares that get auto mounted by your fstab?
I used to but I ended up with AutoFS.

My path to that was discovering:
*** _netdev doesn't do what it used to do or at least how I remember it working.
*** Then I added a "mount -a" script ( I did not have noauto in my fstab ) to /etc/network/if-up.d to make sure everything was mounted after the network is up.
*** Then I did the noauto + users thing I suggested above.
*** Then I moved to Gigolo to automount since it solved 2 problems:

- It would wait until the remote share was available until it mounted
- It wouldn't hang at shutdown if the remote share was disabled before I ended the session

But gvfs in post LTS versions of Ubuntu are royally screwed up so I ended up with AutoFS which solved the same problems Gigolo did plus I got to choose my own mount point.

---

