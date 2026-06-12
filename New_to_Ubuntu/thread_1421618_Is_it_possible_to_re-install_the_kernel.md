---
title: "Is it possible to re-install the kernel?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by bwallum on 2010-03-04
Hi

I have changed motherboards and kept my Ubuntu system hardrives. Most things work fine. However the ethernet adapter on the motherboard doesn't and apparently needs a driver (forcedeth) that is incorporated into the kernel during initial system installation.

I have lots of tweaks in my setup and don't want to lose them with a fresh install of Ubuntu.

Can I just re-install the kernel?

---

### Post by Bachstelze on 2010-03-04
> **bwallum said:**
> However the ethernet adapter on the motherboard doesn't and apparently needs a driver (forcedeth) that is incorporated into the kernel during initial system installation.

What makes you think your Ethernet adapter doesn't work? The [font=monospace]forcedeth[/font] driver is available on all Ubuntu kernels.

---

### Post by coffeecat on 2010-03-04
The forcedeth driver is a loadable module that has come with every  version of the kernel for years now. Unless the forcedeth.ko file has  been deleted somehow, reinstalling the kernel is unlikely to help.

Have you tried running...

```
lsmod | grep force
```... from a terminal to see if the driver is in memory?

**Edit:** just had another thought. What have you done to try to get the ethernet connection working? If you've changed the motherboard, but still use your old installation, the system will name the new ethernet device as eth1, if the old one was eth0 - or eth2 if the previous was eth1, and so on. Have a look in Network Manager to see what's going on.

---

### Post by bwallum on 2010-03-04
> **coffeecat said:**
> Have you tried running...

```
lsmod | grep force
```... from a terminal to see if the driver is in memory?

**Edit:** just had another thought. What have you done to try to get the ethernet connection working? If you've changed the motherboard, but still use your old installation, the system will name the new ethernet device as eth1, if the old one was eth0 - or eth2 if the previous was eth1, and so on. Have a look in Network Manager to see what's going on.
This is what I get:-

i2c_nforce2             8168  0 
forcedeth              61292  0 

and since changing the motherboard I now have eth2 (thats the one onboard that I want to get going) and eth3, which is a pci ethernet card that i have inserted into my pc to get internet connectivity.

If I plug my ethernet cable into the eth2 port on the mb it does not work. Reboot makes no difference. It is turned on in the cmos.

I fiddled around with my /etc/network/interfaces file but couldn't get a combination to work. I am currently running with the following commented out file on the pci card (eth3).

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# allow-hotplug eth2
#auto eth2
#iface eth2 inet dhcp
#up route add default gw 192.168.1.254 dev eth2

#auto eth3
#iface eth3 inet dhcp
#up route add default gw 192.168.1.254 dev eth3

---

### Post by coffeecat on 2010-03-04
Perhaps the onboard ethernet device is faulty. I have two desktops both with motherboards with (different) nvidia chipsets - hence they use the forcedeth driver for ethernet. I've used every version of Ubuntu from Hardy through to Lucid Alpha on one or both (and some other distros as well), and ethernet has always "just worked".

To see whether the issue is in your installation or is a hardware failure, try booting up with a live CD without the PCI card in situ, but with the onboard ethernet connected to your router. If the onboard ethernet is OK, network manager will simply connect it automatically as you boot up. If it doesn't connect, or if NM can't detect an interface, then almost certainly the ethernet adapter is dead.

---

### Post by bwallum on 2010-03-06
Thanks for your help. I tried removing the pci card ethernet adapter, plugged the ethernet wire into the on board adapter and started the machine using a karmic live cd. The onboard adapter could be seen but would not work. It seems to be working very slowly with some indication of TX and RX activity.

I then put the pci card ethernet adapter back in and restarted normally. I took another look at the /etc/network/interfaces file and rearranged it to:> auto eth2 eth3
 mapping eth2 eth3
     script /usr/share/doc/ifupdown/examples/get-mac-address.sh
     map e2:e2:e2:e2:e2:e2 onboardlan
     map e3:e3:e3:e3:e3:e3 pcicardlan
 iface onboardlan inet static
     address 192.168.1.100
     network 192.168.1.0
     netmask 255.255.255.0
     broadcast 192.168.1.255
     gateway 192.168.1.254
 iface pcicardlan inet static
     address 192.168.1.101
     network 182/168.1.0
     netmask 255.255.255.0
     broadcast 192.168.1.255
     gateway 192.168.1.254
I tried the ethernet wire in the onboard port and ran ifconfig -a. I got the following output:- ```
$ ifconfig -a
```> eth2      Link encap:Ethernet  HWaddr e2:e2:e2:e2:e2:e2  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe9c:ec20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3281 (3.2 KB)  TX bytes:13331 (13.3 KB)
          Interrupt:27 Base address:0xe000 

eth3      Link encap:Ethernet  HWaddr e3:e3:e3:e3:e3:e3 
          inet6 addr: fe80::202:b3ff:fe1d:fc49/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4097361 (4.0 MB)  TX bytes:567911 (567.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34692 (34.6 KB)  TX bytes:34692 (34.6 KB)Note that ifconfig reports the eth2 link running.

I ran ```
$ dmesg | grep eth
```and got:-> [    2.281316] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.281722] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    2.281727] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.463216] e100: eth0: e100_probe: addr 0xfdaff000, irq 18, MAC addr e3:e3:e3:e3:e3:e3
[    2.821003] forcedeth 0000:00:07.0: ifname eth1, PHY OUI 0x732 @ 1, addr e2:e2:e2:e2:e2:e2
[    2.821008] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[   31.420166] udev: renamed network interface eth0 to eth3
[   31.423294] udev: renamed network interface eth1 to eth2
[   33.031640] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   33.034090] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   33.034278] eth2: no link during initialization.
[   33.034901] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   35.011520] e100: eth3 NIC Link is Up 100 Mbps Full Duplex
[   35.090514] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   45.591264] eth3: no IPv6 routers present
[ 3205.011568] e100: eth3 NIC Link is Down
[ 3211.093555] eth2: link up.
[ 3211.094508] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[ 3221.561273] eth2: no IPv6 routers present
[ 3514.370768] eth2: link down.
[ 3531.011524] e100: eth3 NIC Link is Up 100 Mbps Full Duplex
[ 4285.011562] e100: eth3 NIC Link is Down
[ 4302.873807] eth2: link up.It says that eth2 is up.

However, I could not get to the router. 

I then plugged the cable back into my pci card and ran ```
$ ifconfig -a
```> eth2      Link encap:Ethernet  HWaddr e2:e2:e2:e2:e2:e2  
          inet6 addr: fe80::2e0:4dff:fe9c:ec20/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30530 (30.5 KB)  TX bytes:40564 (40.5 KB)
          Interrupt:27 Base address:0xe000 

eth3      Link encap:Ethernet  HWaddr e3:e3:e3:e3:e3:e3 
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe1d:fc49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4529469 (4.5 MB)  TX bytes:626512 (626.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58804 (58.8 KB)  TX bytes:58804 (58.8 KB)and```
$ dmesg | grep eth
```> [    2.281316] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.281722] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    2.281727] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.463216] e100: eth0: e100_probe: addr 0xfdaff000, irq 18, MAC addr e3:e3:e3:e3:e3:e3
[    2.821003] forcedeth 0000:00:07.0: ifname eth1, PHY OUI 0x732 @ 1, addr e2:e2:e2:e2:e2:e2
[    2.821008] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[   31.420166] udev: renamed network interface eth0 to eth3
[   31.423294] udev: renamed network interface eth1 to eth2
[   33.031640] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   33.034090] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   33.034278] eth2: no link during initialization.
[   33.034901] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   35.011520] e100: eth3 NIC Link is Up 100 Mbps Full Duplex
[   35.090514] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   45.591264] eth3: no IPv6 routers present
[ 3205.011568] e100: eth3 NIC Link is Down
[ 3211.093555] eth2: link up.
[ 3211.094508] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[ 3221.561273] eth2: no IPv6 routers present
[ 3514.370768] eth2: link down.
[ 3531.011524] e100: eth3 NIC Link is Up 100 Mbps Full Duplex
[ 4285.011562] e100: eth3 NIC Link is Down
[ 4302.873807] eth2: link up.
[ 5652.682930] eth2: link down.
[ 5663.011555] e100: eth3 NIC Link is Up 100 Mbps Full DuplexNow I can reach the router through eth3 but cannot get through to the internet. 

However, by setting up eth3 in Network Manager as an added connection I can get it to work normally. Very interesting but confusing.

So....

I would like to know more about how Network Manager and the /etc/network/interfaces file work together. 

Where does Network Manager store it's configuration files?
Is WICD a better time investment?
------------------------------
EDIT (for anybody following)
There are two ways of configuring networks. The 'legacy' way is to configure the /etc/network/interfaces file. The minimum requirement is > auto lo
iface lo inet loopbackIf you use Gnome's Network Manager (comes as default in Ubuntu installs) then it is probably best to leave the /etc/network/interfaces file with minimum content. If you configure in the interfaces file you cannot edit with Network Manager.

The Network Manager configuration files are best explained by the [Gnome Network Manager]("http://live.gnome.org/NetworkManager/SystemSettings") 

WICD did not work fully for me. It removes Network Manager as it installs and does appear to run ok. Then when I rebooted it asked for permission to do something with the system, I agree... and lost all network connection. To recover, reboot in rescue mode and choose command line with networking. Then recover Network Manager with ```
sudo apt-get install network-manager
```Then reboot.

---

