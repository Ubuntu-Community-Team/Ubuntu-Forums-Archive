---
title: "Wired network quit working after update."
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by sean_fitz on 2007-10-16
After installing updates yesterday, my wired network stopped working.  It still gets an IP address via DHCP, but I can't connect to, or ping anything on the internet or local network.  Connection doesn't show up in Network Manager either.  It's a dual boot system, and everything is fine in WInXP.  Wireless still works fine.  I'm lost here.  Please help me!!!!

```
sfitzgerald@sfmob:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:A4:CF:D0:8A  
          inet addr:172.16.100.125  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::217:a4ff:fecf:d08a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213892 (208.8 KiB)  TX bytes:5583 (5.4 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:27:87:C4  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe27:87c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:982 errors:0 dropped:109 overruns:0 frame:0
          TX packets:932 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:676497 (660.6 KiB)  TX bytes:171250 (167.2 KiB)
          Interrupt:17 Base address:0xa000 Memory:f4000000-f4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:582 (582.0 b)  TX bytes:582 (582.0 b)
```



```
sfitzgerald@sfmob:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

---

### Post by noob12 on 2007-10-16
Do you get any errors either right in the terminal or in the output of **tail /var/log/kern.log** when you are trying to ping a local address?

Can you post the output of these
```

route -n

sudo iptables -nL

```

---

### Post by sean_fitz on 2007-10-17
Thanks for the reply.


```
sfitzgerald@sfmob:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.0.254    0.0.0.0         UG    0      0        0 eth0
sfitzgerald@sfmob:~$ sudo iptables -nL
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
MOBLOCK_IN  0    --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  0    --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
MOBLOCK_OUT  0    --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
NFQUEUE    0    --  0.0.0.0/0            0.0.0.0/0           NFQUEUE num 0
```


Ping didn't give me any errors.


```

sfitzgerald@sfmob:~$ ping 172.16.100.200
PING 172.16.100.200 (172.16.100.200) 56(84) bytes of data.

--- 172.16.100.200 ping statistics ---
413 packets transmitted, 0 received, 100% packet loss, time 412089ms
```


```
sfitzgerald@sfmob:~$ tail /var/log/kern.log
Oct 17 06:44:41 sfmob kernel: [  336.876000] b44: eth0: Flow control is off for TX and off for RX.
Oct 17 06:44:41 sfmob kernel: [  336.876000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 17 06:44:52 sfmob kernel: [  347.008000] eth0: no IPv6 routers present
Oct 17 06:45:07 sfmob kernel: [  362.264000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 17 07:06:23 sfmob kernel: [ 1640.692000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Oct 17 07:07:21 sfmob kernel: [ 1699.164000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 17 07:07:23 sfmob kernel: [ 1700.756000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 17 07:07:25 sfmob kernel: [ 1702.896000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 17 07:07:26 sfmob kernel: [ 1704.436000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 17 07:07:44 sfmob kernel: [ 1722.380000] eth1: no IPv6 routers present
```

I don't see anything relevant in the log, but I don't really know what to look for.  Most activity was from turning on my wireless card(eth1).

---

### Post by noob12 on 2007-10-17
What happens if you put the firewall down?

---

### Post by sean_fitz on 2007-10-17
I'm assuming you mean my hardware firewall, and it makes no difference.

---

### Post by noob12 on 2007-10-17
No your iptables firewall "moblock"  .

---

### Post by noob12 on 2007-10-17
Here are commands to flush the firewall rules:

Get a root shell
```

sudo /bin/sh

```

Then run these commands running in that shell
```

for t in filter nat mangle raw; do  iptables -t $t --flush; done

# Set all filter chains to policy ACCEPT by default
for c in INPUT FORWARD OUTPUT; do iptables -t filter -P $c ACCEPT; done

# Delete all non-built-in filter chains
iptables -t filter -X

```

---

### Post by sean_fitz on 2007-10-17
It worked after shutting the firewall down.  
Started working after the first command line.

```
for t in filter nat mangle raw; do  iptables -t $t --flush; done
```

Should this be a permanent fix, or just for the current session?  It stops working after a reboot.

---

### Post by noob12 on 2007-10-17
Those aren't commands you should run each time.  It was just to verify that the firewall was the issue.

They confirmed that the source of the problem is a misconfigured "moblock" firewall, which is a wrapper around the lower level iptables rules that we flushed.

You must have installed "moblock" at some point because I don't think it is in the default installation.

My recommendations are:

(1) Either uninstall the moblock firewall or spend more time learning to configure it so that it isn't shutting you out from the world.

(2) I think that "firestarter" is a more friendly GUI firewall configuration tool if you require one.

I don't use either, because I configure iptables directly via command-line tools.   I'm not really prepared to help you with the firewall configs, but that's another topic that several others on the forum might be able and willing to help with if you start a thread on that.

---

### Post by sean_fitz on 2007-10-17
Great!!  I can take it from here.  Thanks for the help!!!

---

