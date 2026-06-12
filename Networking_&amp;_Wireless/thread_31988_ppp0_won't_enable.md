---
title: "ppp0 won't enable"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by Zephir on 2005-05-05
Hello people

A question from a ubuntu-rookie:
I have installed my ADSl-modem (siemens santis), did eciadsl-config-tk, everything ok so far but if I want to enable ppp0 in the network window it only enables one second or so.
So, this means no internet :-(

Does anyone know what the problem might be??

Respect!  ](*,) 
Bart

---

### Post by alastair on 2005-05-05
Check your log files for messages e.g.

/var/log/syslog

---

### Post by Zephir on 2005-05-05
Hm, the syslog only mentions "q"

---

### Post by alastair on 2005-05-05
What - it only contains "q"? I don't believe you!

No mention of "ppp" at all? No one can help unless you give us more information to go on.

---

### Post by Zephir on 2005-05-06
Hello again

Finally I have the syslog. Appreciate your help Alastair. 
My username is mentioned in pap-secrets and chap-secrets. 
The dsl-provider file says:

noipdefault
defaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtv 1492
usepeerdns

About ppp the syslog mentions:

May  6 20:03:40 localhost pppd[4005]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'

May  6 20:03:43 localhost pppd[4022]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
May  6 20:03:43 localhost pppd[4031]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
May  6 20:03:46 localhost pppd[4044]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
May  6 20:03:48 localhost pppd[4057]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'
May  6 20:04:37 localhost pppd[4175]: In file /etc/ppp/peers/ppp0: unrecognized option '/dev/modem'

I can't upload the complete file due to the kB limit.

Many thanks for analysing 

Bart

---

### Post by alastair on 2005-05-08
Do you have a /dev/modem device?

ls -l /dev/modem

YOu have an ADSL modem - this might be something configured via "pppoeconfig". I am not familiar with this - but it might set up the modem device as well.

---

### Post by Zephir on 2005-05-12
[QUOTE=alastair]Do you have a /dev/modem device?

ls -l /dev/modem

YOu have an ADSL modem - this might be something configured via "pppoeconfig". I am not familiar with this - but it might set up the modem device as well.[/QUOTE]

Hi alastair

/dev/ does not contain modem ??!! Shouldn't there be a trace of my adsl modem?

pppoeconfig worn't run but pppconfig does. I ran it and tried CHAP and pointed to /etc/eciadsl where the modemdriver is installed. No results

I also did pppoe-discovery > gives Timeout waiting for PADO packets: Succes 
And pppstats say > nonexistent interface 'ppp0' specified (pppstats ppp0 gives same)

I don't get it anymore  :|

---

