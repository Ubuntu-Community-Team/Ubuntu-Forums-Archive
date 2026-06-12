---
title: "Creating a user level access folder on home network"
date: 2023-07-28
forum: Networking &amp; Wireless
---

### Post by pranav-agg1 on 2023-07-28
Im trying to create a storage space on the network for everybody to dump their data while accessing thru windows, mac, ubuntu or raspberry pi.
I have an intel NUC 12 gen with ubuntu desktop 23.04 lts with thunderbolt port connected to a seagate external HDD.
I want to take the folder of the external HDD and share it on the network. 
Further also want to give access by user name and password.
I read about SSH and FTP, but trying to do this in a less complicated way and also didnt understabd them at all.
Any suggestions please.

---

### Post by TheFu on 2023-07-28
23.04 isn't an LTS release.  Support for that one ends in January, 2024.  You must upgrade/install 23.10 when it is released.  The next LTS is 24.04 - April 2024.
The last LTS was 22.04.  Calling something an LTS doesn't many it an LTS. Sorry.

If you want to share via CIFS, then you'd want Samba.  The exact client OSes matters for whether it will be compatible or not.
You should never, ever, ever, use plain FTP. Not since 2002.  We all know better than that.

For Unix-like OSes, NFS would be a better choice.  NFS is server-to-server, so all users get access to the storage like it is locally connected. NFS performs better for many needs.  I've not had luck using NFS with Windows, without using a paid NFS client, but many others have. YMMV.

The file system on the storage matters.  If it is directly connected to a Linux system, then the file system is best as a native Linux file system with full POSIX permissions, owners, groups, ACLs, xattrs.  Usually that means using ext4 or xfs as the file system. btrfs and ZFS are also options, but beyond what most beginners should consider.

For user+password .... well, anything using a password is a security fail and has been about the last 10 yrs. Best to use keys or kerberos tokens for credentials.  NFSv4 or anything based on SSH can be used in that way.

Only NFS or CIFS will provide the MS-Explorer native user interaction you'd likely expect.  sftp is 1000x easier to setup and use and when using ssh-keys, it is considered secure enough to use over the internet.  CIFS is never secure enough to use over the internet and NFSv4+ only with Kerberos AND encryption are secure enough for internet use.  I haven't use NFS over the internet in over 20 yrs, however.

You can setup a VPN server and make that available on your public IP, then NFS without encryption could be used safely.  CIFS over a VPN does bad things to the VPN bandwidth, so it isn't recommended.  sshfs and sftp would be better over the internet ... and are usually good enough and very secure provided ssh-keys are using for authentication, not user+passwords.

It is possible to have all 3 options running at the same time. They have very little overhead.  
[LIST]
[*]CIFS for MS-Windows.
[*]NFS for LAN Unix-like clients.
[*]ssh/scp/sftp/sshfs for remote clients (WinSCP/Filezilla or any Linux file manager can access sftp).
[/LIST]
So, pick what you want, let us know and we can help you find the How-To posts that already exist in these forums and on help.ubuntu.com for each.  

Just last week, I posted how to use sftp. Found it: [https://ubuntuforums.org/showthread.php?t=2489053&p=14151086#post14151086](https://ubuntuforums.org/showthread.php?t=2489053&p=14151086#post14151086)  Pretty easy. If it takes over 30 seconds, you are doing something wrong.

Morbius1 is the local expert on Samba/CIFS here. Look for posts by him.

NFS is the native way and works easily provided the uid/gid numbers match between different systems.  There is a translation layer, idmapd, which can translate uid and gid from SystemA/B/C to the NFS server. I've never used it.   You can check the numbers using the 'id' command on any Unix system.  On most Linux systems, the first username will have a uid of 1000 and a gid of 1000.  These are purely coincidence. The number just needs to match.  I think MacOS starts uids at 500, so you'll want to get idmapd and the config file for it, idmapd.conf, setup correctly.

That's probably enough for you to lookup until tomorrow.

---

