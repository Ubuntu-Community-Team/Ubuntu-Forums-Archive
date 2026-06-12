---
title: "Novell Client on Hoary missing some directories"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by jamaas on 2005-04-15
Has anyone had good success with the Novel Client 0.91 tarball on Hoary?  I'm not sure why but the client will show me some, but not all of the directories I should be seeing on a server.  I think I have ncpfs working correctly but suspect that is the problem.  Is there a way I can double check that it is working correctly? 

Sorry, another Newbie here.

Thanks

Jim

---

### Post by jczucco on 2005-10-21
I try the same thing, install novell client in Ubuntu. I made a package with binaries and libraries required.

I compile with success novfs, but when I load the module, give:

# modprobe novfs
FATAL: Error inserting novfs (/lib/modules/2.6.12-9-386/kernel/fs/novfs/novfs.ko): Invalid module format

Your module load successfully ?

I can send to you my package with modules for you try.

---

### Post by jczucco on 2005-10-21
I follow the document:

[http://www.novell.com/documentation/linux_client/index.html?page=/documentation/linux_client/linuxclient/data/bwluu1c.html#bwluu1c](http://www.novell.com/documentation/linux_client/index.html?page=/documentation/linux_client/linuxclient/data/bwluu1c.html#bwluu1c)

but got the same error:

# modprobe novfs
FATAL: Error inserting novfs (/lib/modules/2.6.12-9-386/kernel/fs/novfs/novfs.ko): Invalid module format

---

### Post by jczucco on 2005-10-21
I successfuly load the module with the command:

modprobe --force-vermagic novfs

But the error on load the nwclient is:

machine1:/opt/novell/ncl/bin$ ./nwlogin
The novfs file system is present but not mounted correctly.

For additional information, see 'Installation and Administration Guide' in the Novell Client for Linux documentation.


:-(

---

