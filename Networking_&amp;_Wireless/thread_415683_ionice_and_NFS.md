---
title: "ionice and NFS"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by keller999 on 2007-04-20
I've been playing around with ionice recently to try to prioritize which programs get drive access first.  My main goal is to allow MythTV to still play HD video while sending other videos around on the network.  As it is now, the HD can't keep up with Myth's video playing request.

However, this isn't really a Myth question, hence why I came here.  I'd like to start each new instance of nfsd (the NFS daemon) with an idle ionice.  I can run the command manually with...

```
ionice -c 3 somecommand
```

However, I want to be able to run the nfs-kernel-service with an ionice of 3 (idle).  Does anyone know how I might go about doing this?  If not, could you suggest a list or forum that might be a better place to ask?

Thanks in advance for your help!

-Keller

---

