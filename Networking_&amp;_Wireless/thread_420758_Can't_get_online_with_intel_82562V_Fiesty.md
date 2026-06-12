---
title: "Can't get online with intel 82562V Fiesty"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by beowulf62381 on 2007-04-23
Ok I'm running Kubuntu 7.04 off the installer cd and can't get online. When I use KDE's network configuration gui to set my static IP or subnet to stick. (note the settings do seem stick in /etc/network/interfaces)

Given the above I can't ping my router or get on line :(
Any help would be much appreciated. As it is right now I am reduced to running Vista (Could not get XP preinstall let alone GNU/Linux)

the out put of

 lshw is

        *-network
             description: Ethernet interface
             product: 82562V 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@00:19.0
             logical name: eth0
             version: 02
             serial: 00:1a:92:52:45:eb
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.3-2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: iomemory:fdfc0000-fdfdffff iomemory:fdfff000-fdffffff ioport:ff00-ff1f irq:17

dmesg  grep is

[    7.141073] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:92:52:45:eb
[    7.203387] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   52.854135] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   52.858818] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   52.858821] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  314.308236] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  315.826324] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  315.826328] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  512.674451] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  512.680376] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  512.680381] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  745.177926] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  745.184981] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  745.184986] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1401.797697] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[ 1403.395577] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[ 1403.395582] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO

[    7.203387] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   52.854135] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   52.858818] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   52.858821] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  107.596656] eth0: no IPv6 routers present
[  314.308236] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  314.308721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  315.826324] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  315.826328] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  315.828302] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  326.764687] eth0: no IPv6 routers present
[  512.674451] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  512.674859] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  512.680376] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  512.680381] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  512.680424] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  522.943350] eth0: no IPv6 routers present
[  745.177926] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[  745.178260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  745.184981] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[  745.184986] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[  745.189158] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  755.842665] eth0: no IPv6 routers present
[ 1401.797697] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[ 1401.800259] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1403.395577] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[ 1403.395582] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1403.395626] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1414.054999] eth0: no IPv6 routers present

---

### Post by gradedcheese on 2007-04-24
I've had some issues with this driver lately.  Try this from a terminal:

```

sudo rmmod e1000; sudo modprobe e1000;

```

(ie: reload the driver) and then see if you can connect.  I'm not yet sure why, but occasionally I have to reload e1000 in order to get things like DHCP to work.

---

### Post by amitava82 on 2007-04-24
I have ubuntu 7.04 and having same problem since last 2 days. after installing, internet worked flawlessly for couple of days but now its not working :-( cant ping server. I tried reinstalling ubuntu but no help...

---

### Post by gradedcheese on 2007-04-24
> 
I tried reinstalling ubuntu but no help...


This isn't Windows ;)  ie: don't reinstall things randomly, you can always fix them.  Did reloading the driver help?  How about reloading NetworkManager too?

```

sudo killall NetworkManager
sudo rmmod e1000
sudo modprobe e1000
sudo NetworkManager

```

I'd like to know if that helps, if it does then we can at least file a more useful bug report, I guess.  I'll keep looking in to it with my laptop as well.

---

### Post by amitava82 on 2007-04-24
^^ tried your commands but no help. my wlan card is being detected as eth1 and it was working. i can ping other computer connected to the network but cant ping proxy server. I'm getting network unreachable error. i tried removing network manager and installed wicd, wifiradder but same problem... so weird and I'm helpless :-(

---

### Post by gradedcheese on 2007-04-24
ok: so you are using eth1 to connect?  Or you can ping via eth0?

---

### Post by amitava82 on 2007-04-24
ya eth1 is wireless lan and eth0 is wired which is disconnected. i've not tried eth0 yet..

---

### Post by beowulf62381 on 2007-04-24
Sorry for taking so long to get back, I hit post and went to bed. Thanks for all the help I am posting this from within Kubuntu running off the live install disk on a HP m7790y.

I used

> sudo killall NetworkManager
sudo rmmod e1000
sudo modprobe e1000
sudo NetworkManager

this worked although I did have to disable/renable using knetworkmanager, got a network unreachable every time I would try to ping my router.

OK I have installed Kubuntu on the computer's HD. I had to use the above method to get my NIC to work the first time, I have since rebooted and every thing seems to stick as it should thanks again for all your help.

p.s. How do I change the title to read solved or do the mods do that at their discretion?
After I install to harddisk will these settings stick across a reboot?

Thanks

---

