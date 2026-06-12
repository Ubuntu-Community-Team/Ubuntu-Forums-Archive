---
title: "Empty output processing pcap files"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by neil3 on 2014-02-26
Hi All,

I am trying to run a text file with a few known malicious IPs against a large number of pcaps contained in a directory... when I run the following command I see it iterating through each pcap for about 20-30mins but each time the output file is 0kb. Any ideas?

**find . -type f -name 1.pcap\* -print0 | xargs -n1 -0 tcpdump -nr | fgrep -wf /pathtomaliciousIPs.txt  > /pathtooutput.txt**


This is an fc20 machine&#8203;.

---

