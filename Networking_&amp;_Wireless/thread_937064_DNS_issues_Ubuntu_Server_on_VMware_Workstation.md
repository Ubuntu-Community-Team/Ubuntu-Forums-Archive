---
title: "DNS issues Ubuntu Server on VMware Workstation"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by centraltimezonemonkey on 2008-10-03
I am running an Ubuntu server on a VMware workstation with a bridged connection.  IP is configured correctly as well as hosts file to our test DNS servers.  There is another failover cluster of DNS server that I do not want to go to.  

If I run nslookup based on the machine name I resolve to the correct fully qualified name.  However if I run nslookup on my ip address I resolve with a non-authoritative source to another server.  Furthermore I am using ultramonkey on this server to loadbalence 2 Micro$oft IIS servers. (I know, I know but, its a requirement for the environment)  The ldirectord queries the webservers every second over port 80 to a website I have specified on the IIS server.  If I do a netstat on the IIS server while this query is happening my ubuntu server comes across with the fully qualified domain name of the unwanted DNS.  

Question is how the heck do I force my DNS to the DNS servers I want?  I think I am missing something small and I just cant quite find the right files to be messing with.  I have scoured the internet to see how to force my DNS to certain servers but just cant find it.  

Please let me know if you need any more info.  I am thinking this may be something with the Ubuntu server picking off some sort of config/dns from the host machine since it is a VM slice.  Thinking about dedicated a box to my ubuntu server but would rather run in VM. 

Thanks for any help or assistance.

---

