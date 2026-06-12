---
title: "Unable to sync time using `ntpdate`, error: “no server suitable for synchronization&quot;"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by AncientPC on 2011-06-18
My ntp.conf file:

```
    user@pc[0][07:37:40]:/etc$ cat /etc/ntp.conf
    idriftfile /var/lib/ntp/ntp.drift
    server 0.pool.ntp.org
    server 1.pool.ntp.org
    server 2.pool.ntp.org
    server pool.ntp.org

```
Command output:

```
    user@pc[0][07:37:24]:/etc$ sudo ntpdate -dv pool.ntp.org
    18 Jun 07:37:35 ntpdate[10737]: ntpdate 4.2.4p8@1.1612-o Tue Apr 19 07:15:05 UTC 2011 (1)
    Looking for host pool.ntp.org and service ntp
    host found : conquest.kjsl.com
    transmit(198.137.202.16)
    transmit(216.45.57.38)
    transmit(64.6.144.6)
    transmit(198.137.202.16)
    transmit(216.45.57.38)
    transmit(64.6.144.6)
    transmit(198.137.202.16)
    transmit(216.45.57.38)
    transmit(64.6.144.6)
    transmit(198.137.202.16)
    transmit(216.45.57.38)
    transmit(64.6.144.6)
    transmit(198.137.202.16)
    transmit(216.45.57.38)
    transmit(64.6.144.6)
    198.137.202.16: Server dropped: no data
    216.45.57.38: Server dropped: no data
    64.6.144.6: Server dropped: no data
    server 198.137.202.16, port 123
    stratum 0, precision 0, leap 00, trust 000
    refid [198.137.202.16], delay 0.00000, dispersion 64.00000
    transmitted 4, in filter 4
    reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    originate timestamp: 00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    transmit timestamp:  d1a71a93.1f16c1e3  Sat, Jun 18 2011  7:37:39.121
    filter delay:  0.00000  0.00000  0.00000  0.00000
             0.00000  0.00000  0.00000  0.00000
    filter offset: 0.000000 0.000000 0.000000 0.000000
             0.000000 0.000000 0.000000 0.000000
    delay 0.00000, dispersion 64.00000
    offset 0.000000
    
    server 216.45.57.38, port 123
    stratum 0, precision 0, leap 00, trust 000
    refid [216.45.57.38], delay 0.00000, dispersion 64.00000
    transmitted 4, in filter 4
    reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    originate timestamp: 00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    transmit timestamp:  d1a71a93.524a05dd  Sat, Jun 18 2011  7:37:39.321
    filter delay:  0.00000  0.00000  0.00000  0.00000
             0.00000  0.00000  0.00000  0.00000
    filter offset: 0.000000 0.000000 0.000000 0.000000
             0.000000 0.000000 0.000000 0.000000
    delay 0.00000, dispersion 64.00000
    offset 0.000000
    
    server 64.6.144.6, port 123
    stratum 0, precision 0, leap 00, trust 000
    refid [64.6.144.6], delay 0.00000, dispersion 64.00000
    transmitted 4, in filter 4
    reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    
    transmitted 4, in filter 4
    reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    originate timestamp: 00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    transmit timestamp:  d1a71a93.524a05dd  Sat, Jun 18 2011  7:37:39.321
    filter delay:  0.00000  0.00000  0.00000  0.00000
             0.00000  0.00000  0.00000  0.00000
    filter offset: 0.000000 0.000000 0.000000 0.000000
             0.000000 0.000000 0.000000 0.000000
    delay 0.00000, dispersion 64.00000
    offset 0.000000
    
    server 64.6.144.6, port 123
    stratum 0, precision 0, leap 00, trust 000
    refid [64.6.144.6], delay 0.00000, dispersion 64.00000
    transmitted 4, in filter 4
    reference time:    00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    originate timestamp: 00000000.00000000  Thu, Feb  7 2036  0:28:16.000
    transmit timestamp:  d1a71a93.857c6fbd  Sat, Jun 18 2011  7:37:39.521
    filter delay:  0.00000  0.00000  0.00000  0.00000
             0.00000  0.00000  0.00000  0.00000
    filter offset: 0.000000 0.000000 0.000000 0.000000
             0.000000 0.000000 0.000000 0.000000
    delay 0.00000, dispersion 64.00000
    offset 0.000000
    
    18 Jun 07:37:40 ntpdate[10737]: no server suitable for synchronization found
```

---

