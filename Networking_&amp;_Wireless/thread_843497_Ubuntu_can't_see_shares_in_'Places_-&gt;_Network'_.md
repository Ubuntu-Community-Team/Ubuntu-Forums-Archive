---
title: "Ubuntu can't see shares in 'Places -&gt; Network'   why??"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by ptn107 on 2008-06-28
I know samba is set up correctly because the share is visible and accessible to the windows computers on my local network.  It is also accessible from my two linux machines (Ubuntu and Debian) when I manually put in the network path in 'Places -> Connect to Server'.

However, the share does not show up in Ubuntu or Debian under 'Places -> Network -> Windows Network'.  The output of 'smbtree' is also blank on the Ubuntu [samba server] machine.

my smb.conf (the only share is at the bottom) - [http://paste.ubuntu.com/23554/](http://paste.ubuntu.com/23554/)
Samba is allowed in Firestarter for my local net on ports 137-139, 445 for 192.168.24.0/24.
My username was also added to samba via 'sudo smbpasswd -a *username*'

Any help would be greatly appreciated.

---

