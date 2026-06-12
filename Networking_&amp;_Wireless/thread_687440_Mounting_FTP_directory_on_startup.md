---
title: "Mounting FTP directory on startup"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by hackle577 on 2008-02-04
I can easily connect to an FTP directory via the **Connect To Server** application, but I'm wondering if there's a way to automate this at startup?

I've read a bit about curlftpfs but I can't seem to get it to login at all, and I don't see the point of having it installed if I can get the FTP directory mounted via the native Connect to Server thing.

---

### Post by curtlee2002 on 2008-02-04
I would be glade to help if I can.
First you need permision to use FUSE

```
$ ls /dev/fuse -la
crw-rw---- 1 root fuse 10, 229 2008-02-03 13:42 /dev/fuse
```

So you need to add your self to the fuse group. 

**NOTE: Below that is your local (on your computer) user name.**

```
$ sudo gpasswd -a <username> fuse

```
Now you can edit your fstab file

```
$ sudo /etc/fstab

```
add the following line changing it to your info

```
curlftpfs#<FTP_USERNAME>:<FTP_PASSWORD>@ftp.example.com /<YOUR_MOUNTPOINT> fuse rw,uid=500,users 0 0

```
**NOTE: You must logout and back in to your local account for the added group to take affect. **

Once you have logged back in running 
```
$ mount /<YOUR_MOUNTPOINT>
```
will mount the ftp server.

---

### Post by hackle577 on 2008-02-04
OK, I followed your directions and added the curlftpfs line to my fstab, but when I logged out and logged back in, my desktop was blank and I Nautilus wouldn't open up my home folder or anything.

I had to take the line out of my fstab and reboot to reverse that.

---

### Post by curtlee2002 on 2008-02-04
ok run this two see if the fuse module is loaded
```
$ lsmod | grep fuse
fuse                   52528  3 
```

if not run
```
sudo modprobe fuse
```

you can also try removing "rw,uid=500" from your fstab

make sure you have read/write priveleges to the folder you are using as your mountpoint

---

