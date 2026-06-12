---
title: "Multiple Users: Samba working fine - fstab question"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by tracyapotter on 2007-01-04
Hello,

Things were working fine and then oddness struck.  When I got back from the holidays I lost the ability to move or delete files located on a peer-to-peer XP machine using my /media links.  If I work using a konqueror smb:/ interface things are working perfectly.

I have multiple Kubuntu, XP, NT machines all tied together peer-to-peer, all with User, Company, and Guest users on each machine of each type.  Now the Kubuntu boxes can move things around on the other machines, just not FROM the Kubuntu boxes TO the others. FROM the Winboxes TO the Kubuntu boxes is good.

The fstab line looked like this:
//pwrconsrvr1/Projects	/media/Projects	smbfs	credentials=/root/.smbcredentials	0	0

(.smbcredentials being the windows login and password of course)

The only thing that gets me able to move things around successfully is to add the UID as follows:
//pwrconsrvr1/Projects	/media/Projects	smbfs	credentials=/root/.smbcredentials,_uid=1000_	0	0

but that only fixes User 1000.

gid, umask, etc are not seeming to do the trick.

Anyone else have this recent change/problem?  I used to have such a simple fstab, now it looks like things are going to get complicated.

I am not discounting that a windows upgrade could also have caused a problem, their sharing just has so few options now that there is not much that I can do on that end.

Thanks 

TA Potter

---

