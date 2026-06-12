---
title: "Transfer Files"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by NewWaves on 2006-09-15
Hi,
I recently purcahsed a new computer... I'd like to throw some files from my old pc into the new one, how can I do this?  I thought about setting up a FTPd on the new one and copying it over, but I wanted to know what else I could do.  Any ideas?

---

### Post by tagra123 on 2006-09-15
> **NewWaves said:**
> Hi,
I recently purcahsed a new computer... I'd like to throw some files from my old pc into the new one, how can I do this?  I thought about setting up a FTPd on the new one and copying it over, but I wanted to know what else I could do.  Any ideas?


SCP works well for a few files from the command line. 

```
man scp
``` from a terminal to learn more

sharing the folders to copy from might be the easiest with nfs sharing.

---

