---
title: "network problem with ubuntu 10.10"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by cmlrj2008 on 2010-10-23
We just installed 10.10 on our dell mini9 from a flash drive (reformatting too), and we ran into a problem with the wireless driver.  We were familiar with connecting to a wired internet connection in order to get it to work (adding the driver from the flash drive did not succeed and gave us an error message: "SystemError: installArchives() failed").  

But now I am having trouble getting the wired connection to work and I may have removed the network manager in the process of following other instructions.  I hope that it is not completely removed, but I don't have enough experience to get it back, and then make sure it's working. 

Any suggestions?

---

### Post by cmlrj2008 on 2010-10-23
I tried to connect our ethernet cable and then follow instructions to install a Broadcom Wireless Driver by doing the following:

*sudo apt-get install*

But I get the following output:

"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)    Something wicked happened resolving 'us.archive.ubuntu.com:http'  (-5 - No address associated with hostname)"

[I]sudo apt-get --reinstall install bcmwl-kernel-source
[/I]
"Reading package lists... Done
Building dependency tree
Reading state information... DoneE: Unable to locate package bcmwl-kernel-source"

I appreciate any help.

Thanks

---

### Post by ugm6hr on 2010-10-24
It's a bit tricky to know what to do, without knowing exactly what you have already done.
If you've just installed, maybe just reinstall again, and ask again.

---

