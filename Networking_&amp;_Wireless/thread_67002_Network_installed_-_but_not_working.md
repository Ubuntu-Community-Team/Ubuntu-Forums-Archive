---
title: "Network installed - but not working???"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by OwenH on 2005-09-19
Hi, 

A recent new starter on ubuntu, my machine is a fresh install, and I'm tearing my hair out! 
My network card seems to be configured correctly but does not seem to work in ubuntu! It works in windows XP so its not a hardware issue.

The card is a Compaq Netelligent 10T PCI Intel UTP and as far as I can research on the internet the "intel e100" is the correct driver and this is the one being used.

However I get the following three error messages

> sit0: unknown hardware address type 776.
SIOCSIFFLAGS: Resource temporarily unavailable
send_packet: Network is down

A friend who has been running ubuntu for a while has the sit 0 one (due to IPv6) but it does not affect his network connection, so its unlikely to be that.

The "network is down" one appears to be a side effect so I believe the "SIOCSIFFLAGS" error is the root of the problem.

After searching online most answers where "make sure PnP is off in your bios" well pnp is off in my bios, though I have tried with it on, and I have also tried with manually setting IRQ numbers for each PCI slot in my bios.

output from various commands are below, 

Any help would be greatly appreciated.

```
root@onsputer:/home/hugheso #
root@onsputer:/home/hugheso # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:5F:D7:64:BA
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20446 (19.9 KiB)  TX bytes:20446 (19.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


root@onsputer:/home/hugheso # ifup eth0
ifup: interface eth0 already configured

root@onsputer:/home/hugheso # ifdown eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:80:5f:d7:64:ba
Sending on   LPF/eth0/00:80:5f:d7:64:ba
Sending on   Socket/fallback

root@onsputer:/home/hugheso # ifup eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:80:5f:d7:64:ba
Sending on   LPF/eth0/00:80:5f:d7:64:ba
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down


root@onsputer:/home/hugheso # dmesg | grep eth0
e100: eth0: e100_probe: addr 0xe7100000, irq 12, MAC addr 00:80:5F:D7:64:BA

root@onsputer:/home/hugheso # cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

auto eth0

root@onsputer:/home/hugheso # ping 192.168.0.1
connect: Network is unreachable

root@onsputer:/home/hugheso # lsmod | grep e100
e100                   32384  0
mii                     4736  1 e100

root@onsputer:/home/hugheso # lspci | grep Ethernet
0000:00:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 02)

root@onsputer:/mnt/share/Linux Drivers/lan # rmmod e100
root@onsputer:/mnt/share/Linux Drivers/lan # modprobe e100
root@onsputer:/mnt/share/Linux Drivers/lan # ifconfig eth0 up
SIOCSIFFLAGS: Resource temporarily unavailable

root@onsputer:/mnt/share/Linux Drivers/lan # dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:80:5f:d7:64:ba
Sending on   LPF/eth0/00:80:5f:d7:64:ba
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down

```

---

### Post by s_p_a_r_k_y on 2005-09-19
have you tried ```
dhclient eht0
```
and also please post your dmesg output

---

### Post by OwenH on 2005-09-19
[QUOTE=s_p_a_r_k_y]have you tried ```
dhclient eht0
```
and also please post your dmesg output[/QUOTE]
Hi, 
Thanks for replying, this is driving me up the wall .

```

root@onsputer:/mnt/share/Linux Drivers/lan # dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:80:5f:d7:64:ba
Sending on   LPF/eth0/00:80:5f:d7:64:ba
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
```

and 

```

root@onsputer:/home/hugheso # dmesg | grep eth0
e100: eth0: e100_probe: addr 0xe7100000, irq 12, MAC addr 00:80:5F:D7:64:BA

```

---

### Post by s_p_a_r_k_y on 2005-09-19
can you manually set an IP?

ifconfig eth0 192.168.0.10 or something?

---

### Post by OwenH on 2005-09-19
[QUOTE=s_p_a_r_k_y]can you manually set an IP?

ifconfig eth0 192.168.0.10 or something?[/QUOTE]
 I tried setting a static IP using the administrator network tool,

 (I can't remember what the binary was called)

that didn't work.

I'll try setting it with ifconfig tonight, well in a couple of hours!

am also going to try manually setting the IRQ numbers in the bios again and modprobing.

will report back on how it went!

---

### Post by OwenH on 2005-09-19
nope same problem.

SIOCSIFFLAGS: Resource temporarily unavailable

manually changing the IRQ and rmmod/modprobe didn't work either.

Anyone reading have any more ideas? I'm at a bit of a loss.
I have even tried moving the network card to a different PCI slot (in case of IRQ sharing)

---

### Post by OwenH on 2005-09-20
Hi,

From more searching on the internet it appears as if this is a case of too many items sharing a single IRQ.

does any one know how to list all IRQ ports being used ?

---

### Post by ampald on 2005-09-20
I think Im having the same issue with you as we speak. I have no idea, but try pinging the each computer. If that works, then you I hear you need to "forward". Of course, i have no idea what im saying, a friend of mine told me this. 

For me, i can ping each computer, just need to forward.

---

### Post by OwenH on 2005-09-20
Thanks for responding, 

but my problem is that my PC does not seem to be able to talk to the network card, and so cannot ping or even get an IP address on my local home network without getting a error message "SIOCSIFFLAGS: Resource temporarily unavailable"

---

### Post by ampald on 2005-09-20
sorry, i have no idea. Im totally new to this. But if you go to system>admin>networks, try giving it your own ip

---

### Post by Glut on 2005-09-21
[QUOTE=OwenH]From more searching on the internet it appears as if this is a case of too many items sharing a single IRQ.

does any one know how to list all IRQ ports being used ?[/QUOTE]
Not sure how to list those in use, but BIOS is the place to be to affect IRQ assignments. Depending on the BIOS options available, you may be able to limit or reassign some of the IRQs in use on your machine.

---

### Post by OwenH on 2005-09-26
No, I've tried setting a static IP address, 
its not to do with the cards Config, its something to do with the IRQs I think.

it constantly says 

```
SIOCSIFFLAGS: Resource temporarily unavailable
```

Does anyone know how to list what IRQs are being used so I can see any overlap??

---

### Post by OwenH on 2005-09-29
Just to say i got it working!!!!!

the driver I was using was the latest up todate one (e100) , which superseeded (<- if thats how you spell that) an older one called eepro100.

My Card being really old only seems to work with the old one! so much for backwards compatibility!

Peace out, and thanks to the guys who helped!

---

### Post by ailanpair on 2006-12-26
Worked like a dream for me too : Toshiba TE2300 Notebook. THANKS!!!

---

### Post by FLPCGuy on 2006-12-26
Sounds like the driver.  Did you follow the link from here to Sourceforge?
[http://www.cpqlinux.com/drivers.html](http://www.cpqlinux.com/drivers.html)                                            
I don't think all versions of that card use the same driver.
[http://sourceforge.net/projects/tlan/](http://sourceforge.net/projects/tlan/)

---

