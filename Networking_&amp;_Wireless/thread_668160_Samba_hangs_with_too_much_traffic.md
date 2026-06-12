---
title: "Samba hangs with too much traffic"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by alffis on 2008-01-15
I have a problem with permanent samba shares. I have set up a share in fstab and samba doesn't find any errors there. I think the problem is in the file handling somehow, but I don't know specificly what's in it.

Here is the description of my problem.
The share works fine when browsing the share or using/copying/etc. single files, but if I make a playlist of music for example, Samba locks up when hatching MP3 tags. Also if I try to open simultaneously multiple files, Samba locks up.

So if there is too small time gap between disk operations or I handle multiple files simultaneously, Samba crashes and loses the connection to the server.


If I set the file system to CIFS  in fstab the share works fine, but that option hangs system in shutdown, because the system first shuts down networking and then tries to shut down the network share..
Also the share works fine in the (bloody) WindowsXP.

In my case, the server is Buffalo LinkStation Live, and the client is a Acer laptop with Ubuntu 7.10 (AMD64).

Any ideas, is this a bug or have I done something wrong?

---

### Post by sqrt2 on 2008-01-15
The problem with automatically unmounting cifs-mounted shares has been addressed [here]("http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/").

---

### Post by kevdog on 2008-01-15
Samba does this with me two when trying to copy files over 2GB in size.  No one has ever explained to me why this has happened, however Ive seen other report this problem also.  The transfer starts out fast (as in Kb/sec), but then gradually slows to nothing.  This occurs when using the simple cp command.

---

