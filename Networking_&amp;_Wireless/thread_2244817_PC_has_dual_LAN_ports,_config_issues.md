---
title: "PC has dual LAN ports, config issues"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by vimfuego on 2014-09-18
Hi All,

I have a new PC that has two Two Intel GbE LAN ports on it., but it would appear only one port seems to be working properly (well, as expected they might work).
If I plug in to 'em1' then I have a network connection, if I plug in to 'p5p1' I can't access the internet and the system sits there waiting for a network connection and finally gives up.

Also in hunting on this topic it seems the 'norm' used to be to have them as eth0 and eth1 ? I am running server 14.04, any harm in renaming them to eth0 and eth1 (which makes more sense to me than em1 and p5p1).

Thanks.

> **em1       Link encap:Ethernet  HWaddr 74:d4:35:11:d7:72  **
          inet addr:192.168.0.42  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe11:d772/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2576786 (2.5 MB)  TX bytes:284942 (284.9 KB)
          Interrupt:20 Memory:f0700000-f0720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

**p5p1      Link encap:Ethernet  HWaddr 74:d4:35:11:d7:52  **
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f0500000-f0600000 


---

### Post by vimfuego on 2014-09-19
I just wanted to add to this, I am logged in to the system via Webmin, it sees the two LAN ports (em1 and p5p1) ok in 'Active Now'.

[TABLE="class: ui_table sortable ui_columns, width: 100%"]
[TR="class: maintitle, bgcolor: #D0E0FC"]
[TD="width: 5"][/TD]
[TD="width: 20%"]**[Name   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[Type   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[IPv4 address   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[Netmask   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[IPv6 address   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 5%"]**[Status   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[/TR]
[TR="class: mainbody row1, bgcolor: #f5f5f5"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 20%"][em1]("https://192.168.0.42:10000/net/edit_aifc.cgi?idx=0")[/TD]
[TD="width: 20%"]Ethernet 1000Mb/s[/TD]
[TD="width: 20%"]192.168.0.42[/TD]
[TD="width: 20%"]255.255.255.0[/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"]Up[/TD]
[/TR]
[TR="class: mainbody row0, bgcolor: #f5f5f5"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 20%"][lo]("https://192.168.0.42:10000/net/edit_aifc.cgi?idx=1")[/TD]
[TD="width: 20%"]Loopback[/TD]
[TD="width: 20%"]127.0.0.1[/TD]
[TD="width: 20%"]255.0.0.0[/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"]Up[/TD]
[/TR]
[TR="class: mainbody row1, bgcolor: #f5f5f5"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 20%"][p5p1]("https://192.168.0.42:10000/net/edit_aifc.cgi?idx=2")[/TD]
[TD="width: 20%"]Ethernet 1000Mb/s[/TD]
[TD="width: 20%"]10.0.0.4[/TD]
[TD="width: 20%"]255.255.255.0[/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"]Up[/TD]
[/TR]
[/TABLE]

When I go to 'Activated At Boot' it shows this...

[TABLE="class: ui_table sortable ui_columns, width: 100%"]
[TR="class: maintitle, bgcolor: #D0E0FC"]
[TD="width: 5"][/TD]
[TD="width: 20%"]**[Name   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[Type   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[IPv4 address   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[Netmask   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 20%"]**[IPv6 address   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[TD="width: 5%"]**[Activate   ]("https://192.168.0.42:10000/net/list_ifcs.cgi?mode=boot#")**[/TD]
[/TR]
[TR="class: mainbody row1, bgcolor: #f5f5f5"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 20%"][em1]("https://192.168.0.42:10000/net/edit_bifc.cgi?idx=1")[/TD]
[TD="width: 20%"]Ethernet[/TD]
[TD="width: 20%"]From DHCP[/TD]
[TD="width: 20%"]From DHCP[/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"]Yes[/TD]
[/TR]
[TR="class: mainbody row0"]
[TD="width: 5"][/TD]
[TD="width: 20%"]lo[/TD]
[TD="width: 20%"]Loopback[/TD]
[TD="width: 20%"]No address configured[/TD]
[TD="width: 20%"]None[/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"]Yes[/TD]
[/TR]
[/TABLE]

If I try to add p5p1 to be activated at boot this error occurs....

**Failed to save interface : Missing or invalid interface name**

Really :(, why can it see p5p1 ok in the 'Active Now' yet it fails when I attempt to add that interface to the 'Activate At Boot' option?

Thanks.

---

