---
title: "drivers install for network card"
date: 2016-04-18
forum: Networking &amp; Wireless
---

### Post by ussr108 on 2016-04-18
Ok I tried everything and researched everywhere and now I'm desperate!

I installed a new tp&#8211;link network card (model no. tg-3269/tg-3468/tf-3200) and can't figure out how to install it because tp-link doesn't have .DEB installation file.

Here is the output after typing  ifconfig -a oh btw yes, I'm a newbie :(


```
enp7s0    Link encap:Ethernet  HWaddr 1c:6f:65:34:25:4a   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 enp8s0    Link encap:Ethernet  HWaddr 1c:6f:65:34:25:48   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:4986 errors:0 dropped:0 overruns:0 frame:0
           TX packets:4986 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:478034 (478.0 KB)  TX bytes:478034 (478.0 KB)
 
 
 wlx00c0ca4ac842 Link encap:Ethernet  HWaddr 00:c0:ca:4a:c8:42   
           inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
           inet6 addr: fe80::2c0:caff:fe4a:c842/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:22866 errors:0 dropped:0 overruns:0 frame:0
           TX packets:16383 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:22813392 (22.8 MB)  TX bytes:1934805 (1.9 MB)
```



thanks for any help men.

---

### Post by jeremy31 on 2016-04-19
If you have 2 ethernet cards, they appear to be working.  If there is supposed to be more post ```
lspci -nnk | grep -iA2 net; lshw -c net
```

---

### Post by ussr108 on 2016-04-20
I have drivers for this card&#8230; it's just that there is no .DEB file and I haven't a clue how to perform the instructions like 'makefile' sundance, or even if they work&#8230;

---

### Post by chili555 on 2016-04-20
Both of the network cards here have drivers and, in fact, the same driver. Please detach the USB wireless, connect the ethernet cable and show us:```
ifconfig
dmesg | grep enp
```

---

### Post by ussr108 on 2016-04-20
> **chili555 said:**
> Both of the network cards here have drivers and, in fact, the same driver. Please detach the USB wireless, connect the ethernet cable and show us:```
ifconfig
dmesg | grep enp
```

I unplugged cable and stopped wireless network first.
Then unplugged wireless USB again and restarted computer and got the same results below.

**    This is what ifconfig said:**
 enp7s0    Link encap:Ethernet  HWaddr 1c:6f:65:34:25:4a   

           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 enp8s0    Link encap:Ethernet  HWaddr 1c:6f:65:34:25:48   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:13409 errors:0 dropped:0 overruns:0 frame:0
           TX packets:13409 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:1390008 (1.3 MB)  TX bytes:1390008 (1.3 MB)
 
 
**  This is what came up when I posted dmesg | grep enp  **

 [    0.887223] r8169 0000:07:00.0 enp7s0: renamed from eth0

 [    1.072517] r8169 0000:08:00.0 enp8s0: renamed from eth1
 [    5.619997] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready

 [    5.764782] r8169 0000:07:00.0 enp7s0: link down
 [    5.764807] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
 [    5.766127] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
 [    5.904946] r8169 0000:08:00.0 enp8s0: link down
 [    5.904968] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready

---

### Post by chili555 on 2016-04-20
>     [ 5.904946] r8169 0000:08:00.0 enp8s0: link down
    [ [COLOR="#FF0000"]5.904968[/COLOR]] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready 

That is very early in the boot process, before the desktop is up and before Network Manager is running. With the USB wireless detached and the ethernet inserted, reboot and show us:```
dmesg | grep -e enp -e etwork
```>  I haven't a clue how to perform the instructions like 'makefile' sundance,Yours is not a sundance device.

---

### Post by ussr108 on 2016-04-20
> **chili555 said:**
> That is very early in the boot process, before the desktop is up and before Network Manager is running. With the USB wireless detached and the ethernet inserted, reboot and show us:```
dmesg | grep -e enp -e etwork
```

Ok, I unplugged USB wifi and also disabled wifi from connection manager, then rebooted and used this code:

dmesg | grep -e enp -e etwork

[    0.885636] r8169 0000:07:00.0 enp7s0: renamed from eth0
[    1.060815] r8169 0000:08:00.0 enp8s0: renamed from eth1
[    4.953757] audit: type=1400 audit(1461167968.643:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=540 comm="apparmor_parser"
[    4.953763] audit: type=1400 audit(1461167968.643:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=540 comm="apparmor_parser"
[    5.565873] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[    5.713013] r8169 0000:07:00.0 enp7s0: link down
[    5.713039] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[    5.714351] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[    5.852908] r8169 0000:08:00.0 enp8s0: link down
[    5.852942] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready

---

### Post by chili555 on 2016-04-20
I must be away for a couple of hours. I'll check back a bit later.

---

### Post by ussr108 on 2016-04-20
> **chili555 said:**
> I must be away for a couple of hours. I'll check back a bit later.


Ok thanks for your help.
I went to bios and enabled onboard Lan1 boot ROM and Lan2 boot ROM but to no avail.

---

### Post by chili555 on 2016-04-20
Are there any clues here?```
sudo ethtool enp7s0
sudo ethtool enp8s0
```I'd like to figure out which the cable is attached to. Whichever it is, or appears to be, try:```
sudo ethtool -s enp8s0 speed 100 autoneg off
```This assumes that we've deduced that the cable is attached to enp8s0 and not enp7s0.

Now see if there is any helpful clue here:```
cat /var/log/syslog | grep enp | tail -n15
```

---

### Post by ussr108 on 2016-04-20
> **chili555 said:**
> Are there any clues here?```
sudo ethtool enp7s0
sudo ethtool enp8s0
```I'd like to figure out which the cable is attached to. Whichever it is, or appears to be, try:```
sudo ethtool -s enp8s0 speed 100 autoneg off
```This assumes that we've deduced that the cable is attached to enp8s0 and not enp7s0.

Now see if there is any helpful clue here:```
cat /var/log/syslog | grep enp | tail -n15
```

```
**sudo ethtool enp7s0**
Settings for enp7s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no

```

```
**sudo ethtool enp8s0**
[sudo] password for iphone: 
Settings for enp8s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no

```

The code **sudo ethtool -s enp8s0 speed 100 autoneg off**  just asked for password and whenI hit enter nothing happened… 

I entered code **cat /var/log/syslog | grep enp | tail -n15  **Bit embarrassing calling my computer iphone lol
```

Apr 20 17:26:22 iphone NetworkManager[689]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0/net/enp7s0, iface: enp7s0)
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0/net/enp7s0, iface: enp7s0): no ifupdown configuration found.
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0/net/enp8s0, iface: enp8s0)
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0/net/enp8s0, iface: enp8s0): no ifupdown configuration found.
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  (enp8s0): new Ethernet device (carrier: OFF, driver: 'r8169', ifindex: 3)
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  (enp8s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 20 17:26:22 iphone kernel: [    5.607863] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
Apr 20 17:26:22 iphone kernel: [    5.748745] r8169 0000:08:00.0 enp8s0: link down
Apr 20 17:26:22 iphone kernel: [    5.748769] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  (enp8s0): created default wired connection 'Wired connection 3'
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  (enp7s0): new Ethernet device (carrier: OFF, driver: 'r8169', ifindex: 2)
Apr 20 17:26:22 iphone NetworkManager[689]: <info>  (enp7s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 20 17:26:22 iphone kernel: [    5.750567] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
Apr 20 17:26:22 iphone kernel: [    5.888815] r8169 0000:07:00.0 enp7s0: link down
Apr 20 17:26:22 iphone kernel: [    5.888837] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
```

---

### Post by ussr108 on 2016-04-20
I've checked the cable is working by connecting it to a laptop and it works fine.
But It's been plugged into TP-link card since I input all the above code.

---

### Post by ussr108 on 2016-04-20
Maybe this might help&#8230;
But the computer is showing the card&#8230;

It shows the wired Hardware address as 1C:6F:65:34:25:4A  and another wired connection as 1C:6F:65:34:25:48 
But it says the cable is unplugged.

---

### Post by ussr108 on 2016-04-20
Hmm, I think it's time to consider investing in a new card chili555 !   Just hope I don't have the same problem with the next one :o

---

### Post by ussr108 on 2016-04-20
Solved !!!!
I put card into another PCI slot disconnected wifi and it's working !!

---

### Post by ussr108 on 2016-04-20
Thanks to jeremy31 and  chili555 for all your help.



Here is something worthy of your consideration&#8230;
Why is Google so successful. Is it because they give away so much free stuff?

You might have a negative or positive opinion of them but there is no question of their success.

 
Karma is not what people think it is&#8211; you get bad for being bad. Karma is a wheel. You give out you get back, you give out, you get back. That's the truth behind tithing. Except when we give, we get far more in return than we gave out.

 
But it's not only software or money which one gets back. Knowledge and assistance given freely will result in one learning and being given far more expertise than one's peers who are not so altruistic.

 
In reality, when we assist another, we are really assisting ourselves.

---

