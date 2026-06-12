---
title: "OpenDNS"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by scottym on 2009-01-09
My DNS settings have suddenly been over ridden by my ISP's DNS. I use Earthlink and Gnome PPP to connect using a 56k modem card, Ubuntu 8.10. I have edited all the obvious files but something keeps changing my resolv.conf dns settings from OPENDNS back to Earthlink's DNS.
Any thoughts on what is happening here

---

### Post by madverb on 2009-01-09
I know this is for a 3G connection but I am wondering if it is similar to your problem?
[http://www.nabble.com/Dynamic-IP-but-DNS-static-(3g-connection)-td19587609.html](http://www.nabble.com/Dynamic-IP-but-DNS-static-(3g-connection)-td19587609.html)

---

### Post by scottym on 2009-01-10
I don't think that is my problem.
What started happening a few days ago is the resolv.conf file which has the nameservers for the DNS keeps getting set back to Earthlinks DNS. I can Change it to the OpenDNS nameserver and when I use pon, Gnomeppp or network-admin to connect it changes the file back to the EL DNS.

---

