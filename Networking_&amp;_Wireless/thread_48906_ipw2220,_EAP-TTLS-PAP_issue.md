---
title: "ipw2220, EAP-TTLS-PAP issue"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by srijith on 2005-07-14
I am running HP customised version of Ubuntu 5.0.4 on my nc6120, The wireless card in this baby is Intel PRO/Wireless 2200BG miniPCI adapter.

I am having problem getting an IP address from our wireless network that uses TTLS with PAP. The xsupplicant log shows a success in authentication:

```

[ALL] Got EAP-Success!
Authenticated!

```
but the dhclient does not get an IP address.

iwconfig strangely shows that it is associated with the correct AP, but the encryption key is all 0s:
```

Encryption key:0000-0000-0000-0000-0000-0000-00

```


The xsupplicant config file I am using is as follows:
```

network_list = ABC-Campusnet
allow_interfaces = eth0
deny_interfaces=eth1,lo,sit0
logfile=/var/log/xsupplicant.log
first_auth_command = <BEGIN_COMMAND>sudo dhclient eth0<END_COMMAND>
ABC-Campusnet
{
        type = wireless
        wireless_control = yes
        allow_types = eap-ttls
        identity =<BEGIN_ID>username@abc.edu<END_ID>
        eap-ttls {
                root_cert = /home/srijith/root.pem
                chunk_size = 1398
                random_file = /dev/random
                phase2_type = pap
                pap {
                        username =<BEGIN_UNAME>username@abc.edu<END_UNAME>
                        password =<BEGIN_PASS>passwd<END_PASS>
                }
        }
}


```

The shell script file I run to get the things to work is as follows:

```

#!/bin/bash
sudo ifconfig eth0 down
sudo /sbin/iwconfig eth0 mode Managed enc open essid ABC-Campusnet
sudo ifconfig eth0 up
sudo killall xsupplicant
sudo killall dhclient3
sudo killall dhclient
sudo rm /var/run/xsupplicant.pid
sudo xsupplicant -c /home/srijith/abc-xsup.conf -i eth0 -d7 -f
sudo ifconfig eth0

```

The last part of the output is as follows:
```

[ALL] Got EAP-Success!
Authenticated!
[ALL] Processing command : sudo dhclient eth0
[ALL] Returning command : sudo dhclient eth0
[ALL] Actual command being called is sudo
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

irda0: unknown hardware address type 783
sit0: unknown hardware address type 776
irda0: unknown hardware address type 783
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:f0:2b:68:04
Sending on   LPF/eth0/00:12:f0:2b:68:04
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
..
..


```

What is strange is that I had gotten this setup to work using the same script and config file (using a more updated version of xsupplicant) when I had FC4 installed on the same machine. I had to thrash FC4 due to hibernation and sleep issues and installed Ubuntu. Everything works *perfectly*, except for the wireless.

Someone, please make my day! :)

---

### Post by bubbers214 on 2005-07-20
I am having the exact same problem with my campus wireless, it says it authenticates but it never recieves an IP address.

---

### Post by srijith on 2005-07-26
Haa... finally got it to work. The Xsupplicant 1.0.1 found with Ubuntu 5.04 does not work. You need to download and compile the xsupplicant 1.2pre1. If you have problems with compiling the source with errors of missing "-lcrypto", install the libssl-dev package.

---

### Post by Kitty on 2005-07-28
[QUOTE=srijith]Haa... finally got it to work. The Xsupplicant 1.0.1 found with Ubuntu 5.04 does not work. You need to download and compile the xsupplicant 1.2pre1. If you have problems with compiling the source with errors of missing "-lcrypto", install the libssl-dev package.[/QUOTE]
 I got the same problem and found a solution.

With xsupplicant 1.0.1, try this line :
first_auth_command = <BEGIN_COMMAND> echo "I am connected"<END_COMMAND>

When you see it, you just have to enter "sudo dhclient eth0"

---

### Post by srijith on 2005-07-28
That is strange, "sudo dhclient eth0" does not work when set as the first_auth_command so I can't see why your trick works!

Also, I tried to do something similar with 1.0.1 I removed the first_auth_command and put a "-d7 -f" to the xsupplicant call and when the "AUTHENTICATED" message came up, I tried to execute "sudo dhclient eth0". It did not work.

Oh well, I am happy with my 1.2pre1

---

