---
title: "Trouble Networking Vmware Server with two nic"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by dacky on 2007-03-26
As a school, we have an ubuntu Dapper server with DHCP, masqerade, firewall, dansguardian, squid that does three separate vlans.  We got a second interent line for students (they were using too much band width).  We can't easily deploy another server.  I am trying to make it so that we can have two internet connections being served by one computer:  2 vlans for office and faculty using 1 internet connection, and 1 vlan for students using the new internet connection (thus, they fight each other for bandwidth).

I tried a firewall script, but could get networking to work.  Next, we tried using a vmware server to run the same ubuntu setup but for the student network and internet connection.  Thus, two servers, one computer, 2 internet connections, 3 vlans.

Host server
eth0 internet 1
eth1 office
eth2 faculty

Vmware server
eth3 student
eth5 internet 2

If we get the vmware internet working, it messes up the host.  Can anyone give us some guides as to which steps to follow to make this all happen, or perhaps a third alternative?  Our server has 1 gig ram and good processor.

Do we want to bridge or nat on the vmware server?
Do we need to configure eth3 and eth5 on the host and on the virtual server?
Thanks.

---

