---
title: "problem the Ubuntu bind9 named process 99% cpu usage issue(help)"
date: 2017-09-12
forum: Networking &amp; Wireless
---

### Post by m0o0hammad on 2017-09-12
hello everyone 
please help
top:
 PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                         
[COLOR=#ff0000]** 4162 root      20   0  810684 622308   3904 S 113.1  7.5   8938:15 named**  [/COLOR]                                                                                                                         
  219 root      20   0   20576  14996  14888 S  12.3  0.2   2591:35 systemd-journal 


dnstop eth0:
Queries: 3200 new, 11711 total                                                                                                                                             

Sources             Count      %   cum%
--------------- --------- ------ ------
(ip public)          7403   63.2   63.2
(ip public)           171    1.5   64.7
5.223.250.223         161    1.4   66.0
5.223.200.87          128    1.1   67.1
217.219.212.162       125    1.1   68.2
5.223.208.161          61    0.5   68.7
5.220.83.7             54    0.5   69.2
5.223.227.140          53    0.5   69.6


cpuinfo:
Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz       (8core)




taskset -p 4162:
pid 4162's current affinity mask: ff

What can I do to reduce CPU?

---

### Post by SeijiSensei on 2017-09-12
The first question is, is this a server or a desktop machine?  If the latter, why is it running named at all?

Have you looked at /var/log/syslog yet?  Are there lots of entries from "named"?  If so, post a few of them here inside [noparse]```

```[/noparse] tags so they will be easier to read.

---

### Post by m0o0hammad on 2017-09-13
Yes, I looked and these logs are relevant

```

Sep 13 06:25:41 DNS named[4162]: error (network unreachable) resolving 'facebook.com/DS/IN': 2001:7fd::1#53
Sep 13 06:25:41 DNS named[4162]: DNS format error from [COLOR=#ff0000](ip public)[/COLOR]#53 resolving gfycat.com/DS: reply has no answer
Sep 13 06:25:41 DNS named[4162]: error (FORMERR) resolving 'gfycat.com/DS/IN': [COLOR=#ff0000] (ip public)[/COLOR]#53
Sep 13 06:25:41 DNS named[4162]: error (network unreachable) resolving 'gfycat.com/DS/IN': 2001:500:12::d0d#53

```

It should be noted that a series of sites such as Facebook have been filtered by ourselves

---

