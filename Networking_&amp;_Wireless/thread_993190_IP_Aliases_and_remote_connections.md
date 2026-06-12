---
title: "IP Aliases and remote connections"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by dwinner on 2008-11-25
Hi all,


I've been finding that when I have more than one IP address bound to an interface, when I make a remote connection to another resource, the connection is made using one of the IP aliases instead of the main IP address. 

This is a problem particularly for NFS, because I would like to set up my /etc/exports to accept connections from a single IP, not an entire range. Consider:

Host A (NFS Client):
Main IP Address (eth0): 10.20.20.6/16
1st IP Alias (eth0:0): 10.20.200.1/16
2nd IP Alias (eth0:1): 10.20.200.1/16

Host B (NFS Server):
One IP Address (eth0): 10.10.30.1/16
In /etc/exports I have:

/home/nfsshare       10.20.20.6(rw,sync,no_subtree_check)


When I attempt to mount that NFS from Host A, it is rejected, because of server deny. I found that it is because Host A is connecting from IP "10.20.200.1", NOT "10.20.20.6". If I change /etc/exports to accept from "10.20.200.1", then it works. 

The problem with this is that the aliases are "dynamic", as in they are being bound for Apache Virtual Hosts, so they may be there one day, but not the next. I know I could make /etc/exports accept from "10.20.*.*", but I would like to make it as secure as possible.

Can anybody tell me why the NFS client is connecting as the 3rd IP address bound instead of the main (eth0) address? And is there a way to control this?


Thanks!

DW

---

