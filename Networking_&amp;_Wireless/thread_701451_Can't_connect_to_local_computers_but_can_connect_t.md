---
title: "Can't connect to local computers but can connect to internet"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by bsicard on 2008-02-19
I have a local network of several computers and a router that allows for automatic IP address configuration.
Most computers can share data between each other but two of them can access internet through the router but can't connect to the other computers. IP properties are set to obtain an IP address automatically so there should be no conflict with other computers, I can ping them but can't map the drive to any of them. 

Any idea of what the problem may be ? 

Thanks
Bruno

---

### Post by Iowan on 2008-02-19
Connect how - SSH, NFS, SMB/CIFS?

---

### Post by bsicard on 2008-02-20
My operating system is Windows. I would like to be able to map drives to any of those computers. When I go to map netwrok drives, it shows under "Microsoft Windows Network" the right domain but when I try to click on it to expand and select a particular computer it refuses to expand. If I try to open it directly it tells me that it is not accessible. However I can ping any of those computers.

---

### Post by Iowan on 2008-02-20
You have installed Samba on the Linux boxes having files to share?

---

