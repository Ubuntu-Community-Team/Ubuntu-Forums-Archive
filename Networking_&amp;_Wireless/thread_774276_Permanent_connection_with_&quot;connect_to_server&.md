---
title: "Permanent connection with &quot;connect to server&quot;"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Joshua Swink on 2008-04-29
How can I add a permanent connection to the desktop with "connect to server"? Whenever I reboot, the connections disappear and I have to click "Connect to server..." and enter the information again.

---

### Post by .nedberg on 2008-04-29
You could add a line in /etc/fstab to have it mounted at boot time...

What the line would look like depends on what type of share it is (samba, nfs...)

---

### Post by Iowan on 2008-04-29
If Samba, check the (somewhat dated) link in my signature - CIFS is replacing (or has already replaced) SMBFS.

---

### Post by Joshua Swink on 2008-04-30
Thanks for the replies, but I really wanted to know how to do it with "connect to server", in other words with Nautilus.

For the benefit of future readers of this thread, the answer is that you cannot do that. Nautilus does not support it.

---

