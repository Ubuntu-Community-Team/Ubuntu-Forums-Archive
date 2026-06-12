---
title: "Bridge error/warning message"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by ibejohn on 2007-02-10
I've been using an Ubuntu LAMP server (console only) primarily as a file/media server for a few months now and so far it's worked out great.  A friend of mine recently suggested adding another NIC to it so I could bridge them to provide increased bandwidth to/from the server so I added a spare one I had from another PC.  Next I installed the bridge-utils package and then manually created a bridge using information from [http://www.tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html](http://www.tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html)
```
[FONT="Courier New"]# ifconfig eth0 down
# ifconfig eth1 down
# ifconfig eth0 0.0.0.0 up
# ifconfig eth1 0.0.0.0 up
# brctl addbr br0
# brctl stp br0 off
# brctl addif br0 eth0
# brctl addif br0 eth1
# ifconfig br0 192.168.13.5 up
# route add gw 192.168.13.1

# brctl stp br0 on

# ifconfig eth1 down[/FONT]
```I had to add the "brctl stp br0 on" command as my network was experiencing a problem without it; I assume this is because I have a switch as the backbone of my network.  Also, I took the eth1 interface down just to stop the messages showing up in the log for this post.

The bridge seems to work with both interfaces up, but I noted a message in my log files:
```
[FONT="Courier New"]eth1: received packet with  own address as source address[/FONT]
```It repeats about every 2-4 seconds.  I did notice that the bridge MAC address is the same as eth1, and believe it is because eth1 has the lower address of eth1 and eth0.  I tried changing the bridge MAC address using ifconfig (after taking it down), but it failed.

Can anyone suggest how I can remove this error/warning or tell me more about what might be causing it?  

Thanks,
  John

I have provided logs and dumps below in case they are useful to helping figure out what might be wrong.

My network topology is:
```
[FONT="Courier New"]Internet
   |
Cable Modem
   |
Router1
   |
Switch------------------+------+ ... +
   |                    |      |     |
Router2-+-------+       |      |     |
  |     |       |       |      |     |
eth0  eth1      |       |      |     |
  |    |        |       |      |     |
  Server        PC      PC     PC    PC[/FONT]
```
**/var/log/messages dump**
```
[FONT="Courier New"]Feb 10 15:58:41  eth1: Setting full-duplex based on MII#1 link partner capability of 41e1.
Feb 10 15:58:57  Bridge firewalling registered
Feb 10 15:59:11  eth0: Promiscuous mode enabled.
Feb 10 15:59:11  device eth0 entered promiscuous mode
Feb 10 15:59:11  audit(1171144751.940:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Feb 10 15:59:19  eth1: Promiscuous mode enabled.
Feb 10 15:59:19  device eth1 entered promiscuous mode
Feb 10 15:59:19  audit(1171144759.860:5): dev=eth1 prom=256 old_prom=0 auid=4294967295
Feb 10 15:59:52  br0: port 2(eth1) entering learning state
Feb 10 15:59:52  br0: port 1(eth0) entering learning state
Feb 10 16:00:07  br0: topology change detected, propagating
Feb 10 16:00:07  br0: port 2(eth1) entering forwarding state
Feb 10 16:00:07  br0: topology change detected, propagating
Feb 10 16:00:07  br0: port 1(eth0) entering forwarding state
Feb 10 16:01:18  eth0: received packet with  own address as source address
Feb 10 16:01:18  eth1: received packet with  own address as source address
Feb 10 16:01:18  br0: topology change detected, propagating
Feb 10 16:01:18  br0: port 2(eth1) entering blocking state
Feb 10 16:01:19  eth1: received packet with  own address as source address
Feb 10 16:01:20  eth1: received packet with  own address as source address
Feb 10 16:01:22  eth1: received packet with  own address as source address
Feb 10 16:01:24  eth1: received packet with  own address as source address
Feb 10 16:01:26  eth1: received packet with  own address as source address
Feb 10 16:01:28  eth1: received packet with  own address as source address
Feb 10 16:01:30  eth1: received packet with  own address as source address
Feb 10 16:01:32  eth1: received packet with  own address as source address
Feb 10 16:01:34  eth1: received packet with  own address as source address
Feb 10 16:01:36  eth1: received packet with  own address as source address
Feb 10 16:01:38  eth1: received packet with  own address as source address
Feb 10 16:01:40  eth1: received packet with  own address as source address
Feb 10 16:01:44  printk: 1 messages suppressed.
Feb 10 16:01:44  eth1: received packet with  own address as source address
Feb 10 16:01:48  printk: 1 messages suppressed.
Feb 10 16:01:48  eth1: received packet with  own address as source address
Feb 10 16:01:54  printk: 2 messages suppressed.
Feb 10 16:01:54  eth1: received packet with  own address as source address
Feb 10 16:01:58  printk: 1 messages suppressed.
Feb 10 16:01:58  eth1: received packet with  own address as source address
Feb 10 16:02:04  printk: 2 messages suppressed.
Feb 10 16:02:04  eth1: received packet with  own address as source address
Feb 10 16:02:08  printk: 1 messages suppressed.
Feb 10 16:02:08  eth1: received packet with  own address as source address
Feb 10 16:02:10  eth1: Promiscuous mode enabled.
Feb 10 16:02:10  br0: port 2(eth1) entering disabled state[/FONT]
```
```
# ifconfig
[FONT="Courier New"]br0       Link encap:Ethernet  HWaddr 00:03:6D:16:C2:42
          inet addr:192.168.13.5  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::203:6dff:fe16:c242/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4051486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:641459080 (611.7 MiB)  TX bytes:37428 (36.5 KiB)

eth0      Link encap:Ethernet  HWaddr 00:E0:4D:06:BC:4C
          inet6 addr: fe80::2e0:4dff:fe06:bc4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20846930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12195036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24891062219 (23.1 GiB)  TX bytes:1133246613 (1.0 GiB)
          Interrupt:225 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:03:6D:16:C2:42
          inet6 addr: fe80::203:6dff:fe16:c242/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2256357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1794525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:519188112 (495.1 MiB)  TX bytes:178810382 (170.5 MiB)
          Interrupt:233 Base address:0xac00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11757 (11.4 KiB)  TX bytes:11757 (11.4 KiB)[/FONT]
```
```
[FONT="Courier New"]# brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.00036d16c242       yes             eth1
                                                        eth0

# brctl showstp br0
br0
 bridge id              8000.00036d16c242
 designated root        8000.00036d16c242
 root port                 0                    path cost                  0
 max age                  20.00                 bridge max age            20.00
 hello time                2.00                 bridge hello time          2.00
 forward delay            15.00                 bridge forward delay      15.00
 ageing time             300.01
 hello timer               0.76                 tcn timer                  0.00
 topology change timer     0.00                 gc timer                   0.06
 flags


eth1 (2)
 port id                8002                    state                  disabled
 designated root        8000.00036d16c242       path cost                100
 designated bridge      8000.00036d16c242       message age timer          0.00
 designated port        8002                    forward delay timer        0.00
 designated cost           0                    hold timer                 0.00
 flags

eth0 (1)
 port id                8001                    state                forwarding
 designated root        8000.00036d16c242       path cost                 19
 designated bridge      8000.00036d16c242       message age timer          0.00
 designated port        8001                    forward delay timer        0.00
 designated cost           0                    hold timer                 0.00
 flags[/FONT]
```

---

