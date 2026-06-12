---
title: "Save to network share only"
date: 2023-12-27
forum: Networking &amp; Wireless
---

### Post by demusman on 2023-12-27
Hello,
On my Windows PC's, I have most of my data saved to a network share to minimize taking up local hard drive space.
On my Ubuntu servers, I mapped that same network share and save to it.
No problems doing that but it also still takes up local hard drive space.
Is there a way to only save to a network share? Meaning I won't have a local copy and a networked copy of the same files.

Note the mapped drive here:

> Filesystem Size Used Avail Use% Mounted on
tmpfs 411M 1.2M 410M 1% /run
/dev/vda2 540G 20G 493G 4% /
tmpfs 2.1G 21k 2.1G 1% /dev/shm
tmpfs 5.3M 0 5.3M 0% /run/lock
//Theogony/Users/Scott/DemusHS_Backups 11T 7.3T 2.9T 72% /media/theogony
tmpfs 2.1G 0 2.1G 0% /run/qemu
tmpfs 411M 4.1k 411M 1% /run/user/0
tmpfs 411M 4.1k 411M 1% /run/user/1000

Thanks.

---

### Post by TheFu on 2023-12-28
Use NFS, not CIFS.

Also, when posting terminal output, especially where columns are important, please, please, please, use forum code tags and remove fake storage.  For example, 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
will only show real storage.  
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.2G   26G  22% /
/dev/nvme0n1p3                           ext4  672M  283M  340M  46% /boot
/dev/nvme0n1p2                           vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-var01                   ext4   20G  4.1G   15G  22% /var
/dev/mapper/vg01-home01                  ext4   20G  5.9G   13G  32% /home
/dev/mapper/vg01-tmp01                   ext4  3.9G   61M  3.6G   2% /tmp
istar:/d/D1                              nfs4  3.5T  3.5T   50G  99% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T   50G  99% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   25G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.2T  239G  94% /d/D6
istar:/d/D7                              nfs4  3.6T  956G  2.5T  28% /d/D7

```
See how much easier that is to read since the columns are aligned?  I didn't do anything special. Copy/paste from the terminal into the browser, and wrapped in _code tags._ That's it.

Note the nfs4 lines at the bottom?

---

### Post by SeijiSensei on 2023-12-28
As you know, I usually choose NFS, but I do use Samba from time to time. I've never had the problem reported here.

---

### Post by TheFu on 2023-12-28
> **demusman said:**
> 
```

Filesystem Size Used Avail Use% Mounted on
/dev/vda2 540G 20G 493G 4% /
//Theogony/Users/Scott/DemusHS_Backups 11T 7.3T 2.9T 72% /media/theogony

```


Those are the only "real" storage being used on the system. The others are "pseudo-logical storage" only, not real.

So the OS is using 20G.  The 540G is a huge a location, which I'd never do, but it is your system.  See the 4% used? That's hardly anything in the storage world for an OS.

Using storage on the network mount, isn't that what you want?

---

### Post by SeijiSensei on 2023-12-28
Let's try something simple using smbclient.

```

$ cd 
$ smbclient //your_smb_server_name/sharename
[enter password when prompted]
> put some_local_file
> quit

```
I get one file in the sharename directory. What about you?

If that command fails with a name resolution problem, try using the server's IP address instead.

---

