---
title: "Cant mount nfs share"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by mrroland on 2008-06-20
Hi all. I have a router running openwrt and a laptop using kubuntu

I installed unfs3 according to this toppic: [http://forum.openwrt.org/viewtopic.php?id=11847](http://forum.openwrt.org/viewtopic.php?id=11847)

my /etc/exports looks like this:
```
/mnt/usb/ftp    (rw,no_root_squash,insecure)
```
i can see the shares available:
```
showmount -e 192.168.1.161
Export list for 192.168.1.161:
/mnt <anon clnt>
```
I try to mount the share
```
sudo mount -t nfs 192.168.1.161:/mnt/usb/ftp /mnt/nfs
mount.nfs: access denied by server while mounting 192.168.1.161:/mnt/usb/ftp
```
checking the log of my router shows this:
```
Jun 20 17:38:13 midge daemon.info unfsd[1788]: 192.168.1.17 attempted to mount non-directory
```
i insmod: 
- sunrpc
- lockd
- nfs

i started
- portmap
- unfsd

I checked everything multiple times.... but i can't find the problem.
Does somebody knows the answer?

---

### Post by nixscripter on 2008-06-20
Silly question: ```
ll /mnt/usb/ftp
```

The message "non-directory" makes me wonder if it's a file or a sym/hard link.

---

### Post by mrroland on 2008-06-21
Thanks for your reply.
/mnt/usb/ftp is a directory witch contains a lot of sub directory's

/mnt/usb is the mount point of my usb harddisk (partition 1)

here is the content of /mnt/usb

```

drwxr-xr-x    7 root     root         4096 Jun 20 17:25 etc
-rw-r--r--    1 root     root          285 Jun 20 12:12 example.udhcpd-eth5.conf
drwxr--r--   10 mrroland mrroland     4096 Jun 20 12:04 ftp
drwxr-xr-x    3 root     root         4096 Oct 16  2006 lib
drwxr-xr-x    3 root     root        49152 Dec 29 18:58 lost+found
drwxr-x---    6 root     root         4096 Mar  2 17:40 st2205tool
drwxr-xr-x    7 root     root         4096 Sep 30  2007 usr
drwxr-xr-x    5 root     www          4096 Jan 27 13:04 var
-rw-r--r--    1 root     root          441 Jan  1  2000 vsftpd.conf

```

---

### Post by nixscripter on 2008-06-21
What jumps out at me is that the ftp directory is owned by another user. What user is the unfsd process running as? Does that user have search access to the directory? (Search is indicated by the x flag in rwx for permissions, and it appears to be owner only). If it's running as root, it might not be deciding to override the permissions.

In either case, depending on what you are doing with it, change one of the following:

1. Change the owner of the directory to whoever runs the unfsd process. This may screw up another process, however (such as FTP, which I am guessing also uses the directory).

2. Change the directory to be world-writable and searchable. In effect, this is lesser security hole, but since you are mounting it read-write to anyone anyway, I don't know that it's such a big deal.

3. Change who runs the unfsd process. It may be required to be run as root or something, in which case this won't work.

Hope this helps.

---

### Post by mrroland on 2008-06-22
Thanks for your info!
This looks usefull. Somehow my filesystem is now corrupted,
so i'll try to fix this.

Thanks again.

---

### Post by mrroland on 2008-06-26
Update: my disk died, so i replaced it. Installed nfs-server instead of unfsd.
Now got read acces. Need to change some accounts for rw acces, nut this won't be a problem. Thanks for your help

---

