---
title: "New Server: Internal Server Issue or Config Problem?"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by GoJimbo on 2007-03-21
Hi,

Troubleshooting a problem with my new Dell Poweredge 1950 server and got this response from the network folks on campus.

"It is probably having some internal server issues.  From the inside network, it responds to ping but not to http, telnet or ftp.  The server operating system appears up, but nothing else seems to be working."

Any idea what the issue may be or how I can isolate it?

Running 6.06 LTS, server has SAS 5i Controller/No Raid, Broadcom NetXtreme II 5708 Ethernet NIC.

Thanks.

---

### Post by GoJimbo on 2007-03-21
Just found this thread [http://www.ubuntuforums.org/showthread.php?t=323667]("http://www.ubuntuforums.org/showthread.php?t=323667")

Wondering if this is my problem, missing driver for Broadcom Ethernet or maybe the cable is in the wrong port...sounds like they're reversed?

---

### Post by GoJimbo on 2007-03-22
Checked and the cable was connected to eth1 interface 1, connected it to interface 2 eth0 and restarted.  

I assume the output below means I am missing the driver?  

Have read this [[COLOR="Red"]POST[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=226114&highlight=poweredge+2950")
and wondering if I should just try Edgy.  

Still not completely sure what the problem is, have a dying PowerEdge 2300 thats been running EzProxy successfully for years.  Got a new PowerEdge 1950 and setup EzProxy but I cannot browse to the machine outside the campus network, on campus I can but not through port 2048 that the software utilizes.   Got the response in my first post from the network manager on campus when I mentioned the issue.

**lsmod**

bnx2                  148292  0

**lspci grep | Broadcom**

0000:03:00.0 PCI bridge: Broadcom: Unknown device 0103 (rev c2)
0000:04:00.0 Ethernet controller: Broadcom Corporation: Unknown device 164c (rev 11)
0000:07:00.0 PCI bridge: Broadcom: Unknown device 0103 (rev c2)
0000:08:00.0 Ethernet controller: Broadcom Corporation: Unknown device 164c (rev 11)
jim@library:~$ lspci | grep net
0000:04:00.0 Ethernet controller: Broadcom Corporation: Unknown device 164c (rev 11)
0000:08:00.0 Ethernet controller: Broadcom Corporation: Unknown device 164c (rev 11)

**ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:15:C5:EB:76:B7
          inet addr:xxx.xx.xxx.xx  Bcast:216.44.254.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feeb:76b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3011118 (2.8 MiB)  TX bytes:356463 (348.1 KiB)
          Interrupt:169 Memory:f4000000-f4011100

eth1      Link encap:Ethernet  HWaddr 00:15:C5:EB:76:B5
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:f8000000-f8011100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88 (88.0 b)  TX bytes:88 (88.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

---

### Post by GoJimbo on 2007-03-23
Solved, turned out to be an Apache issue.

---

