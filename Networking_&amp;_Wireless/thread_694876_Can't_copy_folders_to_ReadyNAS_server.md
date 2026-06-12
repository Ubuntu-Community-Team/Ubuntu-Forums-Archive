---
title: "Can't copy folders to ReadyNAS server"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by ionospheric on 2008-02-12
My NAS is a ReadyNAS NV with firmware RAIDiator  4.00c1-p2  [1.00a037]. On that NAS, I have created a share named "share1" with default options.


Under Windows XP:

On local drive C:, I create a folder named "folderwin" and create a file name "file.txt" inside that folder. I copy the folder to share1- it works without any problems.


Under Ubuntu 7.10:

I log in as user which has a user id of 1000.
On my home folder on a local drive, I create a folder named "folderlin" and create a file name "file.txt" inside that folder. 
I mount share1 with the following line in /etc/fstab:

```
//192.168.0.2/share1    /mnt/NAS1/share1     cifs uid=1000,umask=000,noauto,nogroup,rw,credentials=/root/credentials/NAS1/share1,iocharset=utf8 0 0
```

I use Nautilus to copy the folder "folderlin" to share1- I get an error message saying 
Error "Access denied" while copying "/home/user/folderlin/file.txt"
I click on cancel to dismiss the dialog.
The folder "folderlin" has been created on share1, but it is empty.
Now I start the copying process again, leaving the folder as is, and get a message
A folder named "folderlin" already exists. Do you want to replace it?

I click on "Replace", this time, the copying works, the file "file.txt" is placed in the folder "folderlin" on share1.

Another observation: copying an empty folder to the NAS works without any problems. I can also copy files into that new folder. I just can't copy folders containing files when that folder does not exist yet on the NAS.

This behavior seems unexpected and certainly makes it unfeasible to use the ReadyNAS with a Linux client. Any ideas?

---

### Post by dca on 2008-02-12
It sounds like a permissions issue on your Linux box...  This is one of those things that makes Linux more secure than Windows but sometimes bites you in the rear when you're trying to figure something out...  In Windows, depending on how your profile was created there's a good possibility it was set as Administrator or Administrator privileges meaning that everything on that file system you can mess around with and move.  When it's moved to a NAS it's already accepting the fact that all files/directories migrated or copied over are such.  
 
Now, I may be off-base on this (or just flat out wrong) but when you create new files in your /home directory and check its permissions through the command line using* ls -la* is there anything different about the files created within the directories?  In other words the NAS is attempting to keep the same rights/permissions it's receiving and something is hosing it up...  Try removing those entries from /etc/fstab and if you're using Gnome Ubuntu use the Places -> Connect to Server... option to try mounting the share...  From there attempt copying the files and see if it gives you the same result.  This will ruin my permissions theory and lean towards an issue to the way the share is mounted in /etc/fstab...

---

### Post by ionospheric on 2008-02-14
I just did a test where I set up another PC with Ubuntu 7.10 as a Samba server with a shared folder. Copying a folder to this server showed the exact same behavior as when copying to the ReadyNAS- copying from from a Windows client worked, and copying from an Ubuntu client caused the previously described problems.

When I become superuser (root), the copying works without problems.

The resulting issue here is that a non-root Linux client can utilize only one share on a server-the one with the identical UID, therefore public shares are not possible with Linux? Or is there a way?

---

