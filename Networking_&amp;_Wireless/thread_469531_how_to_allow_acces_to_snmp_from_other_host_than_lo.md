---
title: "how to allow acces to snmp from other host than localhost?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by sammael666 on 2007-06-10
hi

i have two machines on my network, each of the running kubuntu feisty fawn. on both machines i set up snmp, and i've confirmed it is working by issuing snmpwalk -v 1 -c public localhost on each host.
i am using cacti to monitor one of these machines and i would like it to monitor the other one as well. but i do not know how to set up snmpd.conf properly to allow access not only from localhost, but from other ip also.

i tried to edit snmpd.conf myself but it only resulted in not being able to connect to snmp even from localhost, so i now have original snmpd.conf file as installed by apt-get. what line do i need to insert there to allow host with ip aaa.bbb.ccc.ddd to read snmp info from localhost?

any help is appreciated

---

### Post by Deano1123 on 2007-06-27
Just bumping this as I also have the same problem.  Can anybody shed any light?

---

### Post by Ysbeer on 2007-06-28
I also have this problem... Will also appreciate any advice.

---

### Post by RaySeys on 2007-06-29
You need to edit /etc/default/snmpd

change the line

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

to

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid'

then do /etc/init.d/snmpd restart

---

