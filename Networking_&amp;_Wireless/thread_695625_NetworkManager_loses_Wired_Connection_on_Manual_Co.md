---
title: "NetworkManager loses Wired Connection on Manual Config"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by mkwerner on 2008-02-13
Hi everyone,
I'm running Kubuntu 7.10 on a Dell D620 laptop and have been since 7.10 came out.  I have two network interfaces:  wired Eth0 and Wireless Eth1.  

On the few occasions where I've needed to configure a static address for my wired card, everything goes fine until I need to revert to DHCP on this interface.  Then, upon clicking Knetworkmanager, I find that the wired interface option is missing from the dialog box.  Rebooting/logging out does not fix it - I HAVE been able to fix it by doing the following:

1.  edit /etc/network/interfaces and remove any references to eth0
2.  run sudo /etc/init.d/networking restart
3.  log out, then back in

My question, after that long winded anecdote, is this:  would this be considered a "bug" or a "feature"?  I could see how this would be confusing for a new user - I was able to fix this due to prior experience with linux, but a new user would probably find this frustrating.  

Any input would be greatly appreciated!

Take care, and keep up the good work!

M.

---

### Post by kuja on 2008-04-02
It's certainly not a feature. The program isn't functioning as expected, that makes it a bug. It removes the ability to connect wired with the ip address of your choosing, which could prove very inconvenient if your router doesn't have a "static dhcp" feature. (Granted, Avahi should partially relieve this)

---

