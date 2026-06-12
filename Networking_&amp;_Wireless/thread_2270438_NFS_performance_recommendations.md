---
title: "NFS performance recommendations?"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by timonoj on 2015-03-23
Hi guys,

I recently purchased a QNAP NAS TS-431. I'm setting it as the storage for my seafile server (among other things). I'm mounting its shares using NFS, as I'm mostly staying on linux all the time. SMB is available as well for whenever I boot on Windows, but from Linux SMB performance lacked quite a bit. Anyway, I've successfully switched to NFS, and seems to be working fine. However the guides I've seen seem to mention that when not specified, NFS will use its older protocol, v2, which I reckon might be slower. Is this still true? As NFS4 was released very long ago, not sure what's the current status. Should I specify version on my /etc/fstab, and if so, which one? Which params would you recommend to improve performance? 

Thank you!

---

### Post by SeijiSensei on 2015-03-23
First, it all depends on what the NAS supports.  

I use NFSv3 to communicate with the server in my office network.  In /etc/fstab I have "vers=3" in the options list.

---

### Post by timonoj on 2015-03-25
> **SeijiSensei said:**
> First, it all depends on what the NAS supports.  

I use NFSv3 to communicate with the server in my office network.  In /etc/fstab I have "vers=3" in the options list.

Thank you, I'll try to set it to NFS 3 and see if it works.

---

