---
title: "Samba won't start - Kubuntu Dapper"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by r.cannell on 2006-12-04
I installed Samba and set up smb.conf and the computer and its shared files appeared on my home network. Next time the computer was started it did not appear on the network. Samba appears under services.

When trying to start Samba manually using:

/etc/init.d/samba start

I get the following message:

/etc/init.d/samba start
 * Starting Samba daemons...                                                    install: cannot change owner and/or group of `/var/run/samba': Operation not permitted       

I have set the permissions so that user, group and others can read and write to the folder, but still doesn't work.

Any ideas?

---

