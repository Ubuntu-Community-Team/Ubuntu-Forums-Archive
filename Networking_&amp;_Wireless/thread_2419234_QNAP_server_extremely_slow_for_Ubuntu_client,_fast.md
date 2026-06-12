---
title: "QNAP server extremely slow for Ubuntu client, fast for Windows client"
date: 2019-05-18
forum: Networking &amp; Wireless
---

### Post by nocom2 on 2019-05-18
I recently bought a QNAP TS-673 with a QM2-2P10G1TA interface card for the 10Gb speed. Added 4 3TB disks in a RAID 10 configuration and copied my files to it. This works great with windows but is extremely slow in Ubuntu. When I try to open a directory it may take more than a minute to list all files. Thunderbird takes about 5 minutes to start (if it does not crash beforehand due to time-outs). The connection is with CIFS/SAMBA. The (Netgear) switch reports the 10Gb connection to be used. Anyone any idea what might cause these delays?

The raid has a size of 4.94TB of which 2.31TB is used. 

Ububtu 18.04, all updates installed
Windows 10, all updates installed
QTS: 4.3.6.0923

---

### Post by TheFu on 2019-05-18
Please post the mount options your samba client is using.

If you are using a GUI to mount (it isn't really a mount, it is gvfs, known to be very slow), that is likely the issue.  Gvfs should get faster, eventually. I've seen the gnome guys working on it this year. No idea when those updates will make it into any Ubuntu release.

The workarond is to mount using one of these solutions:
* /etc/fstab
* straight **mount** command
* autofs

Each of these gives us total control over the mount options.

Knowing the specific samba protocol the qnap uses would be helpful too.  It it only talks SMB1, then trying to talk SMB2.1 at it isn't useful.

Sometimes, it is just a name resolution issue.  Try using the IP address instead of the name. If that is faster, you can fix the name resolution problem.

BTW, if the qnap supports NFS, that is usually 20-30% faster than any samba/CIFS, plus you get native file ownership and permissions. Unix-to-Unix on a LAN should use NFS.

---

### Post by nocom2 on 2019-05-19
Thanks @TheFu. Your remark made me realize that my information was very scant. I got many different and confusing result so today I tried to have a reproducible description of what exactly is going on. As this required the reboot of the ubuntu client and/or the server this took quite some time. 

My /etc/fstab line for mounting the server file system is:

    //tinctoris/files    /media/i    cifs    rw,credentials=/etc/.credentials,iocharset=utf8,uid=1000,gid=1000,forceuid,forcegid    0    0

This worked on my old server. When I start the file explorer (Caja in my case) and I click on /media/i it get the error:  "unable to mount: i. mount: /media/i: operation permitted for root only". I received this error yesterday as well but after witing/rebooting some time I got the very slow connection I reported. Today I persistently get this mount error. In all of these cases Windows kepot working fine and fast.

I tried mounting by hand:

    sudo mount //tinctoris/files /media/i -t cifs -o rw,credentials=/etc/.credentials,iocharset=utf8,uid=1000,gid=1000,forceuid,forcegid

That works great. The file system is mounted, the benchmarks I run return a read speed of 635MB/s which is just great. In Caja I can click on /media/i and I get a prompt response without delay. I can use the IP address or the symbolic name: both work great. I have been staring at /etc/fstab a long time but I don't understand why that does not work while mounting by hand does.  The last thing I did was (after reboot) enter:

    sudo mount -a

And all is mounted. So the question is in fact: why are the files shares in /etc/fstab not mounted?

---

### Post by TheFu on 2019-05-19
I have never used either forceuid,forcegid options. Ah. Interesting. 
 
There could be a race condition in the mount order since some storage has to be mounted before networking is up and other storage cannot be mounted before networking is up.  The fix is to add, checking the mount manpage: ```

       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).
```
to the fstab options.  

Hopefully, that will solve the issue.

---

