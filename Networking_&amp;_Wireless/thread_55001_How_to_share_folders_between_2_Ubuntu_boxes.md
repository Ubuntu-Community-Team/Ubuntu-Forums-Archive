---
title: "How to share folders between 2 Ubuntu boxes ?"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by marsian on 2005-08-07
Hi all,
not sure I'm in the right sub-forum because I guess my networking problem is rather relating to soft but can't find where to put it elsewhere...

My local network is contituted by 2 Unbuntu boxes (pc0 and pc1) connected via a router (SMC2804WBR) in DHCP mode. 
I want a directory from pc0 to be accessible from pc1, but as the router seems to not be able to act as DNS server, I have to mount shared NFS directory using the pc0 IP address (instead of its hostname), which is able to change at each reconnection :-(... 

In such a configuration, is there a way to be able to mount automatically (and whatever the current pc0 IP address is) the shared directory at each pc1 startup ? (note: I want to keep DHCP because sometimes others PC are connected to the network, so assigning a fix IP to the networked PCs is not a good solution for me)

---

### Post by lol on 2005-08-07
You should probably try using samba... It's a really crappy protocol, and a really pain to setup, but at least you won't need a DNS.

---

### Post by marsian on 2005-08-07
ok, I will try to configure samba.
But I was thinking that samba is intended to share directories between Windows and Linux systems... Aren't there a more "native" ways to share directories in a Linux only world ?

btw, what about the menu Places->Network Servers ? The only icon I have in it is "Windows Network"... but I'm not connected to any Windows PC (and indeed, if I click this icon, the opened panel is empty). Can someone explain me the purpose of this shortcut ?

---

### Post by mortsahl on 2005-08-07
Set your 2 PCs to static IPs ... just because you do that doesn't mean that others on your network can't be DHCP.

In my network I've got 8 machines ... 4 linux boxes and 4 windows ... 2 linux are static, 2 windows are static, the others are DHCP.

---

