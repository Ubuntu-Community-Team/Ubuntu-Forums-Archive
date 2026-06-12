---
title: "Wireless Connected,But Not Working"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by oni_lunk on 2007-07-04
System: Dell Inspiron 6400
Wireless Card: Intel(R) PRO Wireless 3945 ABG

Problem: I'm able to connect to the (Unsecure) Network, however, I'm unable to access sites through firefox.
I'm also not able to Retrieve Updates.

The Wireless works as normal in Windows,but not in Ubuntu Studio...
I've looked around here and found nothing to help me.
Can anyone help me out?

---

### Post by sj3fk3 on 2007-07-05
> **oni_lunk said:**
> System: Dell Inspiron 6400
Wireless Card: Intel(R) PRO Wireless 3945 ABG

Problem: I'm able to connect to the (Unsecure) Network, however, I'm unable to access sites through firefox.
I'm also not able to Retrieve Updates.

The Wireless works as normal in Windows,but not in Ubuntu Studio...
I've looked around here and found nothing to help me.
Can anyone help me out?

Open a terminal and type iwconfig, show us what you see (copy - paste)

---

### Post by oni_lunk on 2007-07-05
Here's What Terminal Shows:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:CC:EB:02   
          Bit Rate:18 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=43/100  Signal level=-83 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

---

### Post by sj3fk3 on 2007-07-05
> **oni_lunk said:**
> Here's What Terminal Shows:

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:CC:EB:02   

          Bit Rate:18 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=43/100  Signal level=-83 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

Ok and is that the AP you want to connect to? Because it's signal is kinda weak if you ask me. anyway if it is then type ifconfig eth1 as well and show the output. You might just not be getting an IP-Address, guessing it's a vanilla Linksys wrt that should be issuing a IP with DHCP.

---

### Post by oni_lunk on 2007-07-05
eth1   Link encap:Ethernet  HWaddr 00:18:DE:81:E9:33  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe81:e933/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:3 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:596 (596.0 b)  TX bytes:1255 (1.2 KiB)
          Interrupt:16 Base address:0x8000 Memory:efdff000-efdfffff

---

### Post by sj3fk3 on 2007-07-05
> **oni_lunk said:**
> eth1   Link encap:Ethernet  HWaddr 00:18:DE:81:E9:33  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          Interrupt:16 Base address:0x8000 Memory:efdff000-efdfffff

ha, the plot thickens... Thats does all seem ok, last thing I can think of:
What does cat /etc/resolv.conf say and route -n

---

