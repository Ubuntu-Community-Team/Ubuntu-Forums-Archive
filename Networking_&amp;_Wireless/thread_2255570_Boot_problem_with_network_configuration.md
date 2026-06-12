---
title: "Boot problem with network configuration"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by cjsmall on 2014-12-06
I have an system with two ethernet interfaces.  A previous installation of Ubuntu 14.04.1 created the **eth0** and **eth1** interfaces.

I just wiped the system clean and did a fresh install of Ubuntu server 14.10 and am having some problem with the network interfaces.  The system boots with the interfaces named **p1p1** and **p2p1**.   In an attempt to get them renamed as **eth0** and **eth1**, I created the **/etc/udevrules.d/70-persistent-net.rules** file with entries like:

```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:3f:49:e8:1a:31", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:3f:49:e8:1a:32", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

This did not work.  Further investigation on the net indicated that the **KERNEL=="eth*"** section of these entries needed to be removed as this pattern was failing to match the **p1p1** and **p2p1** strings.  Eliminating this did seem to address that problem, but I still face a significant delay during boot when it reaches the step "*Waiting for network configuration*".  15 to 20 seconds go by and then the following message is displayed:  "*Waiting up to 60 more seconds for network configuration.*"  Eventually the boot sequence continues and the system comes up with the proper set up.

```
# ifconfig -a | grep -i hwaddr
eth0      Link encap:Ethernet  HWaddr e0:3f:49:e8:1a:31
eth1      Link encap:Ethernet  HWaddr e0:3f:49:e8:1a:32  
```

I took a look in the log files:

```
# dmesg | grep  udev
[    7.258036] systemd-udevd[285]: starting version 208
[    7.288593] random: systemd-udevd urandom read with 10 bits of entropy available
[   13.578590] systemd-udevd[293]: renamed network interface eth1 to p2p1
[   13.786378] systemd-udevd[406]: renamed network interface eth0 to p1p1
[   14.928531] systemd-udevd[628]: starting version 208
[   15.080344] systemd-udevd[669]: renamed network interface p1p1 to eth0
[   15.161976] systemd-udevd[672]: renamed network interface p2p1 to eth1
```

and see that two instances of **systemd-udevd** are being started with the first improperly naming the devices and the secone then naming them back.  I'm guessing that this song and dance are responsible for the delay in the boot sequence.  Further investigation turned up this interesting discussion from over two years ago:

[https://lists.fedoraproject.org/pipermail/users/2012-October/425940.html](https://lists.fedoraproject.org/pipermail/users/2012-October/425940.html)

Here is the **biosdevname** output:

```

# biosdevname -d
BIOS device: p1p1
Kernel name: eth0
Permanent MAC: E0:3F:49:E8:1A:31
Assigned MAC : E0:3F:49:E8:1A:31
ifIndex: 2
Driver: e1000e
Driver version: 2.3.2-k
Firmware version: 2.1-3
Bus Info: 0000:06:00.0
PCI name      : 0000:06:00.0
PCI Slot      : 1
Index in slot: 1

BIOS device: p2p1
Kernel name: eth1
Permanent MAC: E0:3F:49:E8:1A:32
Assigned MAC : E0:3F:49:E8:1A:32
ifIndex: 3
Driver: e1000e
Driver version: 2.3.2-k
Firmware version: 2.1-3
Bus Info: 0000:07:00.0
PCI name      : 0000:07:00.0
PCI Slot      : 2
Index in slot: 1
```

Any suggestions how to get things more streamlined so that I can eliminate this network configuration boondoggle during boot?

Thanks.

---

### Post by cjsmall on 2015-01-09
The problem described persisted, but in researching other issues, I solved the problem.

My **/etc/network/interfaces** file had these two static entries:

```
auto eth0
   iface eth0 inet static
   address 204.107.91.3
   netmask 255.255.255.0
   gateway 204.107.91.254
   dns-nameservers 199.181.164.1 199.181.164.2 68.87.69.146 68.87.85.98

auto eth1
   iface eth0 inet static
   address 204.107.91.4
   netmask 255.255.255.0
   gateway 204.107.91.254
   dns-nameservers 199.181.164.1 199.181.164.2 68.87.69.146 68.87.85.98
```

Although both interfaces were initially coming up live, upon subsequent reboots I started finding that although **ifconfig -a **showed both devices configured, and I could ping both interfaces locally, only one interface was active across the LAN -- and the active interface would varry between reboots.  More investigation yielded this:

```
# ifquery -l
lo
eth0
eth1

# ifquery --state
lo=lo
eth0=eth0
```

So **eth1** (in this case) was actually not configured even though it was displayed properly by **ipconfig -a**.  When I tried to bring the interface up:

```
# ifup eth1
RTNETLINK answers: File exists
Failed to bring up eth1
```

This message led me to articles where it was stated that only one gateway could be defined in the interfaces file.  I eliminated the duplicate gateway and dns-nameservers from the second entry and when I rebooted the system, the 2 minute boot delay was gone and both interface came up properly configured.  So the entries no look like this:

```
auto eth0
   iface eth0 inet static
   address 204.107.91.3
   netmask 255.255.255.0
   gateway 204.107.91.254
   dns-nameservers 199.181.164.1 199.181.164.2 68.87.69.146 68.87.85.98

auto eth1
   iface eth0 inet static
   address 204.107.91.4
   netmask 255.255.255.0
```

I hope this information helps others.

---

