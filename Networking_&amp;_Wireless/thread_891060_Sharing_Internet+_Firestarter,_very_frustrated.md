---
title: "Sharing Internet+ Firestarter, very frustrated"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Wien_Sean on 2008-08-15
I have been working on this for about two days and progress has been very slow. Just to preface, I am still learning a lot about Linux, and I am sure my question is answered in several other posts, but for the life of me I cannot find it. 

I want to use an old PIII 733 as a router for my small home network. I have AT&T DSL that uses PPPoE, that is working correctly as I can post this.

I have DHCP3-Server installed and setup as per this guide [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) 

Firestarter is installed and set to route from PPPoE (this is connected via eth0) to eth1. My router is set to bridge mode, and with this setup I can ping the one computer that is currently on and vise verse. Until I used the guide for DHCP3-Server this morning the one client computer was able to transfer via Bit Torrent, but not able to get to the internet. Now BT does not work, but I am getting an ip address via DHCP, and still no internet. I have added my computer to the trusted hosts but still nada. 

Let me know what info you guys need, I will be here all day and night, I just want to get this finished.

---

### Post by Wien_Sean on 2008-08-15
I have no idea what I did, but it works now. All I did was reboot once again, edit the DHCP3-Server config file, but did it wrong, set everything back to the way it is supposed to be, and now it works.

---

