---
title: "Bind9 master/slave transfer"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-07-23
Hey Forum. 
I'm installing bind9 for testing some issues around bind9 and run into a problem. 

I have followed this guide for Master/Slave setup [http://ubuntuforums.org/showthread.php?t=391601&highlight=bind+master+file](http://ubuntuforums.org/showthread.php?t=391601&highlight=bind+master+file)
 and after restarting bind9 at the slave server and looking into the /var/log/syslog I'm getting this error: 
Jul 23 08:57:22 quark named[4125]: zone xxxxxxx.com/IN: Transfer started.
Jul 23 08:57:22 quark named[4125]: transfer of 'xxxxxxx.com/IN' from 192.168.2.7#53: connected using 192.168.2.10#54939
Jul 23 08:57:22 quark named[4125]: dumping master file: /etc/bind/tmp-fML4bO0Tov: open: permission denied
Jul 23 08:57:22 quark named[4125]: transfer of 'xxxxxxx.com/IN' from 192.168.2.7#53: failed while receiving responses: permission denied
Jul 23 08:57:22 quark named[4125]: transfer of 'xxxxxxx.com/IN' from 192.168.2.7#53: end of transfer

Which permission is it here that goes wrong? The zones defination for Master:
zone "xxxxxxx.com" {
        type master;
        file "/etc/bind/db.xxxxxxx.com";
        allow-transfer { @192.168.2.10; };
};

And the zone for slave:

zone "xxxxxxx.com" {
        type slave;
        file "/etc/bind/db.xxxxxxx.com";
        masters { 192.168.2.7; };
};

I have tried all things but stills getting error: 
Jul 23 10:24:10 quark named[4037]: zone xxxxxxx.com/IN: refresh: retry limit for master 192.168.2.7#53 exceeded (source 0.0.0.0#0)
Jul 23 10:24:10 quark named[4037]: zone xxxxxxx.com/IN: Transfer started.
Jul 23 10:24:10 quark named[4037]: transfer of 'xxxxxxx.com/IN' from 192.168.2.7#53: failed to connect: connection refused
Jul 23 10:24:10 quark named[4037]: transfer of 'xxxxxxx.com/IN' from 192.168.2.7#53: end of transfer



Thanks

---

### Post by terrrorr on 2007-07-23
Hello,

Check this post for more information. I had the same problem as you can see...

[http://ubuntuforums.org/showthread.php?t=267974&highlight=bind9&page=2]("http://ubuntuforums.org/showthread.php?t=267974&highlight=bind9&page=2")

- terrrorr -

---

### Post by Mr. C. on 2007-07-24
The named process does not have write permission to the /etc/bind directory.

MrC

---

