---
title: "NFS sharing of a mounted drive"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by genka on 2014-01-18
I'm sharing a folder /home/user/data/ over NFS as /export. Works fine. 
Now I'm mounting another drive to /home/user/data/drive2 Locally everything works.
fstab:
...
UUID=169e9b-542d-4eb6-9371-3b0371       /home/user/data/drive2/     ext4    errors=remount-ro 0     0
/home/user/data/                                 /export/         none            bind            0       0

On  another PC I'm mounting the share.
sudo mount -t nfs -o  proto=tcp,port=2049 server-ip:/export /mnt
 Everything in /mnt looks OK- the same as /home/user/data/, but the folder /mnt/drive2 is empty. I can create files there, they don't show up on the server.
It is probably a well known NFS behavior, but I'm having hard time searching for answers- can't find specific keywords.

---

### Post by TheFu on 2014-01-19
Don't know the answer, but could you consider not mounting "drive2" under the NFS mount point?  Rather, make a softlink from the NFS to the real "drive2" mount point if you need it to show up that way. Use 2 mounts on the other box too.

Just an option.

---

### Post by genka on 2014-01-19
Yes, I tried it before- mount the new disk to /media/drive2 and put a softlink in ~/data Softlink doesn't work over nfs.
I also tried exporting the disk separately in fstab:
/media/drive2/                                 /export2/         none            bind            0       0
When ls /export2 locally it shows the files in drive2, but when I mount it remotely, it has the same contents as /export!

---

### Post by TheFu on 2014-01-19
I probably didn't explain clearly, since I've done what I tried to explain many, many, many times.
* All mount points need to be the same whether local or remote.
* No mount point can be below any network/NFS mount point. All must be on the local machine.
* softlinks to NFS locations are on the local file system.

So, use autofs - not that it matters - and have all NFS mounts under /.h/ ... they are "hidden" that way.  /.h/d1 and /.h/d2 are the autofs mounts. Then create /media with softlinks to directories as - **cd /media; ln -s /.h/d*  ;** that should be it. This will need to be repeated on each NFS client. Specify full paths in the ln command.

Hopefully, these are all wired ethernet connections. Wifi for file systems .. er .. sucks.

Be certain to review all the options to NFS and I would go out of my way to NFSv4 now.

If you are seeing the same contents under different export names, I would carefully check the NFS server. Perhaps the export line was copied, but not modified?

---

### Post by TheFu on 2014-01-19
I probably didn't explain clearly, since I've done what I tried to explain many, many, many times.  Or perhaps it just doesn't work?
* All mount points need to be the same whether local or remote.
* No mount point can be below any network/NFS mount point. All must be on the local machine.
* softlinks to NFS locations are on the local file system.

So, use autofs - not that it matters - and have all NFS mounts under /.h/ ... they are "hidden" that way.  /.h/d1 and /.h/d2 are the autofs mounts. Then create /media with softlinks to directories as - **cd /media; ln -s /.h/d*  ;** that should be it. This will need to be repeated on each NFS client. Specify full paths in the ln command.

Hopefully, these are all wired ethernet connections. Wifi for file systems .. er .. sucks.

Be certain to review all the options to NFS and I would go out of my way to NFSv4 now.

If you are seeing the same contents under different export names, I would carefully check the NFS server. Perhaps the export line was copied, but not modified?

---

### Post by genka on 2014-01-20
TheFu, thanks for the detailed answer, but I'm afraid I'm still confused. The term "mount" refers to connecting a physical device to a system, creating a nfs share on a server and connecting to an nfs share on a client. Which mount points do you mean in the 3 rules in your post?
You are mostly talking about configuration changes on the client side, but I'm inclined to believe that I'm doing something wrong on the server.
Of course my network is wired.

---

### Post by TheFu on 2014-01-20
You would be surprised at the number of people trying to use NFS over wifi. Surprised.

When I say mount point, I'm talking about the directory. It needs to be named and created on the server AND the clients in exactly the same point. We are talking about the real mount point, not the symlinks.

Using a mount point that is already on a remote machine doesn't work, at least I don't think it will.  NFS/CIFS mount points cannot be remote.  Further, a different file system mounted to an exported file system both on the server-side will not be automatically exported. Does that make sense?  

In short, the file systems for both NFS exports cannot be intertwined. Keep them completely separate on both the NFS server AND on all the clients. Then your issues will go away.

It might be possible to use symlinks to make the NFS file systems appear to be intertwined, but that could be bad if the locations do not match 100% as viewed from every client AND server involved.

---

### Post by genka on 2014-01-20
> **TheFu said:**
> You would be surprised at the number of people trying to use NFS over wifi. Surprised.  I never tried NFS over WiFi, but have no problems with SMB. I think WiFi has matured and is fairly reliable under normal conditions.   > **TheFu said:**
>  When I say mount point, I'm talking about the directory. It needs to be named and created on the server AND the clients in exactly the same point. We are talking about the real mount point, not the symlinks.  Do you mean that if I want to share data hard mounted to /home/user/data on the server, I should mount it to /home/user/data on the client? I already export a  directory from the first hard drive on the server. It is mounted to a different path and works fine. My problem is with sharing second hard drive. > **TheFu said:**
>  Using a mount point that is already on a remote machine doesn't work, at least I don't think it will.  NFS/CIFS mount points cannot be remote.  Further, a different file system mounted to an exported file system both on the server-side will not be automatically exported. Does that make sense?    Yes, I think it makes sense. If I have a /home/user/data directory I'm exporting, and mounting a new drive in this directory, it will not be exported.   > **TheFu said:**
>  In short, the file systems for both NFS exports cannot be intertwined. Keep them completely separate on both the NFS server AND on all the clients. Then your issues will go away.  It might be possible to use symlinks to make the NFS file systems appear to be intertwined, but that could be bad if the locations do not match 100% as viewed from every client AND server involved.

Let me show the actual commands I used. For flexibility I removed the nfs entries from fstab and mounted everything manually.   

 ```
1. Mounting the new drive on the server:  

cd /media
mkdir drive2
chmod 777 drive2/
mount /dev/sda1 /media/drive2
ls -l /media/drive2
total 20
drwxrwxrwx 6 gt   gt    4096 Jan 20 15:08 files
drwxrwxrwx 2 root root 16384 Jan 11 20:08 lost+found
-rwxrwxrwx 1 root root     0 Jan 20 15:12 test1
-rwxrwxrwx 1 root root     0 Jan 20 15:12 test2

2. Exporting:
mkdir /export2/share/drive2/
chmod 777 /export2/share/drive2/
mount --bind /media/drive2/ /export2/share/drive2
 ls -l /export2/share/drive2/
total 20
drwxrwxrwx 6 gt   gt    4096 Jan 20 15:08 files
drwxrwxrwx 2 root root 16384 Jan 11 20:08 lost+found
-rwxrwxrwx 1 root root     0 Jan 20 15:12 test1
-rwxrwxrwx 1 root root     0 Jan 20 15:12 test2

3. Setting up the client:

 showmount -e 1.0.0.1
Export list for 1.0.0.1:
/export2 1.0.0.0/24
/export  1.0.0.0/24
mount -t nfs 1.0.0.1:/export2 /mnt
ls /mnt
doc Home Video  Moto  <-----Shows the contents of /export on the server, not /export2
```

---

### Post by TheFu on 2014-01-20
Holy crap!  Well, I don't have any suggestions. I've never seen anything like that.
Looking over [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) for ideas ... 

Does umount get used to remove any prior NFS mounts first?
Did you rerun **sudo exportfs -ra** after modifying /etc/exports? Looks like you did.

Any chance the mount points are on encrypted file systems?

Probably nothing you haven't already seen/considered.

---

### Post by bab1 on 2014-01-20
> **genka said:**
> I'm sharing a folder /home/user/data/ over NFS as /export. Works fine. 
Now I'm mounting another drive to /home/user/data/drive2 Locally everything works.
fstab:
...
UUID=169e9b-542d-4eb6-9371-3b0371       /home/user/data/drive2/     ext4    errors=remount-ro 0     0
/home/user/data/                                 /export/         none            bind            0       0

On  another PC I'm mounting the share.
sudo mount -t nfs -o  proto=tcp,port=2049 server-ip:/export /mnt
 Everything in /mnt looks OK- the same as /home/user/data/, but the folder /mnt/drive2 is empty. I can create files there, they don't show up on the server.
It is probably a well known NFS behavior, but I'm having hard time searching for answers- can't find specific keywords.

I think it would help to remember a couple of things here.  You do not mount devices to mount points  You*** mount file systems*** on device partitions to mount points in the local file system.  You do not mount multiple file systems to a single mount point (e.g one mount point per file system).  It appears that you are trying to mount /home/user/data (a file system) to /export and mount /home/user/data/drive2 ( a second file system) to the same mount point of /export.

at /export you should have 2 separate directories to use as mount points.  Maybe something like /export/data and /export/data2.

What does the /etc/exports file look like?

---

### Post by genka on 2014-01-21
bab1 and TheFu, thanks for your assistance.
Exporting to directories under /export did the trick. I'll post my configs in the case it might be useful to someone.

/etc/fstab
```

# <file system>                          <mount point>     <type>        <options>       <dump>          <pass>
# / was on /dev/sda1 during installation
UUID=4d1dfb05-f789-497b-ae07-534a20ea8225       /               ext4            errors=remount-ro 0     1
# swap was on /dev/sda5 during installation
UUID=a8a84cd3-05ee-441b-841c-f9f1df3a13dc       none            swap            sw              0       0
UUID=81169e9b-542d-4eb6-9371-3b0331643f71       /media/drive2   ext4    errors=remount-ro 0     0
/home/user/data/                                /export/drive1  none            bind            0       0
/media/drive2/                                  /export/drive2  none            bind            0       0

```

/etc/export
```

/export         1.0.0.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/drive1  1.0.0.0/24(rw,insecure,no_subtree_check,async)
/export/drive2  1.0.0.0/24(rw,insecure,no_subtree_check,async)

```

---

