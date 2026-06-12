---
title: "VirtualBox Host Interface Networking breaks cifs mounts"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by imk on 2008-09-16
I recently installed VirtualBox on Ubuntu Hardy. I found the default NAT networking in guest OSes to be very slow so I set up Host Interface Networking guided by the Networking section of the Ubuntu doc here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox).

This transformed the speed of guest OS networking, but there was a snag: cifs (samba) mounts on my Ubuntu host were broken thereafter. I hope somebody knows why.

I have a network attached storage device on my domestic network. In my Ubuntu bash profile I mount this device with a "sudo mount -t cifs...." command which gave me the NAS at /mnt/slug/imk, where I would run a daily rsync backup to it.

Ever since I configured my host to support host interface networking for Virtual box, this mount command has failed with:

mount: wrong fs type, bad option, bad superblock on //slug/imk,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

which amounts to "something went wrong".

To support HIN for VirtualBox I did just two things on my host:-

1) Changed my /etc/network/interfaces from this:

>>>>>>>>>>>>>>>>>>>>>>>>>
# The loopback network interface
auto lo
iface lo inet loopback
<<<<<<<<<<<<<<<<<<<<<<<<<


to this:

>>>>>>>>>>>>>>>>>>>>>>>>>
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports eth0

# The loopback network interface
auto lo
iface lo inet loopback
<<<<<<<<<<<<<<<<<<<<<<<<<

2) Created /etc/vbox/interfaces like this:

>>>>>>>>>>>>>>>>>>>>>>>>>
# Each line should be of the format :
# <interface name> <user name> [<bridge>]
vbox0 imk br0
vbox1 imk br0
<<<<<<<<<<<<<<<<<<<<<<<<<

There are no networking problems in my boot logs. The relevant tracts look like:

>>>>>>>>>>>>>>>>>>>>>>>>>
Sep 16 18:25:48 puter kernel: [   44.162006] b44: eth0: Link is up at 100 Mbps, full duplex.
Sep 16 18:25:48 puter kernel: [   44.162010] b44: eth0: Flow control is off for TX and off for RX.
Sep 16 18:25:48 puter kernel: [   44.163573] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 16 18:25:48 puter kernel: [   44.454182] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 16 18:25:48 puter kernel: [   44.525724] Bridge firewalling registered
Sep 16 18:25:48 puter kernel: [   44.528750] device eth0 entered promiscuous mode
Sep 16 18:25:48 puter kernel: [   44.528760] audit(1221585928.175:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
Sep 16 18:25:48 puter kernel: [   44.530775] br0: port 1(eth0) entering learning state
Sep 16 18:25:48 puter kernel: [   59.527042] br0: topology change detected, propagating
Sep 16 18:25:48 puter kernel: [   59.527047] br0: port 1(eth0) entering forwarding state
Sep 16 18:25:48 puter kernel: [   60.688374] NET: Registered protocol family 17
...
...
Sep 16 18:25:53 puter kernel: [   67.230556] vboxdrv: fAsync=1 offMin=0xa89b offMax=0xa89b
Sep 16 18:25:53 puter kernel: [   67.230560] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Sep 16 18:25:54 puter kernel: [   67.348293] tun: Universal TUN/TAP device driver, 1.6
Sep 16 18:25:54 puter kernel: [   67.348297] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 16 18:25:54 puter kernel: [   67.380918] device vbox0 entered promiscuous mode
Sep 16 18:25:54 puter kernel: [   67.380926] audit(1221585954.183:4): dev=vbox0 prom=256 old_prom=0 auid=4294967295
Sep 16 18:25:54 puter kernel: [   67.380931] br0: port 2(vbox0) entering learning state
Sep 16 18:25:54 puter kernel: [   67.408002] device vbox1 entered promiscuous mode
Sep 16 18:25:54 puter kernel: [   67.408012] audit(1221585954.255:5): dev=vbox1 prom=256 old_prom=0 auid=4294967295
Sep 16 18:25:54 puter kernel: [   67.408018] br0: port 3(vbox1) entering learning state
...
...
Sep 16 18:26:09 puter kernel: [   74.690983] br0: topology change detected, propagating
Sep 16 18:26:09 puter kernel: [   74.690987] br0: port 2(vbox0) entering forwarding state
Sep 16 18:26:09 puter kernel: [   74.718332] br0: topology change detected, propagating
Sep 16 18:26:09 puter kernel: [   74.718337] br0: port 3(vbox1) entering forwarding state
<<<<<<<<<<<<<<<<<<<<<<<<<

It remains perfectly possible to access the NAS via the url smb://slug/imk, presenting my credentials. I just can't cifs mount it anymore.

---

