---
title: "Share internet with a Virtual Machine"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by betete on 2008-04-07
Hello I nned help on sharing internet connection to a Virtual Machine. This is the situation:

I have a machine running Win XP. It has 2 network adapters (lets say A and B), one connects to a ADSL modem to access the internet(suppose A). The other (B) adapter has a fixed IP adress (192.168.0.1) and is connected to a machine running Debian (IP 192.168.0.2). The network works great. I have internet in the Debian machine.
Now, I installed VMware in the XP machine. I created a virtual machine and I installed Ubuntu on that machine. I set Vmnet0 to Bridged to the adapter B. I assigned IP 192.168.0.3, and now from the Ubuntu virtual machine I can see the Host XP machine and the Debian machine, at least ping works. The problem is that I don't have access to internet. The configuration is the same for de Debian machine, and that machine has access to internet, but I cannot get the virtual machine to connect. Any idea?
I have already set gateway 192.168.0.1 in the Ubuntu machine.

---

### Post by superprash2003 on 2008-04-07
are you able to ping websites in the ubuntu machine? also try changin the ip of the vmnet to connect to the ethernet card connected to the adsl modem.. i.e.192.168.1.x

---

### Post by betete on 2008-04-07
I cannot ping to websites, I tried to ping to yahoo and I had no answer. I tried using NAT instead of briedged and it worked, I could access to internet, but then I don't know how to access remotely to the virtual machine. I don't know how to configure NxServer.
You tell me to try changing the IP of vmnet to connect to the modem, but in that case, I wouldn't have access from the Debian machine to the Virtual machine.

---

