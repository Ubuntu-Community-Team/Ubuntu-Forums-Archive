---
title: "pppd not working"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by damansandhu on 2007-09-05
hi , i am using dsl connection and i connect internet by bridging , so i setup dialup connection on ubuntu by command "pppoeconf" and i choosed to automatically connect internet during bootup , it was working fine but now its not working , i dont know what happened to it , so i am connecting internet by pppoe(in which we insert username and pass in router). But i want to connect internet by dailing(pppd).

---

### Post by damansandhu on 2007-09-05
somebody help plz

---

### Post by damansandhu on 2007-09-06
i need some help plz

---

### Post by damansandhu on 2007-09-06
i think this might help


daman@Ultimate:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
daman@Ultimate:~$ plog
Sep  6 02:54:32 Ultimate pppd[6537]: PPP session is 5590
Sep  6 02:54:32 Ultimate pppd[6537]: Using interface ppp1
Sep  6 02:54:32 Ultimate pppd[6537]: Connect: ppp1 <--> eth0
Sep  6 02:54:32 Ultimate pppd[6537]: PAP authentication succeeded
Sep  6 02:54:32 Ultimate pppd[6537]: peer from calling number 00:90:1A:41:EA:39
authorized
Sep  6 02:54:32 Ultimate pppd[6537]: Cannot determine ethernet address for proxy
 ARP
Sep  6 02:54:32 Ultimate pppd[6537]: local  IP address 122.162.15.163
Sep  6 02:54:32 Ultimate pppd[6537]: remote IP address 202.56.215.134
Sep  6 02:54:32 Ultimate pppd[6537]: primary   DNS address 202.56.215.55
Sep  6 02:54:32 Ultimate pppd[6537]: secondary DNS address 202.56.215.54
daman@Ultimate:~$ plog
daman@Ultimate:~$
daman@Ultimate:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ poff
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem                                            '
daman@Ultimate:~$ plog
Sep  6 02:55:36 Ultimate pppd[6537]: Terminating on signal 15
Sep  6 02:55:36 Ultimate pppd[6537]: Connect time 1.1 minutes.
Sep  6 02:55:36 Ultimate pppd[6537]: Sent 0 bytes, received 0 bytes.
Sep  6 02:55:36 Ultimate pppd[6537]: Connection terminated.
Sep  6 02:55:36 Ultimate pppd[6537]: Exit.
Sep  6 02:55:48 Ultimate pppd[6638]: In file /etc/ppp/peers/provider: unrecogniz                                            ed option '/dev/modem'
daman@Ultimate:~$ pon dsl-provider

---

### Post by damansandhu on 2007-09-06
somebody plz help

---

