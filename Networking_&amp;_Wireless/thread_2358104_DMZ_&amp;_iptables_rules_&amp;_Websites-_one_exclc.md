---
title: "DMZ &amp; iptables rules &amp; Websites- one exclcude another"
date: 2017-04-09
forum: Networking &amp; Wireless
---

### Post by jambyc on 2017-04-09
Hi,

I have set port forwarding for TS3 30033, 10011 and 9987.. OK! its working... rules on iptables set as well.
Previously everything was working without a doubt :/

Suddenly all my apache websites cannot connect to the server but when I enable DMZ to the server everything is working. 
I am fully aware that I have missed off something but I cannot get my head around. 
Logs will be helpful but I am not sure whats needed. 
Please advise.

---

### Post by papibe on 2017-04-09
Hi jambyc.

Did you set up a DHCP reservation for your machine? (so that your router rules don't point to another machine in case the DHCP renewal gives you another address).

Regards.

---

### Post by jambyc on 2017-04-09
Yes, DHCP reservation assigned so Ubuntu 16.04 LTS is set to automatic.
I had massive issue with useless Virgin Media HUB 3.0 to setup port forwarding but I found my way

---

