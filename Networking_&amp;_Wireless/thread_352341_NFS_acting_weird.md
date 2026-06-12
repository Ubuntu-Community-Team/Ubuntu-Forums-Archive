---
title: "NFS acting weird"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by vniksic on 2007-02-03
Hi!

I have a problem concerning NFS.

I have two computers, both running Edgy Eft. One computer has an NFS server running, and the has a mount to that computer. 

Everything works fine, except one thing. While the server computer is downloading a file, be it with wget, azureus or something else, the file that is being download is nearly unreadable from the other computer. It reads at a rate of about 40 KB/s, instead of ~11 MB/s. So it's completely unusable for a preview with Mplayer or something else. Cp also reads similar read speeds. If I try to download it with scp, the file is downloaded full speed. What could be the problem? If it helps, I'll paste my /etc/fstab line concerning the nfs mount:

srv:/home/vniksic/storage /storage nfs rw,user,hard,intr 0 0

This isn't a terrible problem, but more of an inconvinience.

---

