---
title: "&quot;localhost.localdomain&quot; begginer question"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by werty2010 on 2011-04-20
i started using a program to monitor my network-Internet connections. recently, very often among others i see my pc connects to "localhost.localdomain".
im just curious what exactly is it?

---

### Post by Locke_99GS on 2011-04-20
localhost is your own computer. localdomain is the block of space you're a member of on your network.

It is just a named method of referring to itself.

---

### Post by werty2010 on 2011-04-20
ok thanks
but the strange thing is didnt have these kind of connections a few days ago....so my question why now?

---

### Post by Locke_99GS on 2011-04-20
You may have installed a service or daemon/client type application-pair which communicates over the network. Some torrent clients, for instance, are arranged in this way.

If you're running a modern Ubuntu distro, you can look in the Software Centre at the installation history for the last couple of days and see what did it.

---

### Post by werty2010 on 2011-04-20
from gufw listening i also see that a process dhclient3 is always running.
any idea what it is and why is it running?

---

### Post by bodhi.zazen on 2011-04-20
You get an ip address from your router or internet provider using dhcp.

Your router / ip provider runs a dhcp server, you run the client.

[https://calomel.org/dhclient.html](https://calomel.org/dhclient.html)

---

### Post by werty2010 on 2011-04-20
im pretty sure this showed up 1 day ago after upgrading some packages through the update manager( dchp3-common and dchp3-client )...
i think this also slows down my Internet connection
maybe its a bug.. i dont know.....?

---

### Post by bodhi.zazen on 2011-04-20
I doubt dhcp is slowing your internet connection, from your posts I would suggest you keep reading =)

---

### Post by ngubk on 2011-04-20
No way! DHCP is st that gives your computer a dynamic ip-address( you can see your ip is different everyday).

What's the content of your /etc/hosts?

---

