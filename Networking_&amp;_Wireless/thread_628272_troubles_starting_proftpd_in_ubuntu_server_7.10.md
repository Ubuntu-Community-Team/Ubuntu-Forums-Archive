---
title: "troubles starting proftpd in ubuntu server 7.10"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by hygum on 2007-12-01
i have troubles starting proftpd in command line in ubuntu server edition.

i can stop the program, but always when i start it, i get this error:

thomas@kodetslyst:/etc$ /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - notice: unable to listen to local socket: Address already in use
 - Fatal: SystemLog: unable to redirect logging to '/var/log/proftpd/proftpd.log': Permission denied on line 94 of '/etc/proftpd/proftpd.conf'
                                                                         [fail]

i've checked if other programs listens on the port 21, but there arent any.

---

### Post by jhnthn on 2007-12-01
Try using sudo to start it.

---

