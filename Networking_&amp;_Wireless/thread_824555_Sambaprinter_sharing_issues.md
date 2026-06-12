---
title: "Samba/printer sharing issues"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by joechummer on 2008-06-10
I have two issues, which I'm not sure whether or not are related.  And bear with me:  I've only been using Linux for less than 3 months.

In my network I have 2 Ubuntu PCs, an EeePC running the default Xandros (in KDE mode as opposed to default tabbed mode), and some Windows laptops.

The main issue is my printer, which is connected to one of the Ubuntu desktops (both of which have Samba installed and configured).  Other PCs on the network can see the printer and can add it, but none of them can print to it.  My EeePC will add it fine as a "Windows Network" shared printer(although I can't figure out what should be in the "connect as:" field when I'm browsing for it -- the default being "WORKGROUP\user".  I've tried "<host>\<username on host>" which doesn't seem to work), but it just says "error" in the print queue when I try to print a test page to the shared printer, even though the printer status in the queue shows "busy" for a second or two before going back to "idle".  The Windows laptops say that the Ubuntu PC hosting the printer doesn't have the right drivers (which it does, considering I can print to it just fine locally).  I can add the printer if I install the drivers on that laptop manually, but after Windows adds it, the status in the Printers folder shows as "Access denied, cannot connect," even though it never asked me for any username or password.  I have "guest = ok" set in the printers section in smb.conf, so I figured Samba wouldn't require or ask for a username and password.  I couldn't find anything in Ubuntu help about sharing printers, so I'm kind of at a loss here.

Also, as far as Samba shares go, pretty much all of the machines in the network, Linux or Windows, can see each others shares -- except for one.  The Ubuntu PC that has the connected printer can't see Samba shares on anything else on the network except for the other Ubuntu PC (our file server), but all of the other machines can see its shares.  The odd thing is, this machine's smb.conf file is nearly identical to the smb.conf file on the Ubuntu file server, which CAN see all the other shares, and both machines are running the same Ubuntu version.  Any idea what could cause this one machine to discriminate against Windows and Xandros shares?

---

### Post by ayenack on 2008-06-10
Try this.

The Print Server.

**System->Administration->Printing**

**Server Settings**

**Share published printers connected to this system**

**Allow users to cancel any job**

**Apply**

**Close**

The Client.

**System->Administration->Printing**

[B]Show shared printers from other systems

Apply

System->Administration->Printing

Refresh[/B]

You should see the shared printer.

Good luck.

---

### Post by joechummer on 2008-06-10
Well, now I feel a little foolish.  I'd been looking for something along the lines of "share this printer," and it didn't even register to me that "Server Settings" was a clickable menu -- probably because it lacked a disclosure triangle...

Thanks for the assistance.  Just telling Ubuntu to share the printer allowed every computer to print, without me needing to re-add the printer all over again.

---

### Post by joechummer on 2008-06-10
Anyone have insight as to why the one Ubuntu PC can't see anyone else's samba shares, aside from the one on my file server?

---

