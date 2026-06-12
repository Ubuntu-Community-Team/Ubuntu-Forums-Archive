---
title: "ethernet names not consistent ubuntu server 14.04"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by Wayne_Shumaker on 2014-04-26
I installed ubuntu server 14.04 that has 3 ethernet nics.
The names are not consistent between boots:

Sometimes I get this:
# lshw -businfo -C network
Bus info          Device      Class          Description
========================================================
pci@0000:02:00.0  rename4     network        82574L Gigabit Network Connection
pci@0000:05:00.0  p2p1        network        I210 Gigabit Network Connection
pci@0000:06:00.0  p3p1        network        I210 Gigabit Network Connection

or this:
~# lshw -businfo -C network
Bus info          Device      Class          Description
========================================================
pci@0000:02:00.0  p2p1       network        82574L Gigabit Network Connection
pci@0000:05:00.0  p2p2        network        I210 Gigabit Network Connection
pci@0000:06:00.0  p3p1        network        I210 Gigabit Network Connection

#biosdevname -i rename4
p2p1
# biosdevname -i p2p1
p2p2

It seems to get in some circular naming, so they are never consistent.

Changing kernel command line in /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
Will get the names back to eth0, eth1, eth2,
however I'm not sure they will be consistent either.

How can I return to names defined by mac address?

Wayne

---

### Post by Wayne_Shumaker on 2014-04-26
I had a typo in my original 70-persistent-net.rules.
adding proper rule fixed problem

---

### Post by Wayne_Shumaker on 2014-04-29
If anyone crosses this thread, I still get random ethernet assignments with udev net naming, with sometimes rename4 and sometimes names get shifted. So much for the persistent naming feature of udev!

The fix is to create your own /etc/udev/rules.d/70-persistent-net.rules and add something like the following, based on mac address, which tend to be persistent. Sometimes this file gets generated, but bugs remain so don't count on it getting it auto generated, especially if biosdevname -i <nic anme> does not give consistent results.

SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="d8:50:e6:c2:22:d8", NAME="lan0"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="d8:50:e6:c2:22:d9", NAME="lan1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="68:05:ca:19:11:ac", NAME="wan0"

Otherwise I believe ubuntu server 14.04 udev ethernet naming is broken. After a fresh install, my network would not come up because the names were shifted from the install net names. Normally 70-persistent-net.rules is auto-generated, but that is not always the case, hence creating your own based on mac address is the safest solution if you really want "persistent" net names.

Wayne

---

### Post by Doug S on 2014-04-30
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2219332").

Things have changed, and no 70-persistent-net.rules is not auto-generated anymore.

---

### Post by Wayne_Shumaker on 2014-05-01
I realize that 70-persistent-net.rules is not auto-generated.
My issue seems to be with biosdevname getting confused.
It also seems to hang the boot for some time at:

Begin: Running /scripts/init-bottom/

Which is hardware related. Changing the grub default as in my first post,
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
and creating 70-persistent-rules based on mac address
both fixes the slow boot and gets the names consistent.

---

### Post by MACscr on 2014-07-14
grr. Super frustrating, even with adding the default grub lines, I am still getting inconsistent results with my 70-persistent-net.rules. Sometimes the names are fine, sometimes i have a 5 interface show up in "ip link show" output that is for eth0 or whatever when based on my udev rules, it should exist. Let alone a duplicate.

Wayne,
Are things still working fine for you?

---

### Post by chili555 on 2014-07-14
My understanding is that with no GRUB lines, the package *biosdevname* installed, and an edited  70-persistent-net.rules, that the interface names will bind to the MAC address and therefor persist, assuming your BIOS supports it. Please see: [http://linux.dell.com/files/whitepapers/consistent_network_device_naming_in_linux.pdf](http://linux.dell.com/files/whitepapers/consistent_network_device_naming_in_linux.pdf) Especially see page 8.

---

### Post by MACscr on 2014-07-14
Right, but if you are trying to rename your interface for a more uniformed usage, it than the udev rules would be used. Unfortunately those renames are not consistent.

---

### Post by chili555 on 2014-07-14
> if you are trying to rename your interface for a more uniformed usage, With *biosdevname* installed, they get named something like p1p3, that is the first PCI card and the third port, as an example. Is that not uniform enough? What are you looking for?

---

