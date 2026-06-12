---
title: "chkrootkit log help needed."
date: 2009-08-25
forum: New to Ubuntu
---

### Post by newbee70 on 2009-08-25
Folks, I need help determining what lines 117 and 118 are telling me.
has chkrootkit actually found something, and do I need to take any actions.

any and all help will be appreciated. and TIA,

Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... /usr/bin/find: //home/me/.gvfs: Permission denied
/usr/bin/find: //home/me/.gvfs: Permission denied
nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
117 Checking `sniffer'... lo: not promisc and no packet sniffer sockets
118 eth1: PACKET SNIFFER(/sbin/dhclient3[5917])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected

---

### Post by cariboo on 2009-08-26
> 118 eth1: PACKET SNIFFER(/sbin/dhclient3[5917])

That just means that your system is has recieved an ip address via dhcp, and the service is still running just in case a new ip address is needed. There is nothing to worry about.

---

### Post by newbee70 on 2009-09-02
> **cariboo907 said:**
> That just means that your system is has recieved an ip address via dhcp, and the service is still running just in case a new ip address is needed. There is nothing to worry about.

Sorry about taking so long to reply, "I have been out of town since posting the request for help". 

Thank you for explaining that it was just a dhcp request. Now my only question is why I have never seen this occur before. But: I won't lose any sleep over it, and I won't worry about leaving my system running without supervision.

---

