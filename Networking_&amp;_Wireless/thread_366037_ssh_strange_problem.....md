---
title: "ssh strange problem...."
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by ibans on 2007-02-20
Hallo!

Trying to ssh to a remote machine, say A with xxx.xxx.xxx.xx and
I receive the message

ssh: connect to host xxx.xxx.xxx.xx port 22: No route to host

Then, I ssh succesfully to an other remote machine, say B, and from
B I can ssh to the machine A without any problem.....

What is wrong here??????????
The machine A is unreachable for me. 
ping does not work as well....

Last week I was ftping and sshing to the machine A without any problem at all.
From Windows, or using other computers (and keeping the same connection)
I can connect to A. 

Smth is wrong with  and I do not have a clue.


Any Idea???

ThanX,
I.

---

### Post by koenn on 2007-02-20
it's a network problem, not specific to ssh.
explain how these computers are connected, what their ip addresses are, and so on

---

### Post by ibans on 2007-02-22
All these computers are remotely connected.Either, I use the ADSL connection at
home (dynanic IP) or at a library near by, I cannot connect - using LINUX - at the
remote machine of interest , say machine A. However, I can connect to the
machine A either through an other remore machine B (which is actually located
in a different city) or by just rebooting my laptop to Windows... So, the problem
has to do with the network settings of my ubuntu laptop...  Any clue?

---

### Post by koenn on 2007-02-23
> So, the problem
has to do with the network settings of my ubuntu laptop... Any clue?
Maybe a wrong/missing default gateway ?

other than that, I'd have to see the ip addresses and routing tables of the computers involved see if they match. 

```
sudo ifconfig
sudo netstat -nr
```

---

### Post by ibans on 2007-02-26
My computer:
-----------------------
$sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:C5:24:E4:D0
          inet addr:147.102.34.162  Bcast:147.102.34.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185

eth1      Link encap:Ethercnet  HWaddr 00:13:02:99:34:36
          inet addr:147.102.232.146  Bcast:147.102.232.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe99:3436/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18020 errors:0 dropped:1379 overruns:0 frame:0
          TX packets:4077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3112309 (2.9 MiB)  TX bytes:701448 (685.0 KiB)


$sudo netstat -nr

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
147.102.34.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
147.102.232.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         147.102.232.200 0.0.0.0         UG        0 0          0 eth1
0.0.0.0         147.102.34.200  0.0.0.0         UG        0 0          0 eth0

          Interrupt:177 Base address:0x2000 Memory:dcfff000-dcffffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1518 (1.4 KiB)  TX bytes:1518 (1.4 KiB)

________________________________________________________________________________
One of the remote machines I cannot login directly from my computer:

$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:47:A4:01:34
          inet addr:147.102.34.111  Bcast:147.102.34.255  Mask:255.255.255.0
          inet6 addr: 2001:648:2000:22:203:47ff:fea4:134/64 Scope:Global
          inet6 addr: fe80::203:47ff:fea4:134/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3529001 errors:0 dropped:0 overruns:0 frame:4
          TX packets:571187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:153226 txqueuelen:1000
          RX bytes:1121872136 (1069.9 Mb)  TX bytes:76537725 (72.9 Mb)
          Interrupt:11 Base address:0x9000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4352 (4.2 Kb)  TX bytes:4352 (4.2 Kb)

$netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
147.102.34.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U         0 0          0 lo
0.0.0.0         147.102.34.200  0.0.0.0         UG        0 0          0 eth0


[SIZE="5"]THANKS!!!!![/SIZE]

---

### Post by ibans on 2007-02-26
I fixed it! I had used in the past same IP for my network card with that one of
of the remote machines I cannot login. Eventhough I was using
my wirelless connection now and had a DHP configuration, there was
a conflict! Your adviced helped me to find the solution.

[SIZE="7"]THANK YOU[/SIZE]

---

### Post by koenn on 2007-02-26
great. 
:)

---

