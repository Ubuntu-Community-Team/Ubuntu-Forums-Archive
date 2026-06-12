---
title: "Can update update/install"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by SG3 on 2009-07-06
When i try to update i get this message.


W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main-all/binary-i386/Packages.bz2](http://flomertens.keo.in/ubuntu/dists/dapper/main-all/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

What can be the problem.

---

### Post by diablo75 on 2009-07-06
It's possible a software source server is down.  You might try changing your source server to another one that's nearby.

Click System>Administration>Software Sources.

You'll see a box next to "Download From:"

Open that up, and then use it to select Other....

In here is a button that says something like, "Pick best server" or something similar.  It will go through and ping all available servers for you and pick the one with the fastest ping.

Close the window once this server is selected and click Reload when asked.

Then attempt to apply your updates again.

---

### Post by SG3 on 2009-07-06
*****
edited - after changing the software source couple of time i get this error when trying to update - 

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/i18n/Translation-en_US.bz2](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/i18n/Translation-en_US.bz2)  Could not resolve 'ntfs-3g.sitesweetsite.info'

W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/Packages.bz2](http://flomertens.keo.in/ubuntu/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://flomertens.keo.in/ubuntu/dists/dapper/main-all/binary-i386/Packages.bz2](http://flomertens.keo.in/ubuntu/dists/dapper/main-all/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


how can i delete those file or update them correctly : )

---

### Post by SG3 on 2009-07-21
ops edit doesn't bring back the thread

---

