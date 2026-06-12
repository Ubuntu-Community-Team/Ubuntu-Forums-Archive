---
title: "Help with setting up bridged host interface network for VirtualBox"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-10-01
I am having problems with setting up HIN for VirtualBox.
My needs are:

[LIST]
[*]need 2 separate settings (I use eth0 at work, and ath0 at home)
[*]at home, ath0 must be assigned as 192.168.0.168
[*]would like to assign br0 to be bridged with eth0
[*]would like to assign br1 to be bridged with ath0
[*]would like to assign br1 to be 192.168.0.91
[/LIST]

Here is the /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

auto eth0
iface eth0 inet dhcp

auto tap0
iface tap0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user tak

auto tap1
iface tap1 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user tak

auto br0
iface br0 inet dhcp
    bridge_ports eth0 tap0
#    address 192.168.0.90

auto br1
iface br1 inet static
    bridge_ports ath0 tap1
    address 192.168.0.91
    netmask 255.255.255.0

```

This setting seems to disable my wireless connection; it still think it's connected but no actual connection through ath0, ie can't browse the web, etc.

If I change the setting for **br1** to **dhcp**, then the IP address 192.168.0.168 gets assigned to br1 and ath0 gets none; no usable connection.

I'm sure that I'm doing something silly here. Please somebody point me in the right direction. Thank you!

Edit:
This is a portion of the output from "sudo /etc/init.d/networking restart" that I thought might be relevant...

```
No working leases in persistent database - sleeping.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Set 'tap0' persistent and owned by uid 1000
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Set 'tap1' persistent and owned by uid 1000
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```

---

### Post by komofei on 2008-07-20
Hello,

I have same problem to share wireless ath0 connection in bridge. In addition, I need to get my IP address for ath0 interface from DHCP.

Could anybody help us? Many thanks...

---

