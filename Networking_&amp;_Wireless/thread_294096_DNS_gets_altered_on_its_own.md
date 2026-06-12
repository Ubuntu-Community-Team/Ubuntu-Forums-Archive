---
title: "DNS gets altered on its own"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by nike439 on 2006-11-06
I recently started using Dapper Drake (6.06). A peculiar problem has come up.

The DNS entry in my Networking window changes on its own. I have to enter the DNS servers again and again. And it changes. It can happen anytime. I cant figure out why the DNS would change on its own. Please help.](*,)

---

### Post by timmeeej on 2006-11-06
I think this is caused by dhcp in your router, it overwrites your manually configured dns servers.

---

### Post by hekto5 on 2006-11-06
You can add your preffered DNS.
Just open /etc/dhcp3/dhclient.conf and add
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
just before line starting with request. Semicolon is imporant.

This way your DNSes will be used before those fetched from DHCP request.

Good luck :)

---

### Post by nike439 on 2006-11-06
Thank you for the advice. But how do I open dhclient.conf?

I am new to Linux and have no clue about the commands.

---

### Post by hekto5 on 2006-11-06
There are many ways. One of them is:
1. open applications->accessories->terminal
2. type: gksudo gedit /etc/dhcp3/dhclient.conf

---

### Post by handy on 2006-11-07
> **nike439 said:**
> Thank you for the advice. But how do I open dhclient.conf?

I am new to Linux and have no clue about the commands.

Have a look at [**_this how-to_**]("http://ubuntuforums.org/showthread.php?t=282034") it covers your problem, & was written with you in mind. :-)

---

### Post by nike439 on 2006-11-08
Hey Thanks guys,

I'll try this right away. :)

Cheers

---

