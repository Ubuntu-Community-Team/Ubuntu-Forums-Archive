---
title: "Wireless for Vaio FE21B doesn't work!!!!!"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Slothman on 2006-08-26
Hi, I've just installed Ubuntu on my laptop (Vaio FE21B) but can't get my wireless card to work!! Its an Intel PRO/Wireless 3945ABG. 

I've read lots of forums about using Ubuntu with this wireless card and everyone says that it works fine with Network Manager, I installed Network Manager but it did nothing. I have no idea how to configure this card so if anyone can help it would make me very happy :D

---

### Post by Slothman on 2006-08-27
Network Manager is only picking up my wired connection, no wireless connection is coming up!

I've looked at iwconfig and it says fequency: nan KHz access point: not associated

I'm guessing this means that its not configured properly? Can someone advise me on how to configure it please?

Thanks in advance

---

### Post by Slothman on 2006-08-27
Is anyone out there? I'm completely confused with this whole wireless thing! This is what i get from iwconfig and ifconfig

--------- iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"myHub"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0

sit0      no wireless extensions.

---------- ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:09:2B:46
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe09:2b46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1411707 (1.3 MiB)  TX bytes:128336 (125.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:6B:C9:47
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:26 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:15962 (15.5 KiB)
          Interrupt:185 Base address:0x4000 Memory:cc000000-cc000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1356 (1.3 KiB)  TX bytes:1356 (1.3 KiB)

Every time I try to configure the card in Network Settings it finds the router OK and seems to activate OK but it blatently doesn't work!!! Please please please can someone help? I'm totally lost!

---

