---
title: "Problems with (lxc) bridge"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by jackyDon on 2013-12-11
Hi,
I'm running ubuntu server (12.04) on a machine, and I'm having a lot of problems, ever since I've set up a bridge and a lxc.

This is my interfaces file:
```
auto eth0iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        gateway 192.168.1.1
        up ethtool -s eth0 wol g


auto lxcbr0
iface lxcbr0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 0
        bridge_maxwait 0
        bridge_stp off
```

I also selected this bridge in the lxc-config-file for my container (veth)

Everything works fine with this configuration, but as soon as I restart the machine, the boot process hangs:
"Waiting for network configuration"
"Waiting up to 60 more seconds for network configuration"
this times out at some point, and the machine eventually boots up. but then the network doesn't work.

"networking restart" doesn't work either, because apparently the lxcbr0 bridge is still up
So I have to do a:
```
> [FONT=Calibri]ip link set br0down
[/FONT][FONT=Calibri]> brctl delbr br0[/FONT]
```
to delete the bridge
then I can restart the network

after that everything works fine again. until the next reboot.

any ideas what the problem might be?

---

### Post by trobro on 2013-12-11
Perhaps you shouldn't specify any gateway:

[http://askubuntu.com/questions/293827/error-rtnetlink-answers-file-exists](http://askubuntu.com/questions/293827/error-rtnetlink-answers-file-exists)

---

