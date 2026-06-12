---
title: "Mounting Vista Shares not working"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by NongA_TongE on 2008-03-30
So I am pretty much a Linux n00b.  I now have 3 Ubuntu boxes, 1 is Gutsy, the other two are Feisty.
I also have one Vista box with a network share on it.  All boxes are on the MSHOME worgroup 
When I try to mount the Vista share with samba from the terminal, it does not work.  I get:

nsgilmore1@nsgilmore1-desktop:~$ sudo mount -t smbfs -o username={windows username},password={windows pasword}  //XPS1/FAH /mnt/XPS

mount: wrong fs type, bad option, bad superblock on //XPS1/FAH,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I run dmesg | tail,  I get: 
nsgilmore1@nsgilmore1-desktop:/mnt$ dmesg | tail
[102017.316436] end_request: I/O error, dev hdf, sector 64
[102017.318821] hdf: tray open
[102017.319173] end_request: I/O error, dev hdf, sector 671089888
[102017.319566] hdf: tray open
[102017.319918] end_request: I/O error, dev hdf, sector 671089664
[102017.320047] UDF-fs: No partition found (1)
[102083.072977] UDF-fs: No VRS found
[102083.133988] ISO 9660 Extensions: Microsoft Joliet Level 3
[102083.242866] ISO 9660 Extensions: RRIP_1991A
[104414.606136] smbfs: mount_data version 1919251317 is not supported


I should add that this is a location I can browse to just fine.  I need a local mount though in order for a monitoring program to monitor logs in that share.

Does anyone have any suggestions for me?

---

### Post by Eiríkr on 2008-03-30
Assuming you have Gutsy installed (7.10), you need to use a filesystem type of "cifs" instead of "smbfs" -- "smbfs" has been deprecated for some time, and was finally phased out around Samba version 3.024 or 3.026 (3.026 is the current Gutsy package).  

Cheers,

Eiríkr

---

### Post by NongA_TongE on 2008-03-31
Thanks for the info Eiríkr.  Unfortunately, still no luck.
I tried swapping out the fs,  and here are the results below:

nsgilmore1@nsgilmore1-desktop:~$ sudo mount -t cifs -o username={windows username},password={windows password} //XPS1/FAH /mnt/XPS
[sudo] password for nsgilmore1:
mount: wrong fs type, bad option, bad superblock on //XPS1/FAH,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

nsgilmore1@nsgilmore1-desktop:~$ dmesg |tail
[102017.320047] UDF-fs: No partition found (1)
[102083.072977] UDF-fs: No VRS found
[102083.133988] ISO 9660 Extensions: Microsoft Joliet Level 3
[102083.242866] ISO 9660 Extensions: RRIP_1991A
[104414.606136] smbfs: mount_data version 1919251317 is not supported
[105550.204033] smbfs: mount_data version 1919251317 is not supported
[105906.646248] smbfs: mount_data version 1919251317 is not supported
[107121.581954] smbfs: mount_data version 1919251317 is not supported
[110184.100308] hdf: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
[133846.815738]  CIFS VFS: cifs_mount failed w/return code = -22

any additional direction would be greatly appreciated.

Thanks!

---

### Post by Eiríkr on 2008-03-31
Now that you're not using the smbfs type, I know it's not that that's the problem, which makes me wonder why on earth mount seems to be showing that the share is a CD-RW -- ISO 9660 and the Joliet Level 3 business have to do with CD or .iso image filesystems, while the UDF-fs stuff has to do with using CD-RWs as randomly-writable media (instead of session-based media).  Your first post also included the bit "hdf tray open", which again sounds like a CD or DVD drive.  Any chance that's what your FAH share actually is?

Cheers,

Eiríkr

---

### Post by NongA_TongE on 2008-04-02
Thanks for the feedback.  I had the same concerns about the references to the tray being open and stuff.

No, the location is most assuredly NOT a disc drive.  It is "c:/program files/Folding At Home" - which is shared as "FAH" with FULL Control - EVERYONE enabled.  

Any other ideas?

---

### Post by Eiríkr on 2008-04-02
I've read somewhere that Vista introduced some pretty serious Samba incompatibilities (surprise, surprise), and that SP1 apparently fixes at least some of the troubles.  Have you installed SP1 yet (after first backing up, it sounds problematic)?

Cheers,

Eiríkr

---

