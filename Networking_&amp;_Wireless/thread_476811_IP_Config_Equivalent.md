---
title: "IP Config Equivalent?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by vgrisham on 2007-06-17
Hi,

To release and renew an IP address in windows one types ipconfig /release all at the command prompt, then ipconfig /renew.

What is the equivalent for the above commands in Ubuntu Linux?

Thanks,
Vaughn

---

### Post by spd106 on 2007-06-17
In Linux each kind of task has it's own tool.

To get and set interface properties you can use the **ifconfig** command. This used to set a static address, netmask etc. For wireless use **iwconfig**.

To use DHCP you need to use the **dhclient** command.

To access routing information use the **ip** or **route** commands.

I recommend that you read the man pages for each of these, as they have many useful switches.

---

### Post by steveneddy on 2007-06-17
[Here]("http://blogs.pingpoet.com/overflow/archive/2005/12/04/15739.aspx") is your answer.

---

### Post by Cullen on 2007-07-08
Thanks very useful

---

