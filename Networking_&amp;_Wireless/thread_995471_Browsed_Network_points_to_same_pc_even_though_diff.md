---
title: "Browsed Network points to same pc even though different pc names"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by heatpumpcontrol on 2008-11-27
I installed Intrepid on (networked) pc2 and accidentally named pc2 the same host name as pc1. I changed the host name on pc2 and now when I browse the network, both host names (pc1, pc2) point to pc2 host. I can browse pc1 host if I type in its ip address.

I --purged samba and smbclient to no avail. Rebooted, but no change.

Confused :confused:

ellllp

---

### Post by heatpumpcontrol on 2008-11-29
bump

---

### Post by heatpumpcontrol on 2008-12-02
bump.... anyone?

---

### Post by heatpumpcontrol on 2008-12-10
come on guys, I'm sure someone here has the answer... for the love of God, can anyone help? :lolflag:

---

### Post by Iowan on 2008-12-11
Check the machine's **hostname** and contents of /etc/hosts file.  Beyond that, there *might* be something in /var/lib/samba/usershares (I don't have a "new-Samba" machine yet).

---

### Post by heatpumpcontrol on 2008-12-13
Thank you!!!!!!!!!!!!!!!! At least I know a directory from which to start. I will check this out when I get home. This directory seems to have my personal shares only. I now need to find the directory that contains the names of the pcs in the workgroup.

Thanks again....Iowan

---

