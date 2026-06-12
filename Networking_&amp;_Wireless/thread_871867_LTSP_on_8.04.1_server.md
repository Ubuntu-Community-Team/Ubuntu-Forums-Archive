---
title: "LTSP on 8.04.1 server"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by casedog21 on 2008-07-27
I have LTSP up and running on my webserver/app server.  I enabled DHCP on the webserver to test and it works I can boot a vmware "terminal" and I tried an actual workstation.  They both boot fine.

Problem is I have a another machine already setup to run DNS and DHCP.  It uses DNSMASQ. 

**Is the dhcpd server what handles tftp on the ubuntu server?**


Here is what I set up in **DNSMASQ**

dhcp-option=eth0,1,255.255.255.0
dhcp-option=eth0,28,10.1.5.255
dhcp-option=eth0,3,10.1.5.1
dhcp-option=eth0,6,10.1.5.254
dhcp-range=eth0,10.1.5.100,10.1.5.150,24h
dhcp-boot=pxelinux.0,"10.1.5.252",10.1.5.252
read-ethers

Here is the deal 254 is my DHCP server, 252 is my ubuntu server with LTSP.

When I tested if from ubuntu's DHCP server I disabled DNSMASQ on the other so their were no conflicts and it worked fine. And then Disabled DHCPD on ubuntu and reneabled DNSMASQ on the other box.

I think I am on the right track but not sure where I am going wrong.  

I just want to be able to pxe boot with the dnsmasq on the other server.  

Thanks for any help...

Casey

---

### Post by casedog21 on 2008-07-27
ok I got it figured out....

I was adding them to the /etc/ltsp/dhcpd.conf

The fix was add these to the /etc/dnsmasq/dnsmasq.conf

dhcp-boot=/ltsp/i386/pxelinux.0,hostnamegoeshere,ip_of_the_tftp_server
dhcp-option=193,ip_of_the_tftp_server




then /etc/init.d/dnsmasq restart

Then all is well...

Casey


Casey

---

