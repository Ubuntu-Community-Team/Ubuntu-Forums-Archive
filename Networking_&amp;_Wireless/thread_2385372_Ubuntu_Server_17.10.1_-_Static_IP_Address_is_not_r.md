---
title: "Ubuntu Server 17.10.1 - Static IP Address is not read from /etc/network/interfaces"
date: 2018-02-19
forum: Networking &amp; Wireless
---

### Post by ppoteete on 2018-02-19
Hello.

Thank you for your help!

When converting the interface to eth0, and using /etc/network/interfaces, the static IP information is not used when activating the interface. It is possible to perform a dhclient eth0; however, it does not respect the /etc/network/interfaces options.

**Process:**
[INDENT]Boot Ubuntu Server
Change GRUB to use "eth0"
Reboot
Configure /etc/network/interfaces
Reboot
No IP Address Assigned[/INDENT]

**Changes:**
/etc/default/grub:
sed s/GRUB_CMDLINE_LINUX=\"\"/GRUB_CMDLINE_LINUX=\"net.ifnames=0\ biosdevname=0\"/g

**/etc/network/interfaces:**
auto eth0
iface eth0 inet static
address 192.168.0.201
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 10.10.10.1 8.8.8.8

**student@ubuntu:~$ lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

**student@ubuntu:~$ dpkg -l | grep nplan**
ii  nplan                                      0.32~17.10.1                                 amd64        YAML network configuration abstraction for various backends

---

### Post by chili555 on 2018-02-19
Please see: [https://askubuntu.com/questions/994015/ubuntu-server-17-10-wont-autoconfigure-ethernet-on-boot/994028#994028](https://askubuntu.com/questions/994015/ubuntu-server-17-10-wont-autoconfigure-ethernet-on-boot/994028#994028)

What is magic about eth0 instead of the predictable naming convention enp3s0 or whatever it started as? [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

---

### Post by ppoteete on 2018-02-20
The link provides guidance on yaml and netplan. This system is avoiding netplan (nplan).  I have removed nplan from the other nodes.

I can manually bring up the interface; however, I would appreciate the automatic static definition that we enjoy in 100% of our pre-nplan systems as eth0.


To answer the unrelated statement: The magic of eth0 may be overstated in many areas. The consistency for over 20 years of networking may be the best reason. Other reasons could include the simplicity and clarity of the interface as eth0, eth1, eth2, wlan0, in labs of 20-100 systems, et cetera. In stating this, I realize that I am responding to a common fallacy in which an fellow enthusiast asks, "why" to a question that asked, "how."

Kindest Regards,
Paul

---

### Post by chili555 on 2018-02-20
> I would appreciate the automatic static definition that we enjoy in 100% of our pre-nplan systems as eth0.

I am still confused. Are you, in effect, asking how you can remove netplan altogether and go back in time to  /etc/network/interfaces? 

It is perfectly simple to configure netplan and get the requested static IP on each and every boot without any human intervention. Did you try?

---

### Post by ppoteete on 2018-02-20
Hello.

Yes. nplan works fine with the varied names of our classroom interfaces.  We have dissimilar hardware resulting in unpredictable names. (ironic that predictable naming is myopic).

To simplify this request:
How do we change the enpxxx interface names to eth0 for each system in a cluster for Ubuntu Server 17.10.1? It is fine if this is still using netplan.  I can configure the yaml without issue.

**The common grub conf changes are ignored by nplan yaml:**
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"

**Linking to /dev/null is also fruitless:**
ln -s /dev/null /etc/systemd/network/99-default.link

[https://www.freedesktop.org/software/systemd/man/systemd.link.html](https://www.freedesktop.org/software/systemd/man/systemd.link.html)

Thank you so much.

---

### Post by ppoteete on 2018-02-20
root@ubuntu:~# journalctl -b | grep -A3 rename
Feb 20 15:09:58 ubuntu kernel: e1000 0000:00:03.0 enp0s3: renamed from eth0
Feb 20 15:09:58 ubuntu kernel: usb 2-1: New USB device found, idVendor=80ee, idProduct=0021
Feb 20 15:09:58 ubuntu kernel: usb 2-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
Feb 20 15:09:58 ubuntu kernel: usb 2-1: Product: USB Tablet

root@ubuntu:~# udevadm info -e | grep enp -C3
E: SUBSYSTEM=pci
E: USEC_INITIALIZED=7280357

P: /devices/pci0000:00/0000:00:03.0/net/enp0s3
E: DEVPATH=/devices/pci0000:00/0000:00:03.0/net/enp0s3
E: ID_BUS=pci
E: ID_MODEL_FROM_DATABASE=82540EM Gigabit Ethernet Controller (PRO/1000 MT Desktop Adapter)
E: ID_MODEL_ID=0x100e
E: ID_NET_DRIVER=e1000
E: ID_NET_NAME_MAC=enx0800275176c7
E: ID_NET_NAME_PATH=enp0s3
E: ID_OUI_FROM_DATABASE=PCS Systemtechnik GmbH
E: ID_PATH=pci-0000:00:03.0
E: ID_PATH_TAG=pci-0000_00_03_0
--
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_VENDOR_ID=0x8086
E: IFINDEX=2
E: INTERFACE=enp0s3
E: SUBSYSTEM=net
E: SYSTEMD_ALIAS=/sys/subsystem/net/devices/enp0s3
E: TAGS=:systemd:
E: USEC_INITIALIZED=1768311

---

### Post by ppoteete on 2018-02-20
It appears that Ubuntu has changed the locations and functions of several subsystems resulting in this type of issue. I can adapt to the changes; however, I will need to know how to manually manipulate the system for our unique needs and purposes.

---

### Post by chili555 on 2018-02-20
From the link I gave:> I don't like this, how do I disable this?
You basically have three options:

1. You disable the assignment of fixed names, so that the unpredictable kernel names are used again. For this, simply mask udev's .link file for the default policy: ln -s /dev/null /etc/systemd/network/99-default.link
2. You create your own manual naming scheme, for example by naming your interfaces "internet0", "dmz0" or "lan0". For that create your own .link files in /etc/systemd/network/, that choose an explicit name or a better naming scheme for one, some, or all of your interfaces. See systemd.link(5) for more information.
3. You pass the net.ifnames=0 on the kernel command lineIs there any improvement if you change to:```
GRUB_CMDLINE_LINUX="net.ifnames=0"
```In other words, omit the biosdevname=0 part.

---

### Post by ppoteete on 2018-02-28
That worked great!

Kindest Regards!

---

