---
title: "SMB vs NFS Home Network"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Sand Lee on 2007-06-13
I was just trying to set up a network not too long ago. I was connecting my Ubuntu desktop to my Ubuntu laptop. So when i chose how to share my folders, i chose NFS as Linux is Unix-like. The other choice was Samba, which is for Windows networks. To my surprise the folders weren't shared and i had to switch to Samba in order to get them to  work. Does anyone have a clue as to why this happened? What is the difference between SMB and NFS I'm quite confused :confused:

---

### Post by dad311 on 2007-06-13
NFS enables Unix like machine to share files with other Unix like machines.  

SAMBA allows Unix like machines to share files with other Unix like machines AND Window machines.

---

### Post by tagra123 on 2007-06-13
NFS is easy once youve set it up before. The first time things can get missed.

ASSUME

In this example I'll share the cdrom.

COMPUTER SHARING FILE HAS IP ADDRESS 192.168.1.51

The computer using the shared file has an IP Address 192.168.1.52


THE COMPUTER SHARING THE FILE (Server)

```
sudo apt-get install nfs-kernel-server
```
```

gksudo gedit /etc/exports
```

Add this line to share with everyone on the network.
```
/media/cdrom0      192.168.1.0/255.255.255.0
```
save the file and then exit
```

sudo /etc/init.d/nfs-kernel-server restart
```



ON THE OTHER COMPUTERS (CLIENTS)

I always install the kernel server just in case I want to share a file


```
sudo apt-get install nfs-kernel-server
```

```
sudo mkdir /media/remotesharedcdrom
sudo chmod 777 /media/remotesharedcdrom
sudo mount -t nfs 192.168.1.51:/media/cdrom0 /media/remotesharedcdrom
```

It should work.

If its not connecting then install firestarter and allow traffic on port 111 and 2049. Selecting NFS from the dropdown list will do this for you.

---

### Post by jubxie on 2007-06-13
nfs requires a little more work to setup, but I get speeds of 30-40MB/s (yes megabytes) as opposed to 8-15MB/s with samba. If you don't need to share with windows then use nfs, or share with both.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs)

.....see above

---

### Post by Sand Lee on 2007-06-14
cool i'll try this soon, i was navigating folders earlier and the process was pretty slow. Hopefully nfs will provide a speed booost for my remote desktop connection too!

---

### Post by Robin T Cox on 2007-06-16
The easiest way to set up a simple home network is with Zeroconf (Avahi), as explained in my notes:

[http://ubuntuforums.org/showthread.php?t=463836&page=4]("http://ubuntuforums.org/showthread.php?t=463836&page=4")

If you have a mixture of Windows and Ubuntu PCs on your network, then you need Samba. See:

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by dmizer on 2007-06-16
windows does not have the ability to handle nfs shares by default.  you must install special software in order to enable nfs in windows, but it is possible.

but you can install this package in windows:
[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

---

### Post by gurgle on 2007-06-20
doesnt vista have a NFS client by default?

---

### Post by Aikon- on 2008-05-12
> **gurgle said:**
> doesnt vista have a NFS client by default?

Only the Ultimate Edition does :(

---

