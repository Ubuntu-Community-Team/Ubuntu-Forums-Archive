---
title: "Edubuntu Server Network Configuration"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by adMOMistrator on 2007-06-22
I am trying to get my edubuntu feisty server up and running and am having some trouble with the network configuration.  Here's what I have:

The sever is a laptop (that can't autoconfigure at os install for some reason).  I have the pc to the point where it can see the other pc's on my net and it can ping them with about 50% success.  I can ping localhost 100%, but I cannot ping my modem.  My network only has an eth0, for some reason there is no eth1.  I have attempted to configure for static ip, and think it's working.  I think my isp uses pppoe to assign the static ip.

When I looked, the etc/network/iface is empty.

I just saw something on another post that mentioned needing a new ssh key?
And my isp says that the host, ip and subnet mask for the static ip is all 0 ( I assume that it's all dynamically assigned somehow.  And I can't even figure out if I should have my network set for dhcp and let that assign the static ip, or if I need to set the static ip with all 0's or if I need to plug in my isp's "alternate" info.

Can anyone give me some direction please?  I'm clueless about networks - - other than what I've tried to learn figuring this pc out.  And I would really like to use it this school year  - - - we home school the kids.

Have a good Day

Danielle

---

