---
title: "Share NTFS Drive via NFS"
date: 2017-10-06
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2017-10-06
Hello, I'm wondering if this is possible.

I've got NFS setup and working.  I added the external NTFS drive to the /etc/exports file then ran ```
sudo exportfs -ra
``` I was presented with "...does not support NFS export"

This is an external NTFS storage drive that is accessed by both Windows and Ubuntu.

It is currently, and has been forever, shared via Samba but file transfer is SO SLOOOOW.... ~2MB/minute  (this is a USB 3.0 drive in a 3.0 port over a gigabit network) so I was hoping to share via NFS for speed.

Thanks

---

### Post by SeijiSensei on 2017-10-06
NFS expects the devices it exports to use Posix primitives like permissions and modification times.  NTFS does not support those.

Do you use this device with Windows computers as well?  If not, why not back up the contents and reformat it as ext4.

---

