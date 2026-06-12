---
title: "SMB Not connecting to other PC"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by Synner on 2005-08-13
I've recently been trying to set up a network with my girlfriend's Windows PC (yes, the other thread is about the same thing, but there are other issues, and I thought with a new thread about the new issues, the problem might get resolved faster).  Her computer is set to share the entire drive, the firewall is off.  I tried to mount the drive as a network drive, to no avail.  All that comes up is "access denied" if I'm using the command prompt to mount the drive, or "You don't have the permissions to view /192.168.1.**/c$ if I'm trying to use samba through the file browser.

The IP address has been confirmed, as well as the account name and password.  I haven't done anything to configure Samba or anything of that nature, so if that's the step I'm missing, I'm sorry it was such an easy fix.  At this point, it's either Samba configuration or the fact that she never logs off XP that's getting in my way, I don't know of anything else that it could be.

Any help?  And I deeply apologize for being such a hassle with this, but I'm going nuts with it.

---

### Post by nad on 2005-08-13
It seems to me that you need to provide an authorized user name via the -U ( --user)  argument to your smbmount command.

---

