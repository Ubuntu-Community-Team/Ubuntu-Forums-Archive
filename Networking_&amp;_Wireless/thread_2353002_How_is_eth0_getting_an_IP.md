---
title: "How is eth0 getting an IP?"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by astrae on 2017-02-17
Hi guys,


I'm currently playing with 16.04LTS server and have run into a small issue.

I've created a few VM's in Hyper V with no issue, all local virtual disks.

When editing /etc/network/interfaces  eth0 has always shown  'dhcp'

```
iface eth0 inet dhcp
```

I can change this to 'static' and setup a static IP easily.

In my latest VM, I have mounted an iSCSI drive as a secondary drive and its mounting at boot.  I did this through the installer at the partitioning screen.

On this VM when editing the interfaces file, dhcp isn't there, its showing manual.

If I change to static the machine gets two IP's, there is an error when booting up about bringing up network interfaces.  When doing an ifconfig, it shows the dhcp address.

How is eth0 getting this dhcp address?  

How do I find and stop this so I can create a static as normal?

Here is my network interface file. Thanks for any help you can provide.

```

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet manual



```

---

### Post by TheFu on 2017-02-18
With 16.04, network device names are following a new model which provides unique device names (large enterprises and systems with lots of network cards needed this).  Take a look at **ifconfig** output to see all the known ethernet devices.

For example, enx0023663c2337 is what the device name on my current box looks like (I modified it to protect the guilty). I think it is based off the MAC. If you attempt to configure the wrong device (or a non-existent one), it is unlikely anything you intend will happen.

**sudo lshw -C network** will also show the network devices and driver loaded, if any.

I don't know anything about what hyper-v may or may not do, so interactions with that might be doing different things. I dunno.  Been a KVM guy for years after switching from Xen and ESX. Never regretted the KVM upgrade. Not once.

---

### Post by astrae on 2017-02-18
I think I have found it.

Its due to iSCSI.

The script in /usr/share/initramfs-tools/scripts/local-top/iscsi

It is setting up networking and gets a dhcp address.

I set a static IP in a new installation and the system works fine with two IP's.

I disabled DHCP on the server and iSCSI fails to connect.

---

### Post by TheFu on 2017-02-19
I find systemd dependencies obtuse compared to the older methods. 
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1569925](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1569925) and 
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1444555](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1444555) are iSCSI dependency related bugs. 1st seems to be open still. 2nd was closed.

---

