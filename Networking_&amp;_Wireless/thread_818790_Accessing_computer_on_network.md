---
title: "Accessing computer on network"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by SpenceMakesSense on 2008-06-04
On my home network I have  3 computers, one running Ubuntu and the other 2 running XP. I have needs to access these computers files and I was wondering if there was a way to do that over our network. Is there something in the likes of remote desktop I can use or is there a way just to browse their files?

---

### Post by wootah on 2008-06-04
> **SpenceMakesSense said:**
> On my home network I have  3 computers, one running Ubuntu and the other 2 running XP. I have needs to access these computers files and I was wondering if there was a way to do that over our network. Is there something in the likes of remote desktop I can use or is there a way just to browse their files?

You bet there is :) You can use what's called SAMBA of NFS. Samba might be a little easier to start off with, as you don't have to do additional configuration on the Windows machine, imo. Here is a link to a good guide: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by superprash2003 on 2008-06-04
you gotta use samba.. NFS is only linux to linux.. with windows pcs samba is required.. for remote desktop check this [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)

---

### Post by wootah on 2008-06-05
> **superprash2003 said:**
> you gotta use samba.. NFS is only linux to linux.. with windows pcs samba is required.. for remote desktop check this [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)

You can use NFS through windows provided that you download and install the Windows Services for UNIX.

[http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)

and

[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

and
[URL="http://www.microsoft.com/downloads/details.aspx?familyid=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en"]
http://www.microsoft.com/downloads/details.aspx?familyid=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en[/URL] (to download Windows Services for UNIX 3.5)

:popcorn:

---

