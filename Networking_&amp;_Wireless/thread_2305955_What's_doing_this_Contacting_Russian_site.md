---
title: "What's doing this? Contacting Russian site"
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by lindsayward on 2015-12-10
I think I have a few issues...
My ADSL Internet is going very slowly because my Ubuntu 14.10 PC is hogging it (uploads mostly). If I unplug this computer the rest of the devices on the network get good speeds.

When I run **sudo tcpdump -i any -q**
I get:
```
08:51:55.171747 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.171764 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
08:51:55.206578 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.206592 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
08:51:55.241726 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.241764 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
08:51:55.283771 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.283788 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
08:51:55.319400 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.319417 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
08:51:55.364929 IP 5x18x158x83.static-business.iz.ertelecom.ru.35154 > htpc.http: tcp 0
08:51:55.364957 IP htpc.http > 5x18x158x83.static-business.iz.ertelecom.ru.35154: tcp 1452
```

.ru is a Russian domain and the only websites I could find anything about this on said it was a "communications site". I'm pretty sure that's not supposed to be happening!
What's going on with this, and how do I track it down?
I restarted and it's the same.

When I run **sudo nethog**
I see uploads from **/usr/sbin/apache2**
I'm running MythTV so I do expect Apache to be running for MythWeb but I don't know why it's uploading so much. Sometimes I see several entries for apache2.

Any help tracking this down would be much appreciated.
Thanks!

---

