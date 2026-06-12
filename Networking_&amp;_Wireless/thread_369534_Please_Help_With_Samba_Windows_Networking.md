---
title: "Please Help With Samba Windows Networking?"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by sbennettgso on 2007-02-24
I imagine the information I'm looking for is here somewhere, but it seems pretty disjointed.

I have a networked setup as follows:

Cable modem connected to 4-port router
Two desktops connected to the router, one XP (A), one Ubuntu 6.10 (B)

I also have a wireless AP connected to the router, and I have one Ubuntu 6.10 machine (C) connected to the network wirelessly.

I installed Samba on (B).  All three computers can print to the printer on (A), and all three can see shared folders on (A) and (B).  But no one can see anything on (C).

I believe I configured (B) as a WINS server per: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba")

Samba appears to be installed on (C) as well.  Is there anything I need to do to the Samba setup on (C) so its shared folders can be seen on (A) and (B)?  It's not clear to me from the above link that I need to do anything for (C).  But it's not clear that I don't, either, as these directions seem to concentrate on a two-computer peer-to-peer network.

Any help would be appreciated.

Thanks,
Scott

---

### Post by mlarsendk on 2007-02-25
Hi!

Are you able to ping the (C) machine from (A) and (B)? And can you ping from (A) and (B) to (C)?

If you want to access stuff on (A) and (B) from (C) you need to try out smbclient first and post some information about the results. If you don't have it you might want to do an apt-get install smbclient (I think the package is called that, but I'm not sure)

If you want to access stuff on (C) from (A) and/or (B) you need to setup samba server on C (apt-get install samba smbfs as root and then configure smb.conf)

I hope this points you in the right direction :-)

Best regards,
Michael Larsen

---

