---
title: "access hard drive through network"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by wvmac on 2008-02-01
I have a windows machine and I need some info from a ext3 formatted drive.  If I attach the drive to an Ubuntu server will I be able to access the files from the windows machine?  I have tried various  utilities on windows to read the hard drive but none of them work.  So will Ubuntu make it possible to copy the files to my windows machine?
Thanks for the help

---

### Post by patryk77 on 2008-02-01
It will, although you will need a way to transfer the files over the network. Easiest way would be with an FTP server, or Samba to access them from the Windows machine.

Or you can use a USB key if it's not a lot of data.

There are also ext2/3 drivers for windows (I don't know about Vista though)

---

### Post by wvmac on 2008-02-01
the ext2/ext3 drivers did not work for me on xp/2000.  I will try samba, maybe ftp. it is about 80 gigs worth of data.
thanks

---

