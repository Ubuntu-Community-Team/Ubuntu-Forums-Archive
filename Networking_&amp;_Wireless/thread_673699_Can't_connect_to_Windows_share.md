---
title: "Can't connect to Windows share"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by anagnost68 on 2008-01-20
Using feisty fawn I cannot access the windows share <ip>/public through any means:

1.  Places \ Connect to Server, no matter what I put in, when I try to connect I get a silent failure  (where's the log?)

2.  I tried someone else's suggestion of changing the workgroup setting in System 
 Network \ General tab \ workgroup (not sure to use 'mshome' or 'workgroup' as the value though)

3. Entering smb://<ip>/public does not work in the File Browser.  

4.  If I try to mount it, I get this:

# mount -t smbfs //<ip>/public /mnt/storage -o uid=1000

mount: wrong fs type, bad option, bad superblock on //<ip>/public,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

5.  smbclient shows this:

Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

        Sharename       Type      Comment
        ---------       ----      -------
        public          Disk      
        IPC$            IPC       

Domain=[&#519;] OS=[] Server=[&#65533;&#65533;&#65533;]

        Server               Comment
        ---------            -------

        Workgroup            Master

6.  Connecting from another Windows computer to this Windows share works just fine.

7.  ping from Ubuntu works

8.  It used to work from this same computer, same OS, but suddenly stopped working after an Ubuntu file system failure

Any suggestions appreciated, thanks...

---

### Post by anagnost68 on 2008-01-21
Breezy Badger works just fine for the same Windows share.  All I have to do is add the IP in the Connect to Server dialog window.

---

