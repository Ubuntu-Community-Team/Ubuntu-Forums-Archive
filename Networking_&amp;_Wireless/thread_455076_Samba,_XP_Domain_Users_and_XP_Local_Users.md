---
title: "Samba, XP Domain Users and XP Local Users"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by AsGF2MX on 2007-05-26
I have Samba 3 running and I have it setup as a PDC and working roaming profiles + folder redirection and all the users authenticate fine. It's just that I can't seem to figure out a way to grant them rights to do things. Say I have the following users with the following requirements:

These two users need to be able to install and run games on their PCs (These guys must be Power Users):
Mr. GameA
Mr. GameB
These users just use the machines "as is" (These guys must be standard users):
Mr. Workaholic
Mr. Browseaholic
Mrs. Chataholic   
The core admin user (The Administrators):
Mr. Neo 

One special requirement is that the machines must be able to authenticate itself without access to the domain at some times (so far the caching seems to work but I have not altered the "csc" setting on the smb.conf). How do I ensure this works all the time?The other problem is that it seems to me that Domain and Local Users are not tied up so the domain admin can't administer the PC remotely.

I also can't seem to find a way to use mmc to alter the settings on the samba server (for policies...the NT policy thing mentioned the to Samba  How to book is a little puzzling). I am using the tdbsam back-end (ldap seemed pretty damn daunting and so I might try it later down the road BUT I need to get the system up and running ASAP before I get stoned to death:popcorn:).

Any help would be greatly appreciated.

---

