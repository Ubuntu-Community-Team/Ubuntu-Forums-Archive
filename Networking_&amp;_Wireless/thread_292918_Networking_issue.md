---
title: "Networking issue"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by albox on 2006-11-04
Hi,
After installing Dapper, I'm having some problems with the network. Sometimes, after booting, it works and sometimes it doesn't (so that I have to reboot, because even if I use the KDE's network manager, I can't get an IP adress from the DHCP router).

> $ lspci -v | grep net
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4363 (rev 12)

First case (after booting, the network is working) :
> $ dmesg | grep eth0
[17179586.640000] sky2 eth0: addr X
[17179586.768000] sky2 eth0: phy read timeout
[17179586.772000] sky2 eth0: phy read timeout
[17179586.868000] sky2 eth0: phy read timeout
[17179586.872000] sky2 eth0: phy read timeout
[17179586.968000] sky2 eth0: phy read timeout
[17179586.972000] sky2 eth0: phy read timeout
[17179587.068000] sky2 eth0: phy read timeout
[17179587.072000] sky2 eth0: phy read timeout
[17179587.168000] sky2 eth0: phy read timeout
[17179587.172000] sky2 eth0: phy read timeout
[17179587.288000] sky2 eth0: phy read timeout
[17179587.292000] sky2 eth0: phy read timeout
[17179587.388000] sky2 eth0: phy read timeout
[17179587.392000] sky2 eth0: phy read timeout
[17179587.488000] sky2 eth0: phy read timeout
[17179587.492000] sky2 eth0: phy read timeout
[17179587.588000] sky2 eth0: phy read timeout
[17179587.592000] sky2 eth0: phy read timeout
[17179587.688000] sky2 eth0: phy read timeout
[17179587.692000] sky2 eth0: phy read timeout
[17179587.788000] sky2 eth0: phy read timeout
[17179587.792000] sky2 eth0: phy read timeout
[17179587.796000] sky2 eth0: enabling interface
[17179589.444000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none


Second case (after booting, the network DOES NOT work) :
> $ dmesg | grep eth0
[17189699.800000] sky2 eth0: disabling interface
[17189699.804000] sky2 eth0: phy write timeout
[17189699.812000] bridge-eth0: disabling the bridge
[17189699.836000] bridge-eth0: down
[17189701.952000] sky2 eth0: enabling interface
[17189701.956000] sky2 eth0: phy write timeout
[17189701.960000] sky2 eth0: phy write timeout
[17189701.964000] sky2 eth0: phy write timeout
[17189701.968000] sky2 eth0: phy write timeout
[17189701.972000] sky2 eth0: phy write timeout
[17189701.976000] sky2 eth0: phy write timeout
[17189701.980000] sky2 eth0: phy write timeout
[17189701.984000] sky2 eth0: phy write timeout
[17189701.988000] sky2 eth0: phy write timeout
[17189701.992000] sky2 eth0: phy write timeout
[17189701.996000] sky2 eth0: phy write timeout
[17189702.000000] bridge-eth0: enabling the bridge
[17189702.000000] bridge-eth0: up
[17189702.000000] ADDRCONF(NETDEV_UP): eth0: link is not ready

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0
Sending on   LPF/eth0
Sending on   Socket/fallback
DHCPRELEASE on eth0 to X.X.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0
Sending on   LPF/eth0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

$ ifconfig
eth0      Link encap:Ethernet  HWaddr X
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4294967293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4294967293 errors:0 dropped:0 overruns:0 carrier:4294967295
          collisions:4294967295 txqueuelen:1000
          RX bytes:4294967295 (3.9 GiB)  TX bytes:4294967295 (3.9 GiB)
          Interrupt:169

Does somebody have an idea about how to solve this problem ? It's really weird because when it doesn't work, the only thing I have to do is to reboot and it will work....

Thanks,
Al

---

### Post by ingo on 2006-11-05
right, some basics first. i take it you are on a desktop and wired up. 

my first guess would be to check the boot process and see whether there are any issues with eth0. observe and eliminate :)

---

### Post by albox on 2006-11-06
Sorry I forgot to say that I have a medion laptop with a wired network (kernel 2.6.15-27-686).

> my first guess would be to check the boot process and see whether there are any issues with eth0. observe and eliminate 
Do you have some ideas about how to do that ?

Thank you

---

### Post by ingo on 2006-11-06
i meant watching the boot process as the machine comes up, are there any error messages? do they correlate to those times when eth0 works or not? that was it really, nothing fancy (sorry).

however, i noticed that your hadware address (i.e. your MAC address) in case of failure is wrong. no wonder your router doesn't want to give you a lease! you can only get one with a proper MAC address. 

if the above is the case you should have the same problem with any OS as it would be down to faulty hardware :(

---

### Post by albox on 2006-11-06
No, I replaced my mac adress by X (privacy only). I also have Windows XP and everything works fine when I boot on it.

If I try to set an ip by myself (without using DHCP), it doesn't work too...

---

