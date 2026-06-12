---
title: "Configure VLAN in feisty"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by cjrmail2k on 2007-05-28
Hi All,

I need to configure my NIC to connect to a VLAN Trunked port on a Cisco switch. After some research I found that the components should already be installed in the 2.6.* kernel. Can anyone advise me what file/s to edit or point me in the right direction in order to connect to a VLAN. I cannot connect to the internet (except from an xp machine) until I am able to configure this setting.

---

### Post by cjrmail2k on 2007-06-02
I have looked further into this and it would appear that I need to add the package VLAN. Obviously I cannot do this using apt-get because I have no network connection. I have tried to download and 'make' the package but get an error so I cannot 'make'. I need to use the command vconfig but that points me back to the VLAN package. Can someone please help with some advice on how to get the VLAN package installed please?

I have access to the internet from an XP machine so can download packages and transfer them via USB stick if need be. 

Using Sony Vaio, Ubuntu 7.04.

I have had this post up for days without any replies...please can someone out there help a linux noob!

---

### Post by cjrmail2k on 2007-06-25
I guess my question was below y'all. Not even 1 response. 

Anyway I managed to get working by configuring the switch to a specific vlan and removing the trunking, installing VLAN and 8021q and using vconfig for the rest. I didn't want to have to remove trunking because I needed the other VLANS for admin tasks on the same port. I hope I can come up with a nice challenging question for everyone once I get my head around the basics.

Chris

---

### Post by LaneLester on 2007-12-19
> **cjrmail2k said:**
> I guess my question was below y'all. Not even 1 response. 

Anyway I managed to get working by configuring the switch to a specific vlan and removing the trunking, installing VLAN and 8021q and using vconfig for the rest. I didn't want to have to remove trunking because I needed the other VLANS for admin tasks on the same port. I hope I can come up with a nice challenging question for everyone once I get my head around the basics.

Chris, I'm sorry you didn't get more help, because I find myself in need of it as well. Next month I will start teaching at a school where wireless is provided by a VLAN (about which I know nothing). The IT honcho said all I'd need was my username and password... yeah, right... maybe with Windows that's all you need. :(

I've installed vlan as you mentioned, but nothing else you said made any sense to me. I'm going to be very surprised if this thing works without further fiddling... and if I can't get it here, where will I?

Lane

---

