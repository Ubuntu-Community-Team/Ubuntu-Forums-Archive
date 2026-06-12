---
title: "How use libpcap on Ubuntu in Virtual Box (Cannot find the existent interfaces)"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by artss2 on 2016-03-11
I used such Vbox iamges as Ubuntu 10.04, Xubuntu 12.04, with installed libpcap and libpcap-dev libraries, and workable ifconfig and tcpdump. But when trying to find the devices I got "no interfaces found", despite tcpdump/ifconfig reveals it. When checking geteuid() I got 1000 (and after setting seteuid(0) it appears the same), but not 0 (as root). So I understand it deals with super-user permissions, When I set chmod 777 -R / for the whole system I got just usbmon0, but not eth0 and lo? What is up? Does virtual machine and its network settings blocks packet siniffing? Why I cannot set account to root user 0? Where eth0 and lo are lost, as just usbmon0 appears or it is just due the fact usbmon is the first device that appera in pcap_lookupdev()?
And the behaviour the same in Ubuntu 10.04 and Xubuntu 12.04/
Can I try to use Ubuntu Server vbox image? Are the expectation that situation could change? Does Ubuntu server support libpcap, gcc, and codeblocks?

---

