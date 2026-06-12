---
title: "PC - Laptop Crossover Connection, with PC wifi'd to internet"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by SuperAndy on 2007-07-16
My PC is wifi'd to the internet with a ralink card, meaning i cant use network manager to configure the connection. So by changing my interfaces file i have got the wifi working. Now, i thought i could do the same for the eth0 connection, on my laptop and the PC. I can get both machines to ping each other, so I know the basic connection is sound.

As i have openSSH installed on my pc, i can get an ssh terminal on my laptop to my pc, but when i try and use this to get an ssh tunnel working using the "connect to server..." thing in ubuntu, i get a timeout. I have tried all the options, port 22, or leaving it blank, and nothing. its really quite strange. It has worked in the past when i move my laptop downstairs, closer to the AP [the PC is in range but the laptop isn't], and using wifi. Basically, i would really like to get this working, for file transfers.

Also, i cannot connect to the internet while my wired connection is 'up' on my PC, and i cannot ping the AP. I just get "desination host unreachable". If i then type "sudo ifconfig eth0 down", the internet comes back. I would also like to know if this is a permanent problem, and also what are the implications of having the same IP on both the wired and wifi connection.

To clarify, i'm not bothered really about getting the internet working on my laptop through the cable.

The interfaces file for the PC is shown below:
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet static
#address 192.168.2.253
#netmask 255.255.255.0

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra1
iface ra1 inet static
address 192.168.2.52
gateway 192.168.2.1
        pre-up ifconfig ra1 up
        pre-up iwconfig ra1 essid "USR9110"
        pre-up iwconfig ra1 mode Managed

```

and ifconfig when both connections are up:

```

eth0      Link encap:Ethernet  HWaddr 00:15:F2:02:C7:3F  
          inet addr:192.168.2.253  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148024 (144.5 KiB)  TX bytes:186598 (182.2 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50969 (49.7 KiB)  TX bytes:50969 (49.7 KiB)

ra1       Link encap:Ethernet  HWaddr 00:13:D3:7A:40:4F  
          inet addr:192.168.2.52  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe7a:404f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:14850 txqueuelen:1000 
          RX bytes:53376406 (50.9 MiB)  TX bytes:4810970 (4.5 MiB)
          Interrupt:20

```

The interfaces file for the laptop:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.254
netmask 255.255.255.0

```

If anyone could help it would be greatly appreciated.

Andy

---

### Post by SuperAndy on 2007-07-17
bump

---

### Post by SuperAndy on 2007-07-17
ok, i solved the problem.

stupidly decided to have the crossover network and the wifi network on the same subnet. its all fixed, and everyone is happy.

---

