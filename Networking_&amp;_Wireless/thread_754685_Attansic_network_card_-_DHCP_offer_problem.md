---
title: "Attansic network card - DHCP offer problem"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by lvgandhi on 2008-04-14
I am running kubuntu gutsy in my pC with MB asus P5GC which has inbuilt attansic l2 network card. I am connecting to internet through Huawei MT841 dsl modem. The modem connects using auto dialling pppoe and has dhcp server. I have winxp, debian etch and kubuntu on this same machine. I have no problem in getting lease from dhcp sever of this modem in winxp and debian. In kubuntu, I see atl2 driver is loaded and inter face eth0 is up. I have following in /etc/network/interfaces.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
Some times eth0 cah get lease. Sometimes it gets lease with dhclient. But most of the time even with dhclient done manually, i get msg
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
If any other info is required, I will give.
Kindly help to get rid of this problem.

---

### Post by chili555 on 2008-04-14
I was looking at this: [http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04541.html) and it appears the *atl2* module is under continuing development. You might try the lastest version here: [http://people.redhat.com/csnook/atl2/atl2-2.0.4.tar.bz2](http://people.redhat.com/csnook/atl2/atl2-2.0.4.tar.bz2)

Download the file to your /home/user directory, or Desktop; wherever you usually download files. Right-click and select 'Extract here.' A directory will be create, *atl2-2.0.4*. Open a terminal and change to that directory. Do:```
make
sudo make all
```I notice he has a patch, which you may or may not need. Try this and see if you can connect.

---

### Post by lvgandhi on 2008-04-14
Thank you very much.
The new driver solved the problem.

---

