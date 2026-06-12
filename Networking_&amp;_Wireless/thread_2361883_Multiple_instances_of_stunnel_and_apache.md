---
title: "Multiple instances of stunnel and apache"
date: 2017-05-21
forum: Networking &amp; Wireless
---

### Post by JimLS on 2017-05-21
I am having trouble sending email from a Beagle Bone running Ubuntu 14.04.  It was working but has lately been only working occasionally.  A script I have quit sending out status emails and I am trying to figure out why.  I shut down and restarted and it worked for two emails and then quit.  Looking at the running processes with 
ps aux
I see 6 instances of stunnel and 6 of apache which does not see right.  This is the output:

```

root      1813  0.0  0.0   3304   492 ?        S    21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1814  0.0  0.0   3304   492 ?        S    21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1815  0.0  0.0   3304   492 ?        S    21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1816  0.0  0.0   3304   492 ?        S    21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1817  0.0  0.0   3304   492 ?        S    21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1818  0.0  0.1   3304   668 ?        Ss   21:10   0:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
root      1890  0.7  2.7 107668 14028 ?        Ss   21:10   0:00 /usr/sbin/apache2 -k start
asterisk  1899  0.0  0.9 107700  4776 ?        S    21:10   0:00 /usr/sbin/apache2 -k start
asterisk  1900  0.0  0.9 107700  4776 ?        S    21:10   0:00 /usr/sbin/apache2 -k start
asterisk  1901  0.0  0.9 107700  4776 ?        S    21:10   0:00 /usr/sbin/apache2 -k start
asterisk  1902  0.0  0.9 107700  4776 ?        S    21:10   0:00 /usr/sbin/apache2 -k start
asterisk  1903  0.0  0.9 107700  4776 ?        S    21:10   0:00 /usr/sbin/apache2 -k start


```

Any idea what is happening or how to fix this?

---

