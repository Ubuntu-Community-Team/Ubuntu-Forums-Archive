---
title: "weird dns issue"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by aleahey on 2005-06-08
i dont know if anyone else has run in to this, but, here goes.

i use a dlink dwl-650+ card, but thats besides the point, because this problem has happened on a few cards ive used.

every once in a while my DNS servers get changed. theres my 2 normal ones, but when it changes it doubles the second one, and adds a 192.168 ip as the first. 

an example, the right servers:

100.100.100.1
100.100.100.2

servers after this mysterious switchup:

192.168.100.2
100.100.100.1
100.100.100.2
100.100.100.2

any thoughts?

---

### Post by alastair on 2005-06-08
This is DHCP?
What is "serving" you the DNS values? A router/modem?

Check your system logs (/var/log/syslog) e.g.

tail -f /var/log/syslog

and see if you can see this happen.

---

### Post by aleahey on 2005-06-08
yeah a wireless router, dell truemobile something or other. G/B router, B card.

checkin sys logs now, thanks.

update: all ive got in the sys log is:

Jun  8 20:05:12 localhost kernel: tx: error occurred (0x20)!! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Jun  8 20:05:12 localhost kernel: less than 5 minutes since last radio recalibration (maybe card too hot?): not recalibrating!

---

