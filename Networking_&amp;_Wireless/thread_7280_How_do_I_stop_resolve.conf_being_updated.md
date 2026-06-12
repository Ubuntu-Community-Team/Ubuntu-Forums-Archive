---
title: "How do I stop resolve.conf being updated?"
date: 2004-12-05
forum: Networking &amp; Wireless
---

### Post by DougC on 2004-12-05
Hi all,

I have a small but irritating problem in that my resolv.conf file gets updated wrongly. The first entry always sets it'self as my routers IP address while the second sets it'self as my ISP's primary DNS. This causes a 4 or 5 second delay before web names get resolved. It all works fine if I manually set the entries to my ISP's Primary and Secondary DNS servers. I want to keep using DHCP I just want it to stop seting the DNS servers. How can I do this?

Thanks!!!
D

---

### Post by cseg on 2004-12-05
I''m not on my ubuntu system right at the moment, but the following should work.

   sudo vi /etc/dhclient.conf

Change the line:

   #prepend domain-name-servers 127.0.0.1;

to

   prepend domain-name-servers 68.10.16.25,68.10.16.30,68.100.16.30;

using whatever DNS servers you want  to use.

Then:

   sudo ifdown eth0
   sudo ifup eth0

This will restart your NIC and resolv.conf should contain (and hopefully keep) your DNS servers.

---

### Post by DougC on 2004-12-06
cheers!!! worked a treat. Although I did have to remove the domain-name-servers  entry from the request section as well.

Thanks,
D

---

### Post by RAdams on 2006-08-18
> **cseg said:**
> I''m not on my ubuntu system right at the moment, but the following should work.

   sudo vi /etc/dhclient.conf

Change the line:

   #prepend domain-name-servers 127.0.0.1;

to

   prepend domain-name-servers 68.10.16.25,68.10.16.30,68.100.16.30;

using whatever DNS servers you want  to use.

Then:

   sudo ifdown eth0
   sudo ifup eth0

This will restart your NIC and resolv.conf should contain (and hopefully keep) your DNS servers.

I'd like to do this also, but I do not have an /etc/dhclient.conf...

---

### Post by zvacet on 2006-08-22
Look in /etc/dhcp3/dhclient.conf

---

