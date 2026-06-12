---
title: "NAS to fstab setup"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by zerogamer100 on 2013-11-13
Hello, 

I know my way around Linux a little. I have a Buffalo NAS (192.168.0.3) Connected to a switch. I then have ubuntu 12.04 server, also a 192.168.0. I am trying to figure out how to connect the NAS to the server via bash. I have a desktop but I need to do it from the shell. I know how to work my way around mtab and fstab. Can anyone help in connecting the Buffalo NAS to the server so that I can mount it to fstab permanently.

---

### Post by TheFu on 2013-11-13
Which storage sharing protocols does the Buffalo support? CIFS, NFS, iSCSI, AoE, something else?

---

### Post by zerogamer100 on 2013-11-13
From the user manual it says SMB/CIFS , AFP, FTP, SFTP, NFS. I am guessing Ill be using NFS.

---

### Post by TheFu on 2013-11-13
> **zerogamer100 said:**
> From the user manual it says SMB/CIFS , AFP, FTP, SFTP, NFS. I am guessing Ill be using NFS.

NFS would be my choice too.  Hopefully, the attached storage is formated with a Linux file system.

[https://help.ubuntu.com/12.04/serverguide/network-file-system.html#nfs-client-configuration](https://help.ubuntu.com/12.04/serverguide/network-file-system.html#nfs-client-configuration) seems to be the relevant section. I'm certain you've seen it, so what didn't work in those instructions?

---

### Post by zerogamer100 on 2013-11-15
So...
I have the 12.04 server. I am thinking create a directory on the server. Terastation is host name of the buffalo NAS.

Server-------->         /local/terastation.

Then on the server. 

Server----------->    sudo mount terastation:/local/terastation

or

Server------->   sudo mount 192.168.0.39:/local/terastation. 

Thanks for your help but im still learning. I am thinking if I can atleast mount it someone how I can then copy mtab and insert this in fstab.

---

### Post by TheFu on 2013-11-15
Review the options for the mount command. You are missing the target mount point ... or the mount location on the terasttion. I can't tell. There are 2 locations needed.

---

### Post by steeldriver on 2013-11-15
If you DON'T have an fstab entry yet, then you will need to specify both the source share name AND the location of the mountpoint where you want the share to appear in the local filesystem e.g.

```

$ showmount -e nas-01.local
Export list for nas-01.local:
/c/home   192.168.1.0/24
/c/media  192.168.1.0/24
/c/public 192.168.1.0/24
/c/backup 192.168.1.0/24

```

```

sudo mkdir -p /nfs/public

sudo mount -t nfs nas-01.local:/c/public /nfs/public

```

If you don't have the .local (avahi) mDNS name resolution you can replace the hostname.local with the appropriate LAN IP address

---

