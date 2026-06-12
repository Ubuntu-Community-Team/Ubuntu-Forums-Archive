---
title: "[SOLVED] Networking Problems: Large File Transfer"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by matthewrdamon on 2007-11-21
Has anyone else noticed problems with large files and Gutsy 7.10?  Here is a description of the problem:  Any download over about 10mb is significantly delayed, it will download very fast for the first few seconds, then stop, then after a while (sometimes up to a minute), it will start again.  Sometimes happening over and over again, depending on the size of the download.  Also, I can repeat this problem with uploads/downloads to/from my file server, served via NFS.  

A little information about my setup, the problem computer is a toshiba A105-S2001 laptop, it uses an atheros chipset for the wireless connectivity.  I haven't tested for this problem with a wired connection, I will post my results after I try.  Also, one possible solution that I want to test would be upgrading the wireless driver to the (beta?) madwifi driver, I'm not sure if that exists, or if it is possible to.  Lastly, this is a fresh install of gutsy.  I had upgraded the system from Fiesty, then switched to Fedora 8 (I'm back for good now).  But the problem did not exist when I upgraded, only now with the fresh install.

I wonder if anyone else is having these problems, or any solutions would be helpful.  Thanks

---

### Post by matthewrdamon on 2007-11-24
The problem persists even over the wired connection.  I guess this is a bigger problem then just upgrading the wireless driver.  Any suggestions/comments?

Thanks, 

Matt

---

### Post by matthewrdamon on 2007-11-24
Maybe I should change the title, its not even particularly large files that do this.  I can't even watch anything over about 45s on YouTube before the connection freezes.  Anyway, as usual, comments or answers greatly appreciated.  Also, I disabled IPv6, I still have the same problem.

---

### Post by matthewrdamon on 2007-11-24
Solved it, some problem with my router and the Gutsy.  It is detailed in this post:[http://ubuntuforums.org/showthread.php?t=581055](http://ubuntuforums.org/showthread.php?t=581055).  I changed my DNS address to the one provided to me by my ISP, and all is good.

---

