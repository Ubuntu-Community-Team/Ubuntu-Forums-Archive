---
title: "software ipsec forwarder"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by ubuask on 2018-03-30
Hi,
I want to setup an ipsec forwarder "intranet A <-- firewall A --> internet <-- firewall B --> internet <-- firewall C --> intranet C".
the main reason for this is that connection between A-B-C is much better than A-C. 
someone has done this by using a hardware [https://supportforums.cisco.com/t5/vpn/asa-5500-as-an-ipsec-forwarder/td-p/1977906](https://supportforums.cisco.com/t5/vpn/asa-5500-as-an-ipsec-forwarder/td-p/1977906) .
but my firewall B will be on AWS or GCP and there is no ASA there.
is it possible to use ipsec-tool or StrongSwan on an ubuntu server to do the same job?
thanks for your help.

---

