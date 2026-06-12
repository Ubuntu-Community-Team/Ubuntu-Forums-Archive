---
title: "Connecting to DHCP sometimes works and sometimes it doesn't"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Douwe Vos on 2007-10-19
I have a Dell Latitude D820 which I use at home and at my work, it is running the latest version of ubuntu (that is 7.10). If I connect my notebook at work to the network it works fine: the network connection is configured 'roaming mode enabled' and it gets an IP-adress through DHCP. At home it is a different situation. If I connect it at home I do get an IP-adress but I do not get a 'default gateway' assigned. This is all fine for me, so I turn off 'roaming mode' and select 'automatically configuration by DHCP'... the problem stays. So I end up filling in a static IP adress and a static default gateway .. and then it works. 

This could all be good explained by the fact that I configured the DHCP server running on my home Debian server myself. But it makes it weird that everybody else in the house do get normal configurations by using this DHCP server. That includes a pretty old Red Hat Linux machine and a Windows XP machine. The most weird thing is that my normal Desktop computer also gets configured correctly and that its running the same Ubuntu as my notebook.

The DHCP server at my work runs on a Windows 2003 machine.

---

