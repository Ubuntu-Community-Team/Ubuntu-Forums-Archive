---
title: "Cisco Aironet 350 Unable to obtain IP Address on IBM T40"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by New101 on 2007-08-06
Running out of patience...please help.

Installed Ubuntu (Dapper Drake 6.06.1)  on a refurbished laptop 5 days ago. After I configured System>Network Settings using wireless interface eth1 I had a wireless internet connection up and running.

Then I got cocky at the end of day 1 and downloaded two programs called 'Network Manager' and 'Wireless Manager'  via the Add/Remove program in Applications. My wireless stopped working. I removed the programs but still cannot get wireless working. Have re-installed the OS several times and attempted all the solutions I could find on this forum. 

My Cisco Aironet card can see the MAC address of my router  and vice versa but no IP address is assigned. 'Connection Properties' shows 99% signal strength and connection status as 'idle' via interface eth1.

***sudo ifup eth1 *** gives me:

**wifi0: unknown hardware address type 801 **

and after a lot of data this is eventually followed by:

[B]No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

***sudo dhclient*** gives me a similar output.

Routing table is empty.

PLEASE HELP ME THANKYOU VERY MUCH VERY KINDLY!

---

### Post by noob12 on 2007-08-06
Please post the output of these
```

lspci -nn

sudo lshw -C network

ifconfig -a

iwconfig

cat /etc/iftab

grep wifi0 /etc/modprobe.d/*

```

---

### Post by New101 on 2007-08-07
> **noob12 said:**
> Please post the output of these
```

lspci -nn

sudo lshw -C network

ifconfig -a

iwconfig

cat /etc/iftab

grep wifi0 /etc/modprobe.d/*

```

noob,

'Solved' the problem by installing Ubuntu version 7.04. Will avoid superfluous networking tools in the future.

Thanks.

---

### Post by noob12 on 2007-08-07
Got Feisty.  That's an approach. :-)

---

