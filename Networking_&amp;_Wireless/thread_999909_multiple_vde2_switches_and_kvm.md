---
title: "multiple vde2 switches and kvm"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by chrroessner on 2008-12-02
Hi,

I have installed intrepid here. I installed kvm from here:

deb [http://ppa.launchpad.net/intuitivenipple/ubuntu](http://ppa.launchpad.net/intuitivenipple/ubuntu) intrepid main

to have version 74 with vde support. So far so good.

I set up two switches:

```

# KVM/QEMU Virtual Machine Network
iface test0 inet static
  address 10.254.1.254
  netmask 255.255.255.0
  pre-up /usr/bin/vde_switch -tap ${IFACE} -daemon -group vde2-net -sock /var/run/${IFACE}.ctl \
   -mod 775 -mgmtmode 770 -mgmt /var/run/${IFACE}-manage -pidfile /var/run/${IFACE}_vde.pid
  up /usr/sbin/dnsmasq --interface=${IFACE}  --except-interface=lo --bind-interfaces --user=nobody \
   --dhcp-range=kvm,10.254.1.1,10.254.1.253,255.255.255.0,10.254.1.255,8h \
   --domain=lan --pid-file=/var/run/${IFACE}_dnsmasq.pid --conf-file
  up echo "`route -n | sed -n 's/^0\.0\.0\.0 .* \(.*\)$/\1/p'`" > /var/run/${IFACE}_route
  up iptables -t nat -A POSTROUTING -o `cat /var/run/${IFACE}_route` -j MASQUERADE
  down iptables -t nat -D POSTROUTING -o `cat /var/run/${IFACE}_route` -j MASQUERADE
  down kill -s TERM `cat /var/run/${IFACE}_dnsmasq.pid` && rm -f /var/run/${IFACE}_dnsmasq.pid
  post-down kill -s HUP `cat /var/run/${IFACE}_vde.pid`
  post-down rm -f /var/run/${IFACE}_route

# KVM/QEMU Virtual Machine Network
iface test1 inet static
  address 10.253.1.254
  netmask 255.255.255.0
  pre-up /usr/bin/vde_switch -tap ${IFACE} -daemon -group vde2-net -sock /var/run/${IFACE}.ctl \
   -mod 775 -mgmtmode 770 -mgmt /var/run/${IFACE}-manage -pidfile /var/run/${IFACE}_vde.pid
  post-down kill -s HUP `cat /var/run/${IFACE}_vde.pid`

```

Here is a kvm guest-sample script:

```

#!/bin/bash

kvm -m 512 -smp 4 \
  -name guest01 \
  -monitor pty \
  -boot c \
  -drive file=/dev/mapper/vg01-guest01--disk,if=virtio,boot=on \
  -net nic,vlan=0,macaddr=00:16:36:58:f5:65,model=virtio \
  -net vde,vlan=0,sock=/var/run/test0.ctl \
  -net nic,vlan=1,macaddr=00:16:36:58:f5:66,model=virtio \
  -net vde,vlan=1,sock=/var/run/test1.ctl \
  -serial pty \
  -parallel none \
  -k de \
  -vnc 127.0.0.1:0 \
  -daemonize

exit 0

```

And this does not work. By adding a second nic+vde pair, the network stops working. I can see both nics in the guest, but it seems not to be connected to the two switches.

If I remove the secondpair

```

  -net nic,vlan=1,macaddr=00:16:36:58:f5:66,model=virtio \
  -net vde,vlan=1,sock=/var/run/test1.ctl \

```

networking is doing fine again with of course only one nic.

So I think, I did not understand something and ask you geeks, if you do have an idea on that :-) PLEASE

My goal is to have an int0 and ext0 switch for internal traffic and traffic to the internet (so test0/1 are first steps).

I really say thanks for any help on this!

Regards
Christian

[Update, Fixed:]
So many things have been changed since yesterday, so I do not want to present the current result here. If you are interested, see my Blog under [www.roessner-net.com](www.roessner-net.com)

---

