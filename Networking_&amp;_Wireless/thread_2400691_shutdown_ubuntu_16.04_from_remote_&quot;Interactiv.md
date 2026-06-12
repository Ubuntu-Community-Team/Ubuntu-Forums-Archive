---
title: "shutdown ubuntu 16.04 from remote: &quot;Interactive Authentication Required&quot;"
date: 2018-09-08
forum: Networking &amp; Wireless
---

### Post by luca-dgh on 2018-09-08
My desktop runs Ubuntu 16.04, it works fine.
Now I have prepared the system with WOL to power on from remote  (normally from my android phone) and it works fine from LAN and from  WAN. I've a bunch of reasons to do this instead of keep it on 24/24.
The last step should be to shutdown the system from remote, I use an  android ssh client that log easily into my ubuntu box, but if I give the  command "shutdown -h 0" I receive the message:


 Interactive authentication required

 
From local command line I can shutdown the system without sudo.

 I understand that this is a security policy, but in my case I wish to override this policy, I'm the only user of the pc.
 Is it possible?
 Thanks a lot.

---

### Post by TheFu on 2018-09-09
Yes, it is possible. You'll still need to use sudo, but you can allow that command, with exactly those options, when requested by a specific userid, to be run without being asked for a password.  Does that help?

---

### Post by luca-dgh on 2018-09-09
Yes that helps, can you tell me how can I do that?

---

### Post by TheFu on 2018-09-10
> **luca-dgh said:**
> Yes that helps, can you tell me how can I do that?

 I only know it is possible, not the exact steps to accomplish it. I'd have to read the sudoers manpage to do that. I'm positive it is in there, since I've used it before. 
Sorry.

---

### Post by luca-dgh on 2018-09-10
Ok, thanks a lot for the info, I'll look at the sudoers man.

---

### Post by luca-dgh on 2018-09-11
ok, found it, now it works fine. Thanks a lot for the idea, I added this line to sudoers:

user_id ALL=(ALL:ALL) NOPASSWD: /sbin/shutdown

now I have to invoke sudo shutdown from remote, but no password is asked.

---

