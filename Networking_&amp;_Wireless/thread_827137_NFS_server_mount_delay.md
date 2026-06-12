---
title: "NFS server mount delay"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by jdramer on 2008-06-12
I have an embedded device running uBoot and I am trying to mount a kernel from my NFS folder on my kubuntu box (gutsy).  When the embedded device attempts to mount it times out waiting for the mount response.
Wireshark shows the embedded device sending a V2 MOUNT call, and a response occurs 5 seconds later.  The embedded device times out after 3 seconds so misses the response.  Any ideas on what this delay could be?  The embedded device works fine with 2 other NFS servers running OpenSuse.

---

### Post by jdramer on 2008-06-12
I just found a fix.  I added the IP of the embedded device to the /etc/hosts file of the kubuntu box. Now the timeout does not happen. It would appear that it was trying to do some sort of lookup before sending the response.  Are there any ideas on what ubuntu setting was causing a lookup?

---

