---
title: "Duplicate ARP! MITM Attack??"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by gtdaqua on 2007-08-22
This is continuation of a different issue (only the issue is different here)

I have installed Kubuntu 7.04 on my desktop.My internet would work for a while and then suddenly stop. All LAN resources are always available. Internet would resume after few minutes (like 5 mins). 

Two of my machines in the network are having the same ARP entry!!! This happens often!!

192.168.6.1 (L3 Switch & Actual Default Gateway to Internet) - this device's MAC is pointing to 192.168.6.3 (Ubuntu Server) - so when I  ssh'd to 6.1, i was presented the logon screen for 6.3! 

I double checked ARP and 6.1 has 6.3's MAC address. So no routing happens! I have to force a 'arp -s' for 6.1 and register its MAC and then Internet would resume.

Can someone help here? I am concerned if this is a MITM Attack! I know something abt ARP poisoning - but could this be it?

---

