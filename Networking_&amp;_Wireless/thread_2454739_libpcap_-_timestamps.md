---
title: "libpcap - timestamps?"
date: 2020-12-04
forum: Networking &amp; Wireless
---

### Post by jaslit on 2020-12-04
[COLOR=#444444][/COLOR]Hi, I am trying to find info on network packet capture .pcap file timestamps and what they mean. Sent packets by A, received by C or intercepted by B?  I did see a post on this form with a link, but unable to find it again for some reason. I am using Wireshark and tcpdump. I need a detailed explanation who timestamps are stored and where in the packet (hex values and locations). Plz point me in the right direction. Thanks.

---

### Post by mattis13 on 2020-12-05
A computer forensic investigator had pasted a good writeup on this about 5 years ago. It describes the structure of Wiresharl .pcap, not tcpdump one. Here is the link [https://www.elvidence.com.au/understanding-time-stamps-in-packet-capture-data-pcap-files/](https://www.elvidence.com.au/understanding-time-stamps-in-packet-capture-data-pcap-files/)  

According to this guy .pcap timestamp is the time when the packet was captured by the machine running the capture. Sounds logical to me.

---

### Post by jaslit on 2020-12-05
Perfect. Thanks man.

---

