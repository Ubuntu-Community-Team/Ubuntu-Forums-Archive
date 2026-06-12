---
title: "print sharing"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by bmenge on 2007-08-18
ok I have my system set up with 7.04 and am trying to get my apple ibook to print over the wireless network.  I did some searching and found that  most of the data out there is for window machines. 

I have a canon pixma ip6000d running with turboprint.  I posted on the turboprint forum with very little traffic.

I edited the cupsd.conf file to Listen to the ibook 192.168.2.7 browsing is also on.  I Also added Listen to the linux box 192.168.2.29, I think this is redundant since it listens to local but I don't know?

First thing first I set up the printer on the mac os 10.4.2  printer location 192.168.2.29(verified address and found printer info) I tried to print and got error host busy will retry in 30 seconds. 

Did a little research and thought maybe I need to install new printer in turboprint as network printer? anyway I did that with host as 192.168.2.29 with connection remote ipp tried to print a test page same error host busy retry in 30 seconds.  

How do I get around the host busy error.

I can ping the ibook from ubuntu, and the ibook gets the printer info ok so I don't think it is an issue with connectivity but what do I know?

---

