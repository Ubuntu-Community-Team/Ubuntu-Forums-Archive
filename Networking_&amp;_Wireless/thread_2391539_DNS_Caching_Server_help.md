---
title: "DNS Caching Server help"
date: 2018-05-10
forum: Networking &amp; Wireless
---

### Post by rickinfl on 2018-05-10
We have 5 branch offices each branch has a connection to 1 of our partners domain which we resolve using Unconditional Forwarders from our Domain Controller running DNS. I would like to setup a Caching DNS server at each brance that can resolve internal and partner names in case of lost connectivity to Domain Controller.

---

### Post by SeijiSensei on 2018-05-11
What help are you seeking exactly?  Ubuntu or CentOS Server with BIND9 can easily do this for you.  You could run it on a Raspberry Pi, on pretty much any older machine that was taken out-of-service, or in a virtual machine running on top of an existing machine.

A better approach than a caching server would be to designate the branch servers as slaves to the master DNS at headquarters.  The branch machines will keep a copy of the domain records from the main server.  When those records are updated, the main server will notify the slaves to update themselves.

---

### Post by rickinfl on 2018-05-11
I have a Windows Domain Controller running DNS. I have remote branches that use it for DNS. The main lines sometimes go down between locations and my remote locations go down because they are unable to resolve host names. I need some sort of DNS cache or something that will keep them running until they can contact the Domain DNS server again.

I've been trying to figure out if unbound will work. I didn't really want to mess with the Windows Server DNS if possible. Just something that would pull from it and store at each location.

---

### Post by SeijiSensei on 2018-05-11
You should be able to set up a master/slave relationship pretty easily.  I've not used Windows DNS, but you could start by reading the comment from "rootwyrm" here:  [https://www.reddit.com/r/homelab/comments/3zqg2y/using_bind_linux_as_a_backup_dns_server_to_a/](https://www.reddit.com/r/homelab/comments/3zqg2y/using_bind_linux_as_a_backup_dns_server_to_a/)

I have no idea what "unbound" is.

---

