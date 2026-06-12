---
title: "Internet sharing. (Vista to Ubuntu)"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Mehall on 2008-10-02
Hi there.

I have a ubuntu server running, and I want to let it on the web.
I have a laptop running (ugh) Vista (i have dual-boot Kubuntu, but I want this fixed in Vista boot first) and it has a wireless internet connection.

the ubuntu server is connected to the Vista by a crossover cable.

ifconfig output for server:

eth0      Link encap:Ethernet  HWaddr 00:40:ca:28:4c:29
          inet addr:192.168.2.2  Bcast:169.254.118.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe28:4c29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:164985 (161.1 KB)  TX bytes:222147 (216.9 KB)


ipconfig for Vista: 
ipv4 address: 192.168.2.1
Subnet Mask: 255.255.255.0


I have Privoxy installed in Vista if that will be of any use.

Any more details needed can be supplied. I am still quite new at Linux.


EDIT: Forgot to add that I can use putty to connect to the server. I juts can't get the server online.

---

### Post by Mehall on 2008-10-03
bump?

I would really appreciate some help.

Someone has suggested setting up a VMWare server on the laptop to handle the DHCP and everything else.

---

### Post by superprash2003 on 2008-10-03
best way is to enable ICS in vista..its pretty simple [http://windowshelp.microsoft.com/Windows/en-us/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx](http://windowshelp.microsoft.com/Windows/en-us/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx)

---

### Post by Mehall on 2008-10-03
> **superprash2003 said:**
> best way is to enable ICS in vista..its pretty simple [http://windowshelp.microsoft.com/Windows/en-us/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx](http://windowshelp.microsoft.com/Windows/en-us/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx)


For Vista ICS to work, the "client" needs to accept an automatic IP from the Vista machine, which Ubuntu won't.

In fact, on re-trying this (i did it previously, but I figured I would attempt again)

I can no longer SSH into the server, despite having the correct IP for it, according to ubuntu's ifconfig ouptut. (no change from above. The only change is that Vista's ICS is on, and Vista has been automatically set an IP)

---

