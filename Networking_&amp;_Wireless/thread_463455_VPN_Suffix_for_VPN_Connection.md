---
title: "VPN Suffix for VPN Connection"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by octoberdan on 2007-06-03
I've been trying to phase out the use of windows at the workplace and so far I have been successful.. However, one step remains, getting VPN working. I've set up a vpn connection with networkmanager-pptp and the nm-applet, and can connect successfully. However, once connected, I can no longer resolve host names (although I can ping IP addresses within the network. I emailed the network admin at work about the problem and he told me the following; 
> 
Make sure you add the dns suffixes w/in vpn connection for loomissayles.com and loomissayles.net. 

I've looked around, but I haven't been able to figure out how to do this. Any help, guidance, or links would be greatly appreciated. Thank you.

---

### Post by octoberdan on 2007-06-03
In an IRC channel... 
> 
< JayTee52> octoberdan, when I connect to our VPN if I need to remote to 
                  another machine or connect to a share on another machine I 
                  have to use the FQDN (fully qualified domain name). For 
                  example, I want to connect to joe bean's computer named jbean 
                  I have to enter the computer name as jbean.mydomain.com
< JayTee52> however if you want you should be able to add 
                  *.yourdomain.com or *.yourdomain.net using Network Manager by 
                  clicking on the DNS tab after opening the applet.


Hhow do I make that setting specific to that VPN connection and how do I not loose internet connection when I connect?

---

