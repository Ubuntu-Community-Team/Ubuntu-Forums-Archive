---
title: "Windows and Ubuntu - not getting along"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by count23 on 2008-02-01
Gday,

I've got two Ubuntu boxes, they're both running SAMBA, in a default configuration save changing the workgroup in smb.conf to the workgroup of my systems.

Now, they can't see anything. Not themselves, not other systems on the workgroup, nothing. They can ping other workgroup systems and the workgroup systems can see their shares (2003 and XP) nice and easily but the ubuntu machines can't seem to share the love. 

I'm not sure how to proceed with this, when the workgroup was left as "MSHOME" i could see a few other systems in place -> workgroup, but they were all the workgroup "workgroup" and not in the one that i'm after.

What have i missed that could be interfering with this? (I'm not experienced with SAMBA or linux)

Thanks,

---

### Post by ssuehr on 2008-02-01
Hmm.  From one of the Ubuntu systems, can you run:

smbclient -L<ip of the other system>

So like:

smbclient -L192.168.1.10

Just a thought.  That will list the shares available on the particular server.  I'm not sure if that gets you anywhere but it might show that the server isn't listening or isn't sharing.

---

