---
title: "Network shares get dismounted in the middle of a transfer on Hardy?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by nonoitall on 2008-07-29
I've been copying some files from a Windows network share to my home directory on my laptop (running Hardy) and my progress has been hampered by mysterious automatic dismounts that occur right in the middle of transferring files.  I use the GUI method of going to Network Places and navigating to the appropriate share, and then copy and paste the directories/files to my home directory.

All seems to be going well, but after a while (it seems to vary from 15-45 minutes or so) the network share dismounts for no apparent reason, and the transfer just hangs.  So, rather than copy everything at once I've been stuck doing a few directories at a time.  Also, when the transfer hangs I can't cancel the transfer - pushing the cancel button has no effect, and I've had to log out just to cancel the transfer.  Very frustrating.  Any way to prevent this?

---

### Post by dmizer on 2008-07-29
Unfortunately, your best bet for solving this problem is manually mounting the share as outlined in the CIFS howto linked in my sig.

That, or try a different file system like ftp or scp.

---

### Post by cariboo on 2008-07-29
What do your smbd and nmbd logs say? They are located in var/log/samba.

Jim

---

