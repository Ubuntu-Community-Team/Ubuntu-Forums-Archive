---
title: "Intrepid network problem"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by emco83 on 2008-10-31
i had a clean install to Intrepid and i must say that i have problem with the network.when i put the ip adress,netmask,gateway and dns server on ipv4 here it is:
adress 78.90.117.15
netmask 255.255.255.192
gateway 78.90.117.1
dns server 78.90.117.1
it connects to the network,but when i close it and than open again the ipv4 settings i've noticed that netmask is 24
so,everytime when i restart the pc,connection to the network is very slow.i hadn't this problem on Hardy
please somebody help

---

### Post by Iowan on 2008-10-31
What happens if you change 24 to 26? - Does it stay?

---

### Post by cariboo on 2008-10-31
There is a bug in network manager that will not allow settings to stick. See this thread:

[http://ubuntuforums.org/showthread.php?t=964777](http://ubuntuforums.org/showthread.php?t=964777)

Post #6 has a link to the bug.

Jim

---

