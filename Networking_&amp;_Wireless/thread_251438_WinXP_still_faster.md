---
title: "WinXP still faster"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by jslmsca on 2006-09-05
Here's my setup and a couple tests:

eth0      Link encap:Ethernet  HWaddr 00:11:43:78:AA:C1
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe78:aac1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1450  Metric:1
          RX packets:2888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2051940 (1.9 MiB)  TX bytes:641310 (626.2 KiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:3F:A4:CF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1219 (1.1 KiB)  TX bytes:1219 (1.1 KiB)

**:~$ dig [www.ubuntu.com](www.ubuntu.com)**

; <<>> DiG 9.3.2 <<>> [www.ubuntu.com](www.ubuntu.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48047
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 2

;; QUESTION SECTION:
;[www.ubuntu.com](www.ubuntu.com).                        IN      A

;; ANSWER SECTION:
[www.ubuntu.com](www.ubuntu.com).         600     IN      A       82.211.81.166

;; AUTHORITY SECTION:
ubuntu.com.             7993    IN      NS      ns1.blackcatnetworks.co.uk.
ubuntu.com.             7993    IN      NS      ns.ubuntu.com.
ubuntu.com.             7993    IN      NS      ns0.blackcatnetworks.co.uk.

;; ADDITIONAL SECTION:
ns0.blackcatnetworks.co.uk. 26021 IN    A       193.201.200.34
ns1.blackcatnetworks.co.uk. 26021 IN    A       69.55.225.40

;; Query time: 178 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Sep  5 10:58:59 2006
;; MSG SIZE  rcvd: 155

**:~$ ping -c 3 [www.ubuntu.com](www.ubuntu.com)**
ping: unknown host [www.ubuntu.com](www.ubuntu.com)

In WinXP:

[B]>ping -n 3 [www.ubuntu.com](www.ubuntu.com)
[/B]
Pinging [www.ubuntu.com](www.ubuntu.com) [82.211.81.166] with 32 bytes of data:

Reply from 82.211.81.166: bytes=32 time=145ms TTL=52
Request timed out
Reply from 82.211.81.166: bytes=32 time=142ms TTL=52

Ping statistics for [82.211.81.166]:
     Packets: Sent=3 Received=2 Lost=1 (33% loss)
Approximate round trip in milli-seconds:
     Minimum=142ms, Maximum=145ms, Average=143ms

~~~~~
I've changed MTU to startup with 1450.  I'm using ADSL and am directly connected to a D-Link DSL 604+ router.  I tried MTU 1492 as well with no discernable difference from 1450.

My ISP assigns my IP address but I've noticed that WinXP shows my IP address as 192.168.0.2 but Ubuntu is showing it as 192.168.0.3.  The only way to change this would be to disable DHCP and assign myself a static IP address?  Is this something I should do?  I'm loading web pages fine but it usually >10 seconds (as measured by FasterFox) after the initial click to see any changes in Firefox.  It took 63 seconds for this message to appear after I clicked 'Submit'.

Thanks.

---

### Post by Jussi Kukkonen on 2006-09-05
> My ISP assigns my IP address but I've noticed that WinXP shows my IP address as 192.168.0.2 but Ubuntu is showing it as 192.168.0.3
These are probably not IPs given by your ISP but local IPs given by your router. Check its settings if you want to use a (locally) static IP.

I remember the speed problem being mentioned before, but can't remember what was the solution -- could have been disabling IPv6. Try searching the forums, something should come up...

---

