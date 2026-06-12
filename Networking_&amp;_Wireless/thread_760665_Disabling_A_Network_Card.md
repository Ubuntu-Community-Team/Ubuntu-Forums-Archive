---
title: "Disabling A Network Card ?"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by drsox1899 on 2008-04-20
I'm dual booting and have a good way in WinXp with two NIC cards of preventing the WinXp from phoning home but at the same time being able to access the network.

BUT, when I go into Ubuntu the system spends time trying to get a DHCP IP address for the NIC card (eth0) that can't get one.  The other card (eth1) is the one for Ubuntu to use.

How can I get eth0 disabled in Ubuntu (without taking it out) or reverse the numbering to allow the Ubuntu card to be known as eth0 ?

:confused:

---

### Post by ibutho on 2008-04-20
You can disable the network card you do not wish to use, using the Network Configuration tool (network-admin).

---

### Post by drsox1899 on 2008-04-20
> **ibutho said:**
> You can disable the network card you do not wish to use, using the Network Configuration tool (network-admin).


Exactly how do I do this ?  I thought these two tools (Network and Network tools) would contain the means so to do, but none of the options and/or pull-down menus show an option for disabling.  What have I missed ?

---

### Post by CrazyGuy123 on 2008-04-20
Don't disable it, instead set it to IPv4 LL.  That means ubuntu won't spend ages trying to find an address for it, and won't try to use it either.

---

### Post by ibutho on 2008-04-20
> **drsox1899 said:**
> Exactly how do I do this ?  I thought these two tools (Network and Network tools) would contain the means so to do, but none of the options and/or pull-down menus show an option for disabling.  What have I missed ?
Hope this [link]("https://help.ubuntu.com/7.10/internet/C/networking-disable.html") helps.

---

### Post by drsox1899 on 2008-04-20
> **ibutho said:**
> Hope this [link]("https://help.ubuntu.com/7.10/internet/C/networking-disable.html") helps.

Great.  I found it, thanks.  Pity there isn't a enable/disable button.

---

