---
title: "Wareless adapter can't see the wireless net."
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by RobKan on 2007-04-30
My adapter (Level One)  had recognized by Ubuntu, after i install the ndiswrapper. And it can be seen. I connected to the router by DHCP. But I can't connect to internet. I try to ping it, and no answer. 

I'm a new in Linox. In WinXp I just install the driver and the program that comes with CD. The program recognize the wireless net that I have. 

In Ubunto (6.10) - I have install the driver and I can see it in lof file. 

What else I need to do?

Thank you!

---

### Post by got_nix on 2007-04-30
check the ip class that your router gives you.. by doing

ifconfig

depending on the class you get

ensure that your resolv.conf flie has  an ip of the the same class  as its namespace server.

example

router kicks you 192.168.0.31

set your nameserver value to 192.168.0.30 its what i had to do to get mine working

hope it helps..

If i've used wrong terminologies i'm sorry i'm not a networking person.

---

