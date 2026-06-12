---
title: "DHCP keeps renewing after a switch to static IP"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by mike_d on 2006-10-16
Here's a wierd problem that I've never seen before, and I would love some help.

Before this weekend I had an old P166 running gentoo acting as the firewall between my DSL modem and the rest of the house.  The hard drive was starting to go flaky on the P166, so rather than Invest any more time resinstalling and setting up the firewall again, I just bought a Linksys WRT54G wireless router to replace the P166.  The other comptuers in the house were setup with DHCP and i used dnsmasq on the P166 as my DNS/DHCP server.  Since the new router's DHCP server didn't have a DNS system where I could (easily) map a DNS name to a MAC address, I decided that it would be easier to run static IPs behind the router so that I could then just use a static hosts file for the naming.

Here's comes the wierd pard:  I changed my Ubuntu (Dapper with all the latest updates) comptuers to a static IP by editing the "/etc/network/interfaces" file.  And then I restarted the netowrking with "/etc/init.d/networking restart" and all was fine.  Then 24 hours later (the default DHCP renew time) the IP of the Ubuntu computers changes to one in the DHCP assigned block - which caused all the nfs clients to be very unhappy (I kept DHCP on, so when I have visitors, they can just plug in and go).  So I log back into the Unbuntu computer, rerun "/etc/init.d/networking restart" and all is well again - for another 24 hours!  

I did a "ps -ef | grep dhcp" to find any DHCP clients running that may be trying to renew every 24 hours, but can't find anything.  I assume that the DHCP client (my Ubuntu computer) has to initiate the DHCP renewal, so that's why I'm posting the question here.

This has happened on my 3 Ubuntu comptuers, but not my 2 Mac OS X computers, all of which were switched from DHCP clients to static IP when I replaced the router.

Any Ideas?

Mike

---

### Post by ricks1950 on 2006-10-16
Ubuntu has the Administration application to set up your networking, which you by-passed by editing the files.  I'd bet a cookie that the GUI app also modifies a script to renew your DHCP lease.

---

### Post by sitedesign on 2006-10-16
It's a strange one that I too have seen. It seems the DHCP client checks the renewal of the IP from the DHCP server but does not check if a fixed IP has been set. I assume that is done during start-up (DHCP client checks if fixed or DHCP). If you simply set the IP in /etc/network/interfaces then restart the computer you should find that it keeps the fixed IP just fine.

I guess there is a way of killing DHCP client so that it doesn't try to renew.

---

### Post by ricks1950 on 2006-10-17
System=>Administration=>Networking modifies /etc/network/interfaces AND configures DHCP client to renew -- if you simply modify /etc/network/interfaces you miss a piece of the configuration.  Not sure where to change the client.  

DHCP is initiated from the client.  Lease duration is a parameter passed by the server.

---

### Post by handy on 2006-10-17
Is it possible that a solution lies in the **/etc/dhcp3/dhclient.conf** file?

I know very little about this stuff, but a solution to a long term seemingly spontaneous change of DNS server address's came down to one simple line needing to be added to the dhclient.conf file.

Anyway, all the best.

---

### Post by mike_d on 2006-10-23
Just an update for those who care:

I was unable to find any DHCP client service that I could stop.  So I resorted to a reboot and all is well now.  

Mike

---

### Post by Iowan on 2006-10-24
> **mike_d said:**
> 

I did a "ps -ef | grep dhcp" to find any DHCP clients running that may be trying to renew every 24 hours, but can't find anything.  I assume that the DHCP client (my Ubuntu computer) has to initiate the DHCP renewal, so that's why I'm posting the question here.

Any Ideas?

Mike

Try "ps -ef | grep dhclient"...

---

