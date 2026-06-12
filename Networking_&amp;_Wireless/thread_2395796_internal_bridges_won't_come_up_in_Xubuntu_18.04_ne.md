---
title: "internal bridges won't come up in Xubuntu 18.04 netplan/networkd"
date: 2018-07-07
forum: Networking &amp; Wireless
---

### Post by whistl034 on 2018-07-07
I am running Xubuntu 18.04 with the latest patches. I read about netplan and networkd, created my own netplan config file, and uninstalled network-manager (because it kept launching dhclient on my physical ethernet interface).

My netplan config file creates two bridges, br0, which is attached to my docking station's physical ethernet interface, and br1, which is intended to be internal only, and has no slave interfaces. The idea is I want the option to run VirtualBox VMs bridged to my ethernet, or on an internal network. I need to be able to communicate with all my guests from Xubuntu, and they need to be able to communicate with each other, so bridging is the only networking choice available to me.

The problem is ,y bridge br1 gets created, but never comes up.  I googled "networkd bridge", and found very little, but I did read that this exact situation was described by some ArchOS users way back in 2016. No workaround or solution was ever listed that I found. Manually turning up the bridge with ip link doesn't work either.

Any hints?

```

$ cat /etc/netplan/01-networkd-all.yaml
# /etc/netplan/01-work.yaml
network:
  version: 2
  ethernets:
    enp61s0:
      dhcp4: false
  bridges:
    br0:
      dhcp4: true
      interfaces: [enp61s0]
      parameters:
        stp: false
        forward-delay: 0
    br1:
      dhcp4: false
      interfaces: []
      addresses: [192.168.15.1/24]
      parameters:
        stp: false
        forward-delay: 0

$ ip a sh br1
5: br1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether de:ac:ac:3d:81:3a brd ff:ff:ff:ff:ff:ff

$ sudo ip link set br1 up

$ ip a sh br1
5: br1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether de:ac:ac:3d:81:3a brd ff:ff:ff:ff:ff:ff




```

---

### Post by Irihapeti on 2018-07-07
By the look of things, br1 has no interfaces assigned to it. I think you need to have at least one interface assigned before you can make it come up.

---

### Post by whistl034 on 2018-07-07
When you say "br1 has no interfaces assigned to it', if you meant there are no physical ethernet interfaces, you are absolutely correct, but you're wrong that bridges require an external interface. When lxd creates lxdbr0, lxc creates lxcbr0, or docker creates docker0, these are all internal-only bridges with no physical interfaces attached to them. To reach any external networks, they must route through the host's IP stack. I've installed bridge-utils, so when I run 'sudo brctl addbr br2', then 'sudo ip link set br2 up', that works, and I can assign an IP to it (manually) and use it, but it won't survive a reboot.

If you meant 'any interface, including virtual ones', I've tried bringing up a VirtualBox VM bridged to br1, and the bridge br1 still doesn't come up:

```

$ vboxmanage showvminfo chefclient2 | grep 'NIC 1'
NIC 1:           MAC: 080027638CE2, Attachment: Bridged Interface 'br1', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
$ brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.2ef5be64e5a8	no		enp61s0
br1		8000.deacac3d813a	no		
br2		8000.000000000000	no		
lxdbr0		8000.000000000000	no		


$ ip a sh br1
5: br1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether de:ac:ac:3d:81:3a brd ff:ff:ff:ff:ff:ff
$ ip a sh br2
13: br2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether fa:d4:83:62:a3:3f brd ff:ff:ff:ff:ff:ff
    inet6 fe80::f8d4:83ff:fe62:a33f/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by prjpet on 2018-08-06
I have the same issue. I was able to start the bridge by creating and assigning a dummy interface to it following [this Arch linux article]("https://wiki.archlinux.org/index.php/Network_bridge"). 

Unfortunately, as [netplan does not support dummy interfaces]("https://bugs.launchpad.net/netplan/+bug/1774203"), this solution can only be made permanent in a hacky way. Another user in a [thread here]("https://ubuntuforums.org/showthread.php?t=2386080") suggested that an empty list in the interfaces section would be sufficient to make the bridge working but this does not seem to be the case.

Any feedback and ideas would be welcome, we would really need a persistent solution here.

---

