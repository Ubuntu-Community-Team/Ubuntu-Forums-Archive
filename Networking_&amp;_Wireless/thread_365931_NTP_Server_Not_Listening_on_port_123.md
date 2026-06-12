---
title: "NTP Server Not Listening on port 123"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by igb on 2007-02-20
I have installed the ntp-server package, but it doesn't seem to be listening on port 123. Here is my ntp.conf:


```
logfile /var/log/ntpd.log

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org
server 127.127.1.0
fudge 127.127.1.0 stratum 13

#restrict default kod notrap nomodify nopeer noquery
restrict 192.168.0.0 mask 255.255.255.0 nomodify notrap
restrict 0.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery
restrict 1.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery
restrict 2.pool.ntp.org mask 255.255.255.255 nomodify notrap noquery

restrict 127.0.0.1
driftfile       /var/lib/ntp/drift
broadcastdelay  0.08

```

Running ntpq -p shows that it's working OK on the computer where it's installed. However, running nmap shows that the computer is not listening on port 123.

I notice that there is nothing in inetd.conf concerning port 123. Do I need to add something there?

Ian.

---

### Post by brandt on 2007-05-03
I have this problem as well.  Was anyone able to find a solution?

edit:
I should add that the machine in question is running feisty.  I (visually) compared the ntp.conf to one on a machine running edgy (whose ntpd does listen) and they appear to be the same.

---

### Post by johneynesanp on 2008-01-21
Hey guys,

Try this one.....

Add the below line on top of your ntp.conf file

"listen on *"

instead of * , you can specify your NTP Server IP on that place,
Now restart the NTP service...

---

### Post by kevdog on 2008-01-21
Make sure to open port 123 in your firewall.

---

