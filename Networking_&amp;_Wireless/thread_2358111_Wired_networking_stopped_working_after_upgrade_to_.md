---
title: "Wired networking stopped working after upgrade to 16.10"
date: 2017-04-09
forum: Networking &amp; Wireless
---

### Post by Nition on 2017-04-09
I've got an Intel NUC 5CPYH that was running Ubuntu Gnome 16.04. After upgrade to 16.10 the ethernet has stopped working.

I get the following from *ipconfig -a*:

```

    enp3s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether f4:4d:30:68:64:d7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 54  base 0xe000  

    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 39653  bytes 2448001 (2.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 39653  bytes 2448001 (2.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.239  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6956:c8dd:48ef:944b  prefixlen 64  scopeid 0x20<link>
        ether 58:fb:84:ea:cb:35  txqueuelen 1000  (Ethernet)
        RX packets 4403131  bytes 6513554081 (6.5 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 284655  bytes 34231320 (34.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

And the following from *sudo lshw -C network*:

```

     *-network                 
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 81
       serial: 58:fb:84:ea:cb:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-46-generic firmware=22.361476.0 ip=192.168.1.239 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:314 memory:81300000-81301fff
     *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 15
       serial: f4:4d:30:68:64:d7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.042.00-NAPI duplex=full latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:310 ioport:e000(size=256) memory:81204000-81204fff memory:81200000-81203fff

```

Wired ethernet showing as disabled?

I tried *sudo ifconfig enp3s0 up*. This actually changed the **-network DISABLED* on the above ethernet info to show just **-network*, but the wired connection still doesn't work.

BIOS is the latest version. I'm not sure where to go from here.

---

### Post by Nition on 2017-04-09
Found quite a lot of false leads with this that never quite fixed it. Eventually decided to revert to 16.04 LTS where it used to work.

---

### Post by tiberiup on 2017-04-11
This should not be marked as resolved, I have the same issue with the wired connection not working after upgrading from 16.04 to 16.10.

Wifi it is working.

```
tibs@tibs-pc:~$ lspci | awk '/[Nn]et/ {print $1}' | xargs -i% lspci -ks %
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: ASRock Incorporation Motherboard (one of many)
	Kernel driver in use: r8168
	Kernel modules: r8168
tibs@tibs-pc:~$ 

```

LE: The solution from this post worked for me : [https://askubuntu.com/questions/894418/internet-died-after-ubuntu-16-10-upgrade#_=_](https://askubuntu.com/questions/894418/internet-died-after-ubuntu-16-10-upgrade#_=_)

```
Modify your interfaces file: (where enp9s0 is wired interface name)

sudo nano /etc/networking/interfaces

auto lo
iface lo inet loopback

auto enp9s0
iface enp9s0 inet dhcp
```
Save your changes and restart.

---

### Post by Nition on 2017-04-11
Thanks for posting your solution tiberiup, that solution wasn't one I saw so now I'm tempted to try upgrading again.

Seems like it just needs to be manually configured then? That makes some sense because in my research I came across the fact that apparently 16.10 changed how network management works, with non-wireless devices [now being treated as unmanaged]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1638842").

---

### Post by Nition on 2017-04-16
Success! I've upgraded again and tried the fix and it worked for me as well, thanks tiberiup. The only difference apart from my device name was that I didn't have a folder called "networking" - mine was called "network". I suspect that was just a typo in the instructions and it should say

```
sudo nano /etc/network/interfaces
```

The fix adds an "unmanaged wired connection" into the top right menu and the icon for a wired connection no longer shows up in the top bar, which is a little bit awkward, but it works and that's the main thing.

---

