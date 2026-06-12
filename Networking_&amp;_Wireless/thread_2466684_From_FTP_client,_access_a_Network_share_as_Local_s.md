---
title: "From FTP client, access a Network share as Local site"
date: 2021-09-03
forum: Networking &amp; Wireless
---

### Post by simonselmer on 2021-09-03
Hi

I'm rather new in linux, and I want to do the same as I'm able to in windows, which is to:

In FTP Client (e.f. FileZilla) to have the "Local site" access a Network share (on synology).

I have managed to be able to access in in the File Manager, BUT after a lot of googling, and looking in this forum, I cannot figure out how to access the same Network share from within FileZilla as "Local site".

In Windows, I have the Network share mounted as e.g. drive Z, so Drive Z is accessible from both Explore and also FileZilla.
But how to I do the same in Ubuntu?

Can anybody help?
And remember, I'm rather new, so I probably needs it explained kinda step-by-step to understand :)

Best Regards

---

### Post by scorp123 on 2021-09-03
Can you please go into more details?  What IP address would "Local Site" have / need to have? Or can you post a screenshot where we can see the details?

---

### Post by simonselmer on 2021-09-03
Hi
On Windows, in FileZilla, on "Local Site", and can select my mounted drive called
Y: \\MyNAS\MyFolder\

Is this sufficient, to understand what I would like to be able to do?

And the reason is I want to be able to transfer files directly from a FTP server to my local NAS shared drive.
So "Local site" needs to be my NAS Shared drive
and the "Remote site" needs to connect to the FTP server.

---

### Post by TheFu on 2021-09-03
Open any file manager, the name will depend on exactly which flavor and version of ubuntu is used.
If you have the client-cifs packages installed, then you can put *smb://MyNAS/MyFolder*  into the URL - like a website access.  It will prompt you for login credentials.  Any file manager can do this. No need for Filezilla.

If that doesn't work, try *smb://192.168.x.x/MyFolder*  You'll need to know the IP address of the NAS. It should be static, never changing.  Can you 'ping' the NAS using the name or the IP?

Only Windows has "drive letters."  No other OS works that way.  Unix-like OSes use something called "mounts" to make network storage behave as local disk.  The order of preference for LAN-based network storage would be:
[LIST]
[*]NFS
[*]CIFS
[*]Samba
[*]sftp
[/LIST]

Since 2002, nobody, anywhere, should be using plain FTP.
NFS is the native solution for network storage for Unix systems.  Linux is a Unix-like OS, of that isn't clear already.  Most $100+ NAS systems support NFS, but YMMV.  With NFS, you'd mount the storage do a directory on your Ubuntu system somewhere. It would look like every other directory and it would support chown, chmod, hardlinks, and symbolic linking ... just like every other native Linux file system.  Typically, people would mount it under something like /nfs/data so that multiple users can access it easily. You would create that directory, since it doesn't exist.

If the file manager you use doesn't work with "mynas" or the ip address, then it is entirely possible you don't have the cifs libraries installed.

I understand that Windows10 broke many things, so that the GUI doesn't work too well to access Windows Samba/CIFS storage. For that sort of storage, I've read that putting the mount into the /etc/fstab is needed.  There are a number of threads here about doing that.  There are other, better, much more knowledgeable people for that solution, if you go that way.

So, the first question is which, exact, NAS do you have. Does it support NFS?  Which level of CIFS does it support?  What is the IP address?

---

### Post by simonselmer on 2021-09-04
Hi, thank you for youjr help, much appreciated :)

I CAN access my NAS shared drive from the File Manager, so that is not the problem.
It is within a FTP client that I cannot access the NAS Shared drive as "Local site".

My NAS is a Synology, and it seems it support NFS.

So how do I mount the NAS Shared drive on linux, so it becomes accesible as "Local site" in the FTP client?
The IP is 192.168.1.100.

Best Regards Simon

---

### Post by mikewhatever on 2021-09-04
FTP support has been getting depricated for a while now. Perhaps the NAS doen't support it, or it is not configured.

---

### Post by Morbius1 on 2021-09-04
So you are connecting to the Synology NAS ftp "share" through your Ubuntu file manager and you want to connect to some other FTP server and transfer files from that server to the Synology share using Filezilla? Do I have that right?

The problem is the file manager will create a mount point under /run/user/1000/gvfs/XXXX but Filezilla isn't gvfs compliant so it can't get past the gvfs folder.

You need a non-gvfs mount point which means mounting it manually with a cifs mount of a SMB share, NFS, etc...

I suppose you can do a manual ftp mount using curlftpfs - never tried that so don''t ask me an questions about it: [https://wiki.archlinux.org/title/CurlFtpFS](https://wiki.archlinux.org/title/CurlFtpFS)

Did you try to access both ftp server locations at the same time in the File Manager. Nautilus is tab-able so with an Alt-T you can create 2 tabs with a mount in each tab and just drag and drop from one place to the other.

Here's an example using nautilus smb mounts to 2 shares:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289111&stc=1[/IMG]

---

### Post by TheFu on 2021-09-04
> **mikewhatever said:**
> FTP support has been getting depricated for a while now. Perhaps the NAS doen't support it, or it is not configured.

Plain FTP shouldn't be used.  At a minimum, sftp would be the drop-in replacement. Google "stop using plain ftp" for lots of reasons why.

On Windows, use WinSCP or FileZilla for sftp clients.  Android has a number of clients and every Linux file manager I've tried can work with sftp too.

But NFS really would be better, if you want LAN storage that behaves like local storage.  Assuming the NAS supports NFS.

---

