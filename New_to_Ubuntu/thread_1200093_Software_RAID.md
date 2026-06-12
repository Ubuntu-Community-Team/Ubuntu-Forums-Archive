---
title: "Software RAID"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by carl_76 on 2009-06-29
Hi.

I just installed Ubuntu 9.04 using the alternate install CD and configured 2 external hds as a software raid 1 partition in combination with the /home partition on my laptop's hd.  (3 active partitions)  While this seems to be working fine, will Ubuntu inform me if the external drive fails?  If I was to replace a failed drive would it automatically resync?

Thanks in advance.

---

### Post by Boondoklife on 2009-07-03
I dont believe ubuntu will inform you, but you can get the info from cat /proc/mdstat.

You could have that monitored in a conky script or have it emailed out with a script etc.

---

