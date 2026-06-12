---
title: "Ubuntu Desktop pings to and from local Windows Box, No DNS"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by CMoneyDollaBillz on 2007-07-20
Hello Everyone:

I just set up a new Ubuntu Desktop on my home network and I love it thus far. I am having a minor issue with the Ubuntu desktop's host name and DNS. My Ubuntu machine is hooked up to a router and the internet works fine. I can also ping to other windows machines in my network via IP address. However, I can not ping other machines via host names and other machines can't ping the Ubuntu box via host name as well. Below is the contents of my resolv.conf file. The DNS servers are right in terms of my ISP and my router configuration. I am also having a problem configuring Synergy with my Windows box as a host and my Ubuntu as a client (would assume it stems from this DNS issue). Any help would be greatly appreciated, thanks everyone!


********* resolv.conf ***********


nameserver 205.152.144.23
nameserver 205.152.132.23

---

### Post by bernied on 2007-07-20
I think the simplest solution is to add the other machines to your list of hosts. You can do this in network settings, or edit the file /etc/hosts (as root user - use sudo).
Windows machines also have an .../etc/hosts file with exactly the same format, it is buried somewhere in the file system - maybe \Windows\system32\drivers\etc\hosts - you can do the same there for your ubuntu machine.

All this depends on static IP addresses for the machines.

---

### Post by CMoneyDollaBillz on 2007-07-20
Thanks for your reply bernied. I rather use DNS than manually modifying system files to show host names. Is there another way of doing this? Thanks, everyone

---

### Post by bernied on 2007-07-20
Then I think you need a DNS server on your network and use that as your first nameserver. I think the standard linux software is called bind.

---

### Post by CMoneyDollaBillz on 2007-07-21
Any more specific advice? Thanks everyone.

---

