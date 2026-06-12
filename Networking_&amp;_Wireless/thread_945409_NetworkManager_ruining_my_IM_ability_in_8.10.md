---
title: "NetworkManager ruining my IM ability in 8.10"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by squidfaceExtreme on 2008-10-12
Hi, I'm using Ubuntu 8.10, and I'm trying to connect to my IM accounts in Pidgin (or Empathy, for that matter). I have a wired and wireless card, and I am using the wired to connect to the net (I don't use the wireless for anything at the moment) For reference, they both work fine.

NetworkManager tells me I have no connection. This is because there's something wrong with its configuration of my wired connection, so I've had to set up the wired manually using route, ifconfig and an edit of /etc/resolv.conf. Nonetheless, I'm not sure how it works but it seems that NetworkManager not setting up the connection is enough to convince Pidgin that there's no network connection.

To be specific, NetworkManager, upon clicking the icon, says under Wired Network, "device is unmanaged".
In the Edit Connections menu, I can see under the Wired tab one entry: "Ifupdown (eth0) | never" 
I cannot delete or edit this entry, otherwise I get the error "Removing connection failed: ifupdown - connection delete not supported (read-only)..." or Updating, practically anything I try to apply to it.

EDIT: After a bit more looking up I found a hacky way around it is to set Pidgin's status to Away, then back to Available when it's all signed up. I'd still like to find a legit way to fix this problem though as I don't like such ugly solutions.

---

