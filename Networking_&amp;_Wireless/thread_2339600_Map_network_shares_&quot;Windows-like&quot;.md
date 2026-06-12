---
title: "Map network shares &quot;Windows-like&quot;"
date: 2016-10-10
forum: Networking &amp; Wireless
---

### Post by DB4711 on 2016-10-10
Hello,

currently I mount all my network shares of a Synology NAS in my fstab like this:
//NAS.local/photo /home/user/NAS/photo cifs credentials=/home/user/.cred 0 0

In the .cred I saved username and password. Additional I configrued a Cron job to look every 2 minutes if shares are available to mount.

What I do not like is the hard coded password. In Windows one can map a network share permanently, if it is available I can browse it, if not I get a message. Furthermore user on NAS and Windows are identical (also password). Windows relays username/password of the logged in account to NAS first before a prompt comes up. So I never have to enter any passwords to use my network shares.

Is there any solution to get similar network mounting to Ubuntu? Best solution: all network shares are shown in explorer and are waiting to be accessed, then asking for my username/password. If then my Ubuntu account is relayed while accessing a share to the NAS it would be even better.

Edit: one more question. Every time my network shares are mounted I get one folder icon per share in my start menu. That's annoying. Can I stop that?

Thanks for your help!

---

### Post by TheFu on 2016-10-11
Perhaps if the native network file sharing for Unix systems was used?

Use NFS, not CIFS.  Use autofs, not /etc/fstab.  Then storage will appear as native disks, using Linux permissions, and only mount when actually requested. No hassles for credentials.  Oh, and NFS is faster than CIFS. Bonus!

Of course, the NAS has to support NFS and the cheap ones usually don't. [https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS) appears to work.

For any lurkers who can't use NFS, autofs can be used with CIFS storage. There should be a way to tell the NAS how to map Unix userids to Windows userids.  [https://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html](https://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html) and [https://askubuntu.com/questions/269643/how-do-i-map-users-with-a-samba-share](https://askubuntu.com/questions/269643/how-do-i-map-users-with-a-samba-share) explains the options. Cheap NAS with CIFS might not support username mapping.  Mine didn't so replaced it with a $120 Pentium-based Ubuntu server which handles 24TB of storage ($99 ext array with 16TB over USB3).  Performance isn't fantastic, but 75MB/sec is more than needed for the application.  The ext-array is so cheap that it doesn't support SMART, which is an issue with cheap stuff. It was unexpected, but paying 2x+ just to get SMART wasn't worth it to me. Good backups should limit the issues of NOT having access to SMART data and we all need good backups anyway.

NFS really is the best option and should be used for Linux clients, if available.

---

