---
title: "Problem with my network driver..."
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by docquier-samuel on 2014-02-15
Hello everyone,

I am relatively new with Ubuntu 12.04. Yesterday I tried to get a newer driver for my network card. Now, one time out of 10 it works. It normally tries to find a wifi connection even though I don't have a wireless card! The driver I installed is for a Realtek R8168... I read afterward that this chip is not friendly for Ubuntu but before I upgrade it it was working fine.

Is there a way to go back to my previous driver? I have some ideas how to proceed but I don't really want to make the matter worse...

Thanks a bunch!

Update: I can finally log on my ubuntu partition. Here's the result of lshw -class network:

 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:32:b9:85
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=full ip=192.168.0.107 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:53 ioport:ae00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff memory:fbc00000-fbc1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 06
       serial: 1c:6f:65:32:cc:a5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 ioport:8e00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fba00000-fba1ffff

And here's what I have with lspci:

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


I don't get why it works sometimes and sometimes it don't...

---

### Post by chili555 on 2014-02-15
My, oh my!!

Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
lsmod | grep r81
```Thanks.

---

### Post by docquier-samuel on 2014-02-15
Here's for the first command: 

03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)



Here's for the second: 
r8168                 261756  0 

By the way, I am amazed how fast this forum moves!

---

### Post by chili555 on 2014-02-15
Are there any clues in the logs?```
cat /var/log/syslog | grep -e r816 -e etwork | tail -n 20
```

---

### Post by docquier-samuel on 2014-02-15
Nothing in syslog...

---

### Post by chili555 on 2014-02-15
> **docquier-samuel said:**
> Nothing in syslog...I hate when that happens! From time to time, the log fills up, is archived and a new page started. We were unlucky enough to look at the log a few minutes after it restarted and so no new details were recorded, at least about your ethernet. Let's check the archived log:```
cat /var/log/syslog**.1** | grep -e r816 -e etwork | tail -n 20
```

---

### Post by docquier-samuel on 2014-02-15
There you go!

Feb 15 10:49:20 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 15 10:49:20 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> DNS: starting dnsmasq...
Feb 15 10:49:21 Linux NetworkManager[1059]: <error> [1392479361.565507] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Feb 15 10:49:21 Linux NetworkManager[1059]: <error> [1392479361.565523] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Feb 15 10:49:21 Linux NetworkManager[1059]: <warn> DNS: plugin dnsmasq update failed
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> Activation (eth0) successful, device activated.
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Feb 15 10:49:21 Linux NetworkManager[1059]: <warn> dnsmasq appeared on DBus: :1.22
Feb 15 10:49:21 Linux NetworkManager[1059]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 15 10:49:21 Linux kernel: [   13.183534] r8168: eth0: link up


Feb 15 10:49:22 Linux NetworkManager[1059]: <info> (eth0): carrier now ON (device state 100)
Feb 15 10:49:41 Linux NetworkManager[1059]: <info> (eth0): IP6 addrconf timed out or failed.
Feb 15 10:49:41 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 15 10:49:41 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 15 10:49:41 Linux NetworkManager[1059]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

---

### Post by chili555 on 2014-02-15
As a temporary measure, please try:```
sudo ethtool -s eth0 autoneg off speed 100
```If it helps, we can write a short file and make it persistent.


--------------

Possible reference:  [http://askubuntu.com/questions/100988/how-to-force-network-manager-to-set-auto-negotiation-to-false-off-for-a-particul](http://askubuntu.com/questions/100988/how-to-force-network-manager-to-set-auto-negotiation-to-false-off-for-a-particul)

---

### Post by docquier-samuel on 2014-02-16
I'll try and we'll see how it do.

---

### Post by docquier-samuel on 2014-02-17
It still gets hiccup but if I restart the network service it works again... Any ideas?

---

### Post by chili555 on 2014-02-18
> **docquier-samuel said:**
> It still gets hiccup but if I restart the network service it works again... Any ideas?What do you mean by hiccup? What does it do or not do as expected?

Please try:```
sudo ethtool -s eth0 autoneg off speed 100 duplex full
```

---

