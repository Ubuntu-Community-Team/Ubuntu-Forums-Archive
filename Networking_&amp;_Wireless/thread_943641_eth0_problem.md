---
title: "eth0 problem"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by kubyak on 2008-10-10
Hello. I am new in ubuntu...a search something about my problem but i found nothing..thats the reason why i create this task.
I have one problem.
I installed ubuntu server edition and i try to connec to the internet.
My interfaces are eth0 - Link encap:Ethernet and lo Link encap:Local Loopback.
I am connected to the router , when i try sudo dhclient eth0 it writes No DHCPOFFERS...
When i try that same on my notebook ( Ubuntu desktop) it connect with no problem...
Can somebody what have i to configure on the ubuntu server pc ?

This is dhclient from notebook...
There is already a pid file /var/run/dhclient.pid with pid 7056
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:14:c2:d5:c6:3d
Sending on   LPF/eth0/00:14:c2:d5:c6:3d
Sending on   Socket/fallback
DHCPREQUEST of 89.173.78.242 on eth0 to 255.255.255.255 port 67
DHCPACK of 89.173.78.242 from 10.173.64.1
bound to 89.173.78.242 -- renewal in 108419 seconds.

Thank you

---

### Post by cariboo on 2008-10-10
Please you the code tags when poting output from a command, you can find the code tag # in the advanced editor.

What type of network card do you have, and is it being detected properly please post the output of:

```
sudo lshw -C network
```

Jim

---

### Post by kubyak on 2008-10-10
There is a little problem.
I cannot copy and paste the result of lshw -C because the other computer is not connected to the internet..and i dont know hot to do that...

But if you want to know i have 
```
*-network:1 DISABLED
      dsecription : Ethernet interface
      logical name : eth1
```

Its old 3com Fast Etherlink 

when i try ifconfig it is eth0

I hope that thats it what do you have asked for...that i have DISABLED the ethernet interface...

---

### Post by kubyak on 2008-10-10
ok thank you for this lshw... i have add the eth0 ( like on the notebook) to /etc/network/interfaces and now when i see that the eth1 is DISABLED i try to edit the eth0 to eth1 in /etc/network/interfaces and it goes... when i try ifdown and ifup it connect with no problems...only one fatal error with resolv.conf or something like that , but internet is going now...thank you for help..

---

