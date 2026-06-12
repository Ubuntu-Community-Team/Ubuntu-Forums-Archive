---
title: "Ubuntu Computer: Set up as Network Attached Storage Computer"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by groomsy57 on 2006-09-08
Here is what I'm wanting to do: I have two roommates.  I use Mac, one uses Windows, and the other uses a combination of Mac or Ubuntu.  As a project to acquaint myself with Linux and Ubuntu to be more specific, I came up with the idea to take an old computer I have, put Ubuntu on it, and set it up on our network inside our apartment and use it as a storage computer pretty much.  But I also want to set it up as an ftp server so that I can access it across the net if I'm ever away from it.  The problem: I am very terrible when it comes to networking on any platform.  How hard will this be and is it doable?  Anyone have any links that would help me out?  Thanks,

Todd

---

### Post by tbonius on 2006-09-08
You need the Samba packages, a decent FTP server (maybe ProFTPD) and maybe you could try the Mdns (rendezvous.. bonjour.. hwatever) service to brouadcast NFS exports for MAC.

There are plenty of good documents on how to do each out there:

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

[http://www.linuxheadquarters.com/howto/networking/samba.shtml](http://www.linuxheadquarters.com/howto/networking/samba.shtml)

[http://archiv.debianhowto.de/en/proftpd/c_proftpd.html](http://archiv.debianhowto.de/en/proftpd/c_proftpd.html)

-Shameless Plug-

[http://www.section6.net/wiki/index.php/Main_Page](http://www.section6.net/wiki/index.php/Main_Page)

Hope this helps

T

---

### Post by groomsy57 on 2006-09-08
Thank you for the quick reply.  All these links seem great and overwhelming all at the same time.  haha  It looks to be a weekend long project, something I'll be elbows deep in tomorrow.  Again thank you for the help and I will be sure to post more if I run into any troubles.

Todd

---

