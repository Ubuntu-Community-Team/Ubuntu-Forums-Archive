---
title: "Feisty &amp; IPv6"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by beren on 2007-07-06
I have been browsing the posts on Feisty networking but I have not quite found the problem I have.

I installed Feisty a few days ago and my network stopped working. After some investigation I found out that eth0 was set to DHCP with IPv6. It was impossible to change this. After some more fiddling I managed to set up static IP with IPv4 and everything worked again.

But I actually would like to use DHCP as before - how do I go about that? How come I can't use DHCP with IPv4 - as I expect IPv6 to be a problem with my router.

Beren

---

### Post by kevdog on 2007-07-06
To disable ipv6 (a great source of controversy) do the following

gksu gedit /etc/modprobe.d/blacklist
blacklist ipv6

I think you have to reboot to make the changes take effect.  You could try sudo /etc/init.d/dbus restart, but Ive always found rebooting to be more reliable.

---

