---
title: "Cannot get to a Windows share after reinstall"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by scootre on 2008-10-09
I have a client using Kubuntu.  After a complete system format and install of Kubuntu 8.04 (not 8.04.1) a folder on a Winders server that was available under the previous installation (Kubuntu 7.04) no longer works.

I get the error:  The file or folder smb://fs1/Data/Customers does not exist.

I've seen this before and have Googled here and elsewhere...

BUT what sets this problem apart is that the only share on that fileserever that I can no longer reach is this one and only folder that was being access by the same computer (and IP address) under Kubuntu 7.04.

The actual fileshare from the Windows server is \\fs1\Data and it contains a lot of folders.  I can get to any other folder there except the Customers folder and I think it's because the previous installation had a shortcut to it (and reading and writing happily) but now Windows has a lock of sorts on that folder.

The server in question is Windows Small Business 2003.  Everything else seems to work fine, the user is even prompted for username and password and the can, as I said, access every other folder except the Customers folder.

I can go to smb://fs1/Data and see the Customers folder, but get the error when I try to open it.  OR I can try to set up a shortcut to the Customers folder on the Desktop but get the same error.

---

### Post by scootre on 2008-10-10
Anyone, anyone?  Bueller?

---

