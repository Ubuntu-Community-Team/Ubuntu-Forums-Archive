---
title: "Failed to start Raise network interfaces, but eth0 is up - after upgrade to 16.04"
date: 2017-05-06
forum: Networking &amp; Wireless
---

### Post by oliver- on 2017-05-06
Hi i just upgraded my ubuntu 14.04 server to 16.04 (this is a root server i have not physical access to) and now i have a networking problem.
During boot i get this error: Failed to start Raise network interfaces

The output of: systemctl status networking.service
shows:
```

&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Sun 2017-05-07 00:46:14 CEST; 17min ago
     Docs: man:interfaces(5)
  Process: 1066 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 947 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCCESS)
 Main PID: 1066 (code=exited, status=1/FAILURE)

May 07 00:46:11 rs206878 ifup[1066]: /sbin/ifup: waiting for lock on /run/network/ifstate.eth0
May 07 00:46:14 rs206878 ifup[1066]: RTNETLINK answers: File exists
May 07 00:46:14 rs206878 ifup[1066]: Failed to bring up eth0.
May 07 00:46:14 rs206878 ifup[1066]: RTNETLINK answers: File exists
May 07 00:46:14 rs206878 ifup[1066]: run-parts: /etc/network/if-up.d/v6_defgw exited with return code 2
May 07 00:46:14 rs206878 ifup[1066]: /sbin/ifup: post-up script failed.
May 07 00:46:14 rs206878 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
May 07 00:46:14 rs206878 systemd[1]: Failed to start Raise network interfaces.
May 07 00:46:14 rs206878 systemd[1]: networking.service: Unit entered failed state.
May 07 00:46:14 rs206878 systemd[1]: networking.service: Failed with result 'exit-code'.

```

ifconfig -a shows (i replaced the IP by XX.XX.XX.XX):
```

eth0      Link encap:Ethernet  HWaddr 00:1c:42:7d:6e:57  
          inet addr:XX.XX.XX.XX  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: XX.XX.XX.XX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421012 (421.0 KB)  TX bytes:596038 (596.0 KB)
          Interrupt:23 Base address:0x8200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164533 (164.5 KB)  TX bytes:164533 (164.5 KB)

```

and /etc/network/interfaces looks like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address XX.XX.XX.XX
        netmask 255.255.255.255
        broadcast 0.0.0.0
        up route -A inet add 169.255.30.1 dev eth0
        up route -A inet add default gw 169.255.30.1

iface eth0 inet6 static
        pre-down ip -6 addr flush dev eth0 scope global || :

```

Can anyone help me resolving this issue?
Google gives a lot of info about this error but none of the solutions helped in my situation.


btw: i can access the server via SSH, and the webserver is reachable too! But my mailserver is not working, i do not know why but i hope it will work again after this problem is solved.

---

