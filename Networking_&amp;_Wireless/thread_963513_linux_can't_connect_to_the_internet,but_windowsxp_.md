---
title: "linux can't connect to the internet,but windowsxp can"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by qvbsx on 2008-10-30
Hey guys&#65306;
i install 3 OS ---xp+ubuntu8.04.1+fedora 8 
in the beginning ,3OS can connect 2 Internet
but today,only windows can&#65292;2 linux cannot 
 
when i login ubuntu ,i see a round red  point on network-monitor on the pannel,click it&#65292;a little widow reads&#65306;
“Could not find information on interface 'eth0:avahi' in /proc/net/dev ”
 
when fedora 8 is booting&#65292; click “show details”&#65292;when it comes to &#65306;
“determining IP information for eth0...”
then hold up for some minutes&#65292; at last&#65292;it said&#65306;
“failed ”
after i login fedora&#65292;i cannot connect to the net
 
 
i have tried lots of methods got from internet&#65292;such as diable ipv6&#12289;use static ip...all didnot work 
 
 
the following are the info from my fedora OS&#65306;
[COLOR="Red"][root@localhost ~]# dmesg|grep eth0 
sky2 eth0: addr 00:15:f2:6d:5b:89 
net eth0_rename: device_rename: sysfs_create_symlink failed (-17) 
net eth0: device_rename: sysfs_create_symlink failed (-17) 
udev: renamed network interface eth1 to eth0 
udev: renamed network interface eth0_rename to eth1 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
NETDEV WATCHDOG: eth0: transmit timed out 
eth0: Transmit timeout, status 0d 0000 c07f media 00. 
eth0: Tx queue start entry 4  dirty entry 0. 
eth0:  Tx descriptor 0 is 00082156. (queue head) 
eth0:  Tx descriptor 1 is 00082156. 
eth0:  Tx descriptor 2 is 00082156. 
eth0:  Tx descriptor 3 is 00082156. 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
NETDEV WATCHDOG: eth0: transmit timed out 
eth0: Transmit timeout, status 0d 0000 c07f media 00. 
eth0: Tx queue start entry 4  dirty entry 0. 
eth0:  Tx descriptor 0 is 00082156. (queue head) 
eth0:  Tx descriptor 1 is 00082156. 
eth0:  Tx descriptor 2 is 00082156. 
eth0:  Tx descriptor 3 is 00082156. 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
NETDEV WATCHDOG: eth0: transmit timed out 
eth0: Transmit timeout, status 0d 0000 c07f media 00. 
eth0: Tx queue start entry 4  dirty entry 0. 
eth0:  Tx descriptor 0 is 00082156. (queue head) 
eth0:  Tx descriptor 1 is 00082156. 
eth0:  Tx descriptor 2 is 00082156. 
eth0:  Tx descriptor 3 is 00082156. 
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
 
 
 
 
[root@localhost ~]# service   network   restart 
Shutting down loopback interface:                          [  OK  ] 
Bringing up loopback interface:                            [  OK  ] 
Bringing up interface eth0:   
Determining IP information for eth0...PING 192.168.10.1 (192.168.10.1) from 192.168.10.202 eth0: 56(84) bytes of data. 
 
--- 192.168.10.1 ping statistics --- 
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3000ms 
, pipe 3 
 failed. 
                                                           [FAILED] 
Bringing up interface eth1:   
Determining IP information for eth1... failed; no link present.  Check cable? 
                                                           [FAILED] 
[root@localhost ~]# ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0A:EB:4D:66:A2   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17 Base address:0x4c00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:10799 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10799 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:6876212 (6.5 MiB)  TX bytes:6876212 (6.5 MiB) 
 
 
[root@localhost ~]# dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.6-Fedora 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
Listening on LPF/eth0/00:0a:eb:4d:66:a2 
Sending on   LPF/eth0/00:0a:eb:4d:66:a2 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.[/COLOR]
 
 
i hope you can help me out &#65292;Thanks&#65281;

---

### Post by qvbsx on 2008-10-31
how to ?thanks

---

### Post by lH)4~mK0e on 2008-10-31
Please perform:

```

lspci | grep Network

```
and ```

hostname

```

From your ubuntu and your fedora installs and provide notation as to which one is which.

Thanks

---

### Post by qvbsx on 2008-10-31
> **miwarlock002 said:**
> Please perform:

```

lspci | grep Network

```
and ```

hostname

```

From your ubuntu and your fedora installs and provide notation as to which one is which.

Thanks

in Fedora&#65292;i got these results&#65306;
```
Fedora
[root@localhost ~]# lspci | grep net
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)

[root@localhost ~]# hostname
localhost.localdomain

[root@localhost ~]# cat /etc/modprobe.conf | grep eth0
alias eth0 8139too

[root@localhost ~]# mii-tool eth0
eth0: link ok

[root@localhost ~]# service netplugd status
netplugd is stopped

```

and in ubuntu&#65306;
```
qiu@qiubuntu:~$ lspci | grep net
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)

qiu@qiubuntu:~$ hostname
qiubuntu

qiu@qiubuntu:~$ hostname -i
127.0.1.1

qiu@qiubuntu:~$ sudo mii-tool eth0
eth0: link ok

```

Thanks

---

### Post by rc55 on 2008-10-31
I can confirm this happens when upgrading the kernel to 2.6.27-generic, with 81xx Realtek chipsets. :(

---

### Post by qvbsx on 2008-11-01
> **rc55 said:**
> I can confirm this happens when upgrading the kernel to 2.6.27-generic, with 81xx Realtek chipsets. :(

but my kernel is 2.6.24

---

### Post by lH)4~mK0e on 2008-11-03
It appears to me that you have two network cards.  One is working and getting an ip address and the other does not have the cable plugged in.  You may need to define which card you want to use as the Default Gateway Device in your Network Manager.  eth0 appears to be getting an ip address from 192.168.10.1.  Just go into the manual configuration for your Network Manager by going to System --> Administration --> Network.  If you don't need the other ethernet card (eth1) then just Unlock the application and then click on the eth1 entry, choose properties, and disable the card.

---

### Post by qvbsx on 2008-11-05
> **miwarlock002 said:**
> It appears to me that you have two network cards.  One is working and getting an ip address and the other does not have the cable plugged in.  You may need to define which card you want to use as the Default Gateway Device in your Network Manager.  eth0 appears to be getting an ip address from 192.168.10.1.  Just go into the manual configuration for your Network Manager by going to System --> Administration --> Network.  If you don't need the other ethernet card (eth1) then just Unlock the application and then click on the eth1 entry, choose properties, and disable the card.

In fact ,The network cards(eth1) was  broken&#65292;then i bought a new one&#65288;eth0&#65289;.
I disable the eth1&#65292;but eth0 still cannot get an ip

Thank you very much&#65292;anyhow&#65281;

---

### Post by qvbsx on 2008-11-14
at last ,someone said update the windows driver of 
eth0(8239) ,and i did that.so,it worked &#65281; i can connect to the internet now&#65281;
thank you all&#65281;

---

