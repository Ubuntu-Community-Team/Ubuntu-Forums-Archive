---
title: "Error saving disk with DD over network using SMB"
date: 2023-06-19
forum: Networking &amp; Wireless
---

### Post by Starcruiser322 on 2023-06-19
I'm trying to use a live USB to run DD in order to backup my OS drive before I do a complete reinstallation on that drive. I have a SMB server running Ubuntu Server 20.04 LTS, and I'm able to access the contents of this server from all devices on my network. 
The commands I've tried to run (from a root shell) are as follows. I have already created the directory /mnt/backup:
```
mount -t cifs -o ip=[server.ip],username=[user],password=[pass] //share/name /mnt/backup
dd if=/dev/nvme0n1 | gzip -c | dd of=/mnt/backup/images/nvme.img.gz
```

DD throws this error:
```
dd: failed to open '/mnt/backup/images/nvme.img.gz': Permission denied
```

I find it very strange that DD can't get permission when running as the root user, so my suspicion is that it's somehow related to how mount interacts with a network device. Or maybe I'm an idiot and I have a malformed command or missing flag.
Any suggestions are appreciated, even if that suggestion is an entirely different approach. I just want to have this backup and I don't care much how.

---

### Post by TheFu on 2023-06-19
Root is for the local system, never remote storage.  That's how it should always work.

a) best not to use plain dd for stuff like this. Use **ddrescue**, which won't stop at any error.
b) best not to use CIFS, use ssh or even netcat.
c) best not to gzip  until the last step.

Network storage between Linux systems should be NFS.  CIFS is for MS-Windows. CIFS is one of the least capable protocols when it comes to network storage.  But I wouldn't use either for this situation.

netcat can be 2x+ faster than other options, but it doesn't have security. OTOH, you don't have to setup remote-root credentials for a quick transfer and if done quickly on a small network, the chances of that nc connection being abused is tiny, especially when the transfer happens at wirespeed.

Of course, it might just be easier to use sneaker*net and a USB storage device to do everything local, if you can't figure out the ssh or nc commands.  I use nc to migrate LVM LVs between systems.  Both systems have SSDs so the performance is limited to 1 Gbps ... but as I'm transferring 20G or less at a time, those 25 seconds for the xfer are fairly minimal.

---

### Post by sudodus on 2023-06-19
There is a dedicated tool that can clone or create an image locally as well as via a network: **Clonezilla**.

Download a 'stable' iso file from [**clonezilla.org**](https://clonezilla.org), make a USB boot drive and use it.

See also [this link with a brief description](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248?r=SearchResults&s=4%7C12.9136#958248).

---

### Post by Starcruiser322 on 2023-06-19
I did try clonezilla already and it did not like my server at all. It was the only time I've seen a connection refused by the client requesting the connection.
I know CIFS isn't ideal but I needed it for interoperability with multiple operating systems. 
Security is a non-issue on my network, the systems in question are airgapped. I'll look into netcat, thanks for the suggestion.

> Root is for the local system, never remote storage.
It's weird that it's failing anyway because I can write to that directory using a normal user account, which I sign into when I connect to the SMB server.

---

### Post by sudodus on 2023-06-20
If I remember correctly, Clonezilla uses ssh, and is probably not compatible with samba (SMB). So if it is not an option to install an ssh server in your server computer you must use another tool.

I agree, netcat can transfer 'anything', and if you need not worry about attacks via an internet connection, it should work well for you. If you never used it, [this link](https://ubuntuforums.org/showthread.php?t=2474692&p=14140395#post14140395) plus the information in **[FONT=Courier New]man nc[/FONT]** should be enough to make it work.

---

### Post by TheFu on 2023-06-20
> **sudodus said:**
> If I remember correctly, Clonezilla uses ssh, and is probably not compatible with samba (SMB). So if it is not an option to install an ssh server in your server computer you must use another tool.

ssh doesn't interfere with any other tools that I know.

---

### Post by sudodus on 2023-06-20
> **TheFu said:**
> ssh doesn't interfere with any other tools that I know.

+1

---

### Post by TheFu on 2023-06-20
> **Starcruiser322 said:**
>  
It's weird that it's failing anyway because I can write to that directory using a normal user account, which I sign into when I connect to the SMB server.

You have to get your mind around (local storage and root) compared with (remote storage and nobody).  To the remote system, the local root appears like a "nobody" account.
The root account is only root to the local system.  On another system, the root account is completely different and treated that way.

A flaw in CIFS is that storage is user-to-server mounted, unlike NFS which is server-to-server mounted.  I suppose, some people may think the CIFS method is more correct. Depends on your background, I support.  In the enterprise world, end-users aren't expected to mount storage - and everywhere I've worked, they weren't allowed to do it.  If you needed storage mounted, you'd have to ask the admin, who would setup the mount for your use (and perhaps your entire team's use). 

If you needed to mount a flash drive, the admin would setup the system to allow only that single flash drive to be mounted and only to a specific location.  If the admin was lazy, she'd make a script.  If not, she'd make a udev rule to handle it with **autofs** to control where it was mounted.  I still use autofs to mount CIFS, USB, NFS storage on my systems today.

The power to mount is the power to destroy.  End users shouldn't have that power, IMHO.

---

