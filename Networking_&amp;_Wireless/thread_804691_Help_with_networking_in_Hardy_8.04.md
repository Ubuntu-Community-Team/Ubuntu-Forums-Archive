---
title: "Help with networking in Hardy 8.04"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by castor_troy on 2008-05-23
These are my conn details as they appear in Windows.

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
DHCP Enabled. . . . . . . . . . . : No
Autoconfiguration Enabled . . . . : Yes
IPv4 Address. . . . . . . . . . . : 10.0.xx.xxx(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.xx.x
DNS Servers . . . . . . . . . . . : 10.0.xx.x
NetBIOS over Tcpip. . . . . . . . : Enabled

I selected static ip configuration(in manual configuration) in Ubuntu and entered my ip, subnet mask, Gateway and dns server. For using the internet i need to log on to the gateway using my browser.
But whenever i open firefox and try connecting to "http://10.0.xx.x" it says "The site you have entered seems to be valid but firefox cannot connect to the server at ........ ".
But i can see other computers connected to the network when i open "Places/Network". But firefox doesn't seem to work.

I saw another post in the forum and tried

/etc/rc.d/rc.inet1.conf

/etc/resolv.conf

sudo /etc/init.d/networking restart

But all it says is "Unable to resolve host at ....... ."

What am i doing wrong. Am i missing something ???
Any help would be appreciated.

---

### Post by mapes12 on 2008-05-23
You appear to have a class C subnetmask allocated to a class A private IP address.

Please could you post the output to:

```
ifconfig

```

```
cat /etc/resolv.conf
```

from Ubuntu

---

### Post by castor_troy on 2008-05-23
Code:
ifconfig

output: Unable to resolve host "......" .


Code: 
cat /etc/resolv.conf

Output:  Domain WORKGROUP
         nameserver 10.0.xx.x

The same config worked with win xp and is working with vista too.

---

### Post by mapes12 on 2008-05-23
Try changing the subnetmask to the correct configuration for a class A IP address:

```
255.0.0.0
```

Then restart you network:

```
sudo /etc/init.d/networking restart
```

---

### Post by castor_troy on 2008-05-23
That was a real quick reply.
Thanks a lot. It worked :) !!!
Right now posting through Hardy.
wonder how it worked in windoze though :confused: ?????

---

### Post by Fire_Chief on 2008-05-23
> **castor_troy said:**
>  For using the internet i need to log on to the gateway using my browser.
But whenever i open firefox and try connecting to "http://10.0.xx.x" it says "The site you have entered seems to be valid but firefox cannot connect to the server at ........ ".
But i can see other computers connected to the network when i open "Places/Network". But firefox doesn't seem to work.

What gateway are you using that requires you to logon prior to getting Internet access? The only places I usually see that behavior is in Hotels or resort locations offering public Internet access with a logon code or something to track usage.

Have you tried just going straight out to the Internet (i.e. google or yahoo)?

Your local network config does seem to be working since you can see other PCs. We might be able to help you faster if you don't xx out the last two octets of your IP addresses.

Cheers!

---

