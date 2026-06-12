---
title: "Cracking WEP"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by orangecakez on 2008-11-15
I'm learning to crack the WEP I have set up in my place, so I'm following directions from:  [http://ryanunderdown.com/wp-content/uploads/2007/02/turkeyfarm.html](http://ryanunderdown.com/wp-content/uploads/2007/02/turkeyfarm.html)

But when I get to the step that says ```
wget http://syserr.com/stuff/madwifi-cvs-20051025.tar.gz
```
I get an error > ~$ wget [http://syserr.com/stuff/madwifi-cvs-20051025.tar.gz](http://syserr.com/stuff/madwifi-cvs-20051025.tar.gz)
--11:29:40--  [http://syserr.com/stuff/madwifi-cvs-20051025.tar.gz](http://syserr.com/stuff/madwifi-cvs-20051025.tar.gz)
           => `madwifi-cvs-20051025.tar.gz'
Resolving syserr.com... 206.114.147.92
Connecting to syserr.com|206.114.147.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:29:41 ERROR 404: Not Found.

I have a Linksys WPC55AG so I need to patch it.

What do I do now?

---

### Post by iponeverything on 2008-11-15
all that error means is that the instructions are out of date and the the file wget is trying to fetch no longer exist.

---

### Post by sittingducks on 2008-11-15
> **orangecakez said:**
> I'm learning to crack the WEP I have set up in my place, so I'm following directions from:  
I get an error
What do I do now?

get them from here:


[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121)

---

### Post by rlzyoner on 2008-11-15
the madwifi drivers that *sittingducks* provided a link to and aircrack-ng should do the trick

kismet / nmap are good tools also for auditing your own network

---

