---
title: "Network Card Problem w/ Clean Install 5.04"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by MyFirstUbuntu on 2005-08-03
I just installed ver 5.04 and am having a problem with detecting/configuring the network card.

The command lspci returns these two entries (I have two identical network cards installed):

0000:00:0e:0 Ethernet Controller: Intel Corp 82557/8/9 [Ethernet Pro 100] (rev 02)
0000:00:0f:0  Ethernet Controller: Intel Corp 82557/8/9 [Ethernet Pro 100] (rev 02)

It seems like the hardware is being detected, but I have no idea what to do next? How can I get the internet up and running?

Thanks in advance for your help!

---

### Post by aveline on 2005-08-03
[QUOTE=MyFirstUbuntu]I just installed ver 5.04 and am having a problem with detecting/configuring the network card.

The command lspci returns these two entries (I have two identical network cards installed):

0000:00:0e:0 Ethernet Controller: Intel Corp 82557/8/9 [Ethernet Pro 100] (rev 02)
0000:00:0f:0  Ethernet Controller: Intel Corp 82557/8/9 [Ethernet Pro 100] (rev 02)

It seems like the hardware is being detected, but I have no idea what to do next? How can I get the internet up and running?

Thanks in advance for your help![/QUOTE]
 what have you tried?  is it running at all?  do ifconfig -a eth0 post output pls.  are you using dhcp or static IPs?  if dhcp try  just "dhclient" and try to ping something like [www.google.com](www.google.com).

aveline

---

### Post by MyFirstUbuntu on 2005-08-03
eth0 is active and configured for DHCP

I have no way of saving the output of commands to disk so I typed the following in and I may have some minor typos or omissions in the output:

[INDENT]dhclient
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listenitnn on LPF/sit0
Sending on LPF/sit0
Listening on LPF/eth0/00:a0:c9:5e:ba:25
Sending on LPF/eth0/00:a0:c9:5e:ba:25
Listening on LPF/lo
Sending on LPF/lo
Sending on Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
...
DHCPDISCOVER on lo ...
DHCPDISCOVER on eth0 ...
DHCPDISCOVER on sit0 ...
DHCPDISCOVER on lo ...
DHCPDISCOVER on etho0 ...
...
NO DHCPOFFERS Received
No working leases in persistent database - sleepingf[/INDENT]


[INDENT]ifconfig -a eth0
eth0 :Link encap:Ethernet HWaddress 00:A0:C9:5E:BA:25
inet6 addr: fe80:2a0:c9ff:fe5e:ba25/64 Scope:Link
UP BROADCAST ULTICAST MTU:1500 mETRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packers:59 errors:59 dropped:0 overruns:0 carrier:59
collission:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX Bytes 18845 (18.4 KiB)[/INDENT]

I have removed the second nic card so eth0 is the only one installed in the box.

Any help would be appreciated.

---

### Post by aveline on 2005-08-13
[QUOTE=MyFirstUbuntu]eth0 is active and configured for DHCP

I have no way of saving the output of commands to disk so I typed the following in and I may have some minor typos or omissions in the output:

[INDENT]dhclient
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listenitnn on LPF/sit0
Sending on LPF/sit0
Listening on LPF/eth0/00:a0:c9:5e:ba:25
Sending on LPF/eth0/00:a0:c9:5e:ba:25
Listening on LPF/lo
Sending on LPF/lo
Sending on Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
...
DHCPDISCOVER on lo ...
DHCPDISCOVER on eth0 ...
DHCPDISCOVER on sit0 ...
DHCPDISCOVER on lo ...
DHCPDISCOVER on etho0 ...
...
NO DHCPOFFERS Received
No working leases in persistent database - sleepingf[/INDENT]


[INDENT]ifconfig -a eth0
eth0 :Link encap:Ethernet HWaddress 00:A0:C9:5E:BA:25
inet6 addr: fe80:2a0:c9ff:fe5e:ba25/64 Scope:Link
UP BROADCAST ULTICAST MTU:1500 mETRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packers:59 errors:59 dropped:0 overruns:0 carrier:59
collission:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX Bytes 18845 (18.4 KiB)[/INDENT]

I have removed the second nic card so eth0 is the only one installed in the box.

Any help would be appreciated.[/QUOTE]
 sorry to get back to you so late on this hon i missed this thread  & forgot i'd posted to it. :\

are you going through a router or is the nic connected directly to the modem?  can you ping anything?  try booting up and putting the words "noacpi" at the end of your kernel line in grub *Hit ESC when the grub menu starts counting down, look at the botom of the screen it tells you how to edit the file temporarily* see if that helps.

anyone else got ideas? throw em out :)

aveline

---

