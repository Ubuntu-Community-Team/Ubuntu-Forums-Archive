---
title: "ADSL Modem important info"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by raulb on 2007-10-28
Hi, I was debugging a few issues with my adsl modem connection in Ubuntu Feisty and I think this info may be helpful to others who face similar issues. These issues are unique to Ubuntu, the same problem doesn't occur in XP or Vista on my system and applies to those who are using  pppoe software to dialup to connect( ie bridged mode and not pppoe in the modem which gives an always on connection when you switch on the modem.)

First I was facing too many dropped connections. Originally my network was set up as DHCP. This was probably causing the dropped connections for some reason. Use static instead of DHCP and the frequent disconnections should vanish. For this go to 'System/Administration/Network' and select 'Wired' connection and 'Properties' tab and in 'Configuration' choose 'Static IP Address'. Now put in values for IP address, Subnet mask and Gateway address. In my case these are 192.168.1.2 for IP address, 255.255.255.0 for Subnet mask and 192.168.1.1 for Gateway. Subnet mask will remain 255.255.255.0 but your IP address and Gateway values could be different. Incase you have XP you can run the command 'ipconfig -all' when you are connected to the internet through your adsl modem in XP to get the values.  

Second and more difficult to debug and resolve  if I boot the system with the adsl modem on  internet would work but if I boot the system with the adsl modem off, for some reason the nic led would not start meaning no network and there would be no connectivity with pon dsl-provider untill I rebooted with the modem on. Highly frustrating. I tried lots of things '/etc/init.d/networking restart' ,' ifconfig eth0 up' etc but no go. The led won't come on. I googled a lot and went through the forums here but couldn't resolve this. The solution to this is surprisingly simple. You just have to run a single command 'mii-tool -r'. And this immediately starts the nic led meaning your network is now up and 'pon dsl-provider' will work as expected and connect to the internet without rebooting. 

Hope this is helpful to those similarly affected.

---

