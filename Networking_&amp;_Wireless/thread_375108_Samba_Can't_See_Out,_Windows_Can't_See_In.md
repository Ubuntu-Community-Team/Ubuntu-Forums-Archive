---
title: "Samba Can't See Out, Windows Can't See In"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by sog on 2007-03-03
I've seen a host of other Samba related threads, but the vast majority seem to be about problems viewing external networks from Ubuntu. I've got that problem, but also have the added complication that none of the other machines on the network (Ubuntu + Windows) can see this Ubuntu machine. 

Here's the deal:

Platform: 
Edgy

Package Versions (all four have been reinstalled): 
samba          3.0.22-1ubuntu a LanManager-like file and printer server fo
smbclient      3.0.22-1ubuntu a LanManager-like simple client for Unix
smbfs          3.0.22-1ubuntu mount and umount commands for the smbfs (for
libgnomevfs2-e 2.16.1-0ubuntu GNOME virtual file-system (extra modules)

Problem Description: 
Samba has worked since the machine was runner Dapper and subsequently upgraded to Edgy, although it or Nautilus used to be fickle - I'd have to refresh the window multiple times to get various other machines on the network visible and browsable. 

As of yesterday, however, either Samba or Nautilus has ceased working. Now when I browse the same workgroup that I always have. Nothing in the network configuration has changed, and as far as I'm aware no packages have recently been installed that would affect Samba and/or Nautilus. Further, the other networked machines, as mentioned, cannot see this machine in their available network. 

It's not a network problem per se, b/c I can still print via CUPS and ping the local router/access point. I just can't browse anything via Samba. 

Any suggestions would be appreciated - particularly when it comes to what to look for in /var/log/samba. Thanks.

---

### Post by ingo on 2007-03-04
Odd behaviour indeed. Did you do any updates, touch any cables?

---

### Post by sog on 2007-03-04
unfortunately, no. that's what i can't figure. nothing important, as far as i can tell, has changed, but it just won't show me the SMB shares.

---

