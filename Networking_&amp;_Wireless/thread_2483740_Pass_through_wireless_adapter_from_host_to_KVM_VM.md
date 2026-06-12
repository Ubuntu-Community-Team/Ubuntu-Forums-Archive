---
title: "Pass through wireless adapter from host to KVM VM"
date: 2023-02-07
forum: Networking &amp; Wireless
---

### Post by kingslavcho on 2023-02-07
Hello guys, I have a problem with my KVM virtual machine because it does not have internet connection and i like my connection to be made directly with the wireless adapter which will be connected directly with the wireless router. I am new into KVM and don't know much but from reading i understood that there is an option called passthrough in KVM which can help guest to directly use the wireless adapter.

The host is connected with lan cable and i do not need the wireless adapter on the host but on the guest VM.

This is the output of the host ifconfig:

enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.201  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::3e7c:3fff:fe27:6476  prefixlen 64  scopeid 0x20<link>
        ether 3c:7c:3f:27:64:76  txqueuelen 1000  (Ethernet)
        RX packets 6114698  bytes 6211114275 (6.2 GB)
        RX errors 0  dropped 11  overruns 0  frame 0
        TX packets 6022861  bytes 1304250533 (1.3 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3266146  bytes 1699931157 (1.6 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3266146  bytes 1699931157 (1.6 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

macvtap0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::5054:ff:fef7:48fe  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:f7:48:fe  txqueuelen 500  (Ethernet)
        RX packets 189  bytes 30948 (30.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2094  bytes 338491 (338.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:40:80:51  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlxd03745ed8e3c: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.247  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::325a:43fd:82d9:ec8e  prefixlen 64  scopeid 0x20<link>
        ether d0:37:45:ed:8e:3c  txqueuelen 1000  (Ethernet)
        RX packets 6448  bytes 384777 (384.7 KB)
        RX errors 0  dropped 175  overruns 0  frame 0
        TX packets 2402  bytes 436312 (436.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

Also tried to install with virt-manager but i get error: device or resource busy and the wireless adapter is not connected..

How can i make this wlxd03745ed8e3c adapter to be used directly from my KVM VM? Thank you

---

### Post by TheFu on 2023-02-07
Passthru requires that the device be exclusive to the single VM.

If it is a USB device, it is relatively easy.  If it is a PCIe card, then you'll need to figure out how to pass-through that PCIe slot, card, to the VM using VT-d and IOMMU.  Good luck with that.

It is much easier to setup wired NIC passthru or just setup a bridge for the VMs to use.

---

### Post by kingslavcho on 2023-02-08
It is a USB device (wireless adapter) and the host is not disconnecting it fully.. How can i do that? I don't really know how to use KVM but for my needs it is the most suitable virtualization software. Thank you

---

### Post by TheFu on 2023-02-08
> **kingslavcho said:**
> It is a USB device (wireless adapter) and the host is not disconnecting it fully.. How can i do that? I don't really know how to use KVM but for my needs it is the most suitable virtualization software. Thank you

You blacklist the driver on the KVM host.  Look in /etc/modprobe.d/ for examples.

The only reasons I know to pass a wifi adapter into a VM is for using it in penetrations or penetration testing.  OTOH, wired NIC passthru has lots of good security reasons, like running a router inside a VM.

---

