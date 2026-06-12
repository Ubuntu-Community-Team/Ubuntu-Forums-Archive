---
title: "Internet and Network services suddenly stopped working"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by ejay563 on 2008-09-23
Hi,

I have a desktop setup with MythTV, and I was working on getting it setup as a wired router so I could plug my laptop into it and transfer files to/from it. It was working fine, then one day out of the blue I was no longer able to access the internet or any of the network services that are on the network at the University I attend (just to make it clear, I had been ablle to access it all just fine, and I had not changed anything in between the time it was working, and when it stopped working). I have tried taking down the network interfaces, and starting them back up, restarting the computer, restarting the network with sudo /etc/init.d/networking restart, and sudo dhclient. No matter what I do, I get an IP address, but can not access anything. Is there a way to bring all the network settings back to their originality, or if not, any ideas on how to fix this?

Thanks!

---

### Post by willca on 2008-09-23
So you get assigned an IP...tried to ping some sites or some hosts you know are up.

Tried to do some traceroute and see where the packet gets dropped?

Sounds like you are using dhcp, so whatever the university dhcp server is spitting out then that should have stayed the same, configuration wise though.

---

