---
title: "Rsyslog drops occasional hostnames."
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by mcparty2 on 2016-07-19
I thin Rsyslog is stripping the hostnames or i have a DNS issue... 

```

Jul 19 09:59:52 192.168.10.23  Test Syslog.

```

TCP Dump:

```

tcpdump -l -i eth0 port 514
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
10:00:13.027824 IP ups1.domain.com .55070 > 192.168.10.50.syslog: SYSLOG user.emergency, length: 48

```

I can ping the hostname without issue which would imply rsyslog is ignoring the hostname being sent.

```

ping ups1.domain.com
PING ups1.domain.com (192.168.10.23) 56(84) bytes of data.
64 bytes from ups1.domain.com (192.168.10.23): icmp_req=1 ttl=252 time=7.74 ms
64 bytes from ups1.domain.com (192.168.10.23): icmp_req=2 ttl=252 time=6.82 ms
64 bytes from ups1.domain.com (192.168.10.23): icmp_req=3 ttl=252 time=6.84 ms

```

Has anyone else had this problem? or can suggest a solution?

Thanks

---

### Post by SeijiSensei on 2016-07-19
You probably don't have reverse DNS set up for those machines.  Your ping test uses a forward lookup from the hostname to its IP address. The entries in syslog use the reverse process.  They log the activities by IP address, then see if they can resolve the address to its hostname using the reverse records.  So you would need to add a zone file for 10.168.192.in-addr.arpa with a PTR entry that points address 23 to ups1.domain.com.

---

### Post by mcparty2 on 2016-08-11
Thanks for the info. Much appreciated. What you've said makes sense (sorry it has taken so long to return your message)
Just to add closure, I managed to get it working by copying another rsyslog.conf file across and ensuring all nodes were listed in the local hosts file. Unfortunately i didn't get to diff the two files first otherwise i'd maybe have had something else to throw in to the mix.

Thanks

---

