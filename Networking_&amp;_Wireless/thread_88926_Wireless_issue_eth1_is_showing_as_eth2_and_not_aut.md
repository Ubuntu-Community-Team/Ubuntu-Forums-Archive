---
title: "Wireless issue: eth1 is showing as eth2 and not auto loading"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by loon on 2005-11-11
Here is the problems and my research.

1) 
My wireless is not auto loading on boot. I am having to manually mount it each time.

2)
When trying to manually mount my wireless card, I notice in the networking setting eth0 (lan), eth1, and eth2.  When enabling eth1 and configure it for the wireless network, the network settings just hangs like its trying to pull an address but cant. When I cancel and disable it, then enable eth2 and configure it, I am able to get on the net right away.

Here is the ifconfig output file:

```
eth1      Link encap:UNSPEC  HWaddr 00-40-96-37-EA-55-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:802 errors:668 dropped:0 overruns:0 frame:668
          TX packets:939 errors:12 dropped:0 overruns:0 carrier:12
          collisions:178 txqueuelen:100
          RX bytes:581956 (568.3 KiB)  TX bytes:120801 (117.9 KiB)
          Interrupt:3 Base address:0x100

eth2      Link encap:Ethernet  HWaddr 00:40:96:37:EA:55
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:96ff:fe37:ea55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:802 errors:668 dropped:0 overruns:0 frame:668
          TX packets:939 errors:12 dropped:0 overruns:0 carrier:12
          collisions:178 txqueuelen:1000
          RX bytes:581956 (568.3 KiB)  TX bytes:120801 (117.9 KiB)
          Interrupt:3 Base address:0x100

```

Notice the MAC addresses?? hrmmm...
Looking deeper into the situation I found this interesting discovery!

```

ls /sys/class/net/eth1
address   broadcast  features  ifindex  mtu         tx_queue_len  weight
addr_len  carrier    flags     iflink   statistics  type

ls /sys/class/net/eth2
address   broadcast  **device**    flags    iflink  statistics    type
addr_len  carrier    features  ifindex  mtu     tx_queue_len  weight

ls -l device
lrwxrwxrwx  1 root root 0 2005-11-11 06:16 device -> ../../../devices/pci0000:00/0000:00:1e.0/0000:03:01.0/0.0


```

I tried correcting this by making a link from where the drivce directory is to where it is pointing in eth2. No luck, it will not let me.

```
sudo ln -s /sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/0.0/ device

ln: creating symbolic link `device' to `/sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/0.0/': Operation not permitted

```

Also my /etc/network/interface is:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface

iface eth2 inet dhcp
wireless-essid Thirdstrike
wireless-key 1234567890abcdef0987654321

auto eth2

```
 


Whew.... what a hand full and im stumped!  Any ideas?? 
This is a Cisco 350 card

Thanks!!

-loon

---

### Post by loon on 2005-11-12
first one to help me fix this gets a cookie. :)

jk

I hope someone might have a clue.

- loon

---

### Post by Cloudchaser on 2005-12-20
I am having this exact same problem with a Cisco 340  wireless card. Anyone have any solutions yet please?? This is the only distro to ever do that!

---

### Post by karld1 on 2006-02-28
Same here with Cisco Aironet 340.

---

### Post by syg00 on 2006-03-04
Looks like a problem in the init scripts - I added pcmcia (at S20) in rcS.d to ensure the card was ready when the network started.
Seems to work o.k., although the start is slow - looks like the network start activates everything, and eth2 is the interface the card uses. Didn't bother chasing it any further.

---

### Post by smartax on 2006-03-20
I've been having the same problem with an mpi350 card since about two kernel upgrades ago.  (I track the official Ubuntu precompiled kernels.)  My mpi350 card shows up as eth1 when I boot, but when I wake it up after an ACPI suspend-to-RAM nap, the card magically becomes eth2, and eth1 gets UNSPEC link encap.  I bet this happens precisely when the 'airo' module is loaded.  Has anyone else figured it out yet?

---

