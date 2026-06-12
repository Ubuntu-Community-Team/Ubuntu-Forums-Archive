---
title: "Very slow transfer rates with smbfs"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by irotas on 2008-10-07
I've seen a few posts about slow transfer rates with smbfs but so far I've not found any particular solutions. Let me describe my setup:

I have VMWare installed under WinXP, and I've got Ubuntu Gutsy installed in a virtual machine. The Ubuntu virtual machine is configured to access the network using 'Bridged' Ethernet.

On the WinXP host I shared a directory with standard Windows file sharing (although I disabled 'Use simple file sharing'). 

From Ubuntu I mounted the WinXP share using smbfs. Here's the line from my /etc/fstab:
//192.168.1.47/Projects /Projects smbfs credentials=/etc/samba/cred-file,uid=irotas,gid=irotas 0 0

The trouble is that the transfer rate from the WinXP host to the Ubuntu virtual machine is incredibly slow (even though they're actually running on the same box!). I typically get about 200-250 kilobytes/sec.

I have no idea how to troubleshoot this. I don't know if the virtual machine creates a special scenario that smbfs doesn't handle well, or maybe this is the transfer speeds everyone gets with smbfs.

Any advice?

Thanks,
Adam

---

### Post by irotas on 2008-10-07
I tried mounting with cifs instead but unfortunately the transfer rate is still very slow.

Strangely, transferring over SFTP is much faster - about 5MB/s on average.

---

### Post by irotas on 2008-10-07
I set up a Samba share on the Ubuntu virtual machine, and transfers to that share from the WinXP host are extremely fast. Whatever is wrong is specific to mounting WinXP shares using cifs from Ubuntu.

---

