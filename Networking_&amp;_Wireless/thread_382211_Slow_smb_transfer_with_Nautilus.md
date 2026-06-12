---
title: "Slow smb transfer with Nautilus"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by msandoy on 2007-03-11
Hi!

I'm having a strange problem with my Ubuntu 6.10. Smb file transfer on my local network, is very slow when I'm using Nautilus (3.5-4.5 Mb/sek) . If I transfer the same files with Konqueror, I get 9.2-10.7 Mb/sek. The problem is the same, for both read and write to/from remote smb share.

My home network is 100 Mbit. Both switch and cards.

I had Dapper earlier, and there was no difference in transfer speeds for Nautilus/Konqueror there.

Can anyone guide me to the correct config files/options to tweak Nautilus?

---

### Post by dmizer on 2007-03-12
the answer to your problem is simply to mount the share with fstab instead of using places > connect to server.  nautilus sucks at network file transfer.

second link in my sig outlines the details for creating a line for mounting a share in fstab.  if you follow the guide, you'll end up with an icon on your desktop you can click and get immediate access to your shares.  cifs is faster, better, and more reliable than nautilus, and it also allows for file transfers that are larger than 2gb.  post there if you need some help.

---

