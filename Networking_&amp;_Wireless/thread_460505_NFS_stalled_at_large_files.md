---
title: "NFS stalled at large files"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by AchimRS on 2007-05-31
Hi,
I have a nice problem on a Feisty client machine. It is connected to a SUSE 10.0 server via mounted NFS directories.
In principle it works, but after some seconds of transferring data, the transferrate goes down to 0 and it displays "stalled" for a while. Than it continues transferring again for some seconds until it stalles again.
by transferring big files (above 10Mb ;-) it's seen betterm but it also appears by more smaller files. Transferring a 4GB file is nearly impossible, i tried it the other day over hours.

The both PCs are connected via 100Mb/s Ethernet.

i also have a laptop running on Feisty connected to the same server via 11Mb/s wireless LAN. It dont have this problems even when accessing the same exported NFS mount points.

Any idea what could cause this performace drop?
The Feisty machine do have the portmap package installed.

Thanks a lot
  Achim

---

