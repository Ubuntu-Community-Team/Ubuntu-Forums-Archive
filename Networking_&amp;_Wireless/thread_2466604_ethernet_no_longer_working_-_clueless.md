---
title: "ethernet no longer working - clueless"
date: 2021-08-31
forum: Networking &amp; Wireless
---

### Post by jgw on 2021-08-31
My ethernet connection no longer works.  Currently using wifi for the internet.  I have been reading stuff for a couple of hours now.  This just seems to happen. I was thinking that I may have changed something in the bios but maybe not.  I searched that and didn't find anything that might cause this.  I gave up but found that folks seem to have solved it and it has something to do with the driver for Realtek Semiconductor Co   Then I read that there is a problem with that?  Anyway, here is some stuff about my machine.  Would appreciate any thoughts on this one.

```


greg@gregdown:~$ sudo lshw -C network
[sudo] password for greg: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 15
       serial: 18:31:bf:0d:b4:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-31-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 ioport:e800(size=256) memory:febff000-febfffff memory:febf8000-febfbfff
greg@gregdown:~$ 

greg@gregdown:~$ ip -h address 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 18:31:bf:0d:b4:c1 brd ff:ff:ff:ff:ff:ff
3: wlx30469a0097f2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 30:46:9a:00:97:f2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx30469a0097f2
       valid_lft 3393sec preferred_lft 3393sec
    inet6 fe80::8066:a360:2bb5:2568/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: wgpia0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none 
    inet 10.29.197.94/32 scope global wgpia0
       valid_lft forever preferred_lft forever
greg@gregdown:~$ 


 Network Interfaces
lo	1.51MiB	1.51MiB	127.0.0.1
enp5s0	0.51MiB	0.00MiB	
```

---

### Post by linerman on 2021-09-01
1. Have you got Windows next to Ubuntu?

---

### Post by jgw on 2021-09-01
thanks for the reply - nope just Ubuntu 21.04

---

### Post by ajgreeny on 2021-09-01
Did this ethernet connection work well in the past and has it just stopped recently?

What changes do you suspect you have made in your BIOS that may have caused this problem, or is that just a complete guess?

Just to make a check please boot to a live version of 21.04 to see if you get a connection using that.  I have the same ethernet card in my laptop and although I usually work with wireless the ethernet connection works, or did when I first used this machine.

---

### Post by linerman on 2021-09-02
I would check Wake On Lan feature in Bios. Have you changed anything there?

The main problem with that NIC is that WOL function is not properly working with Linux systems.
As a first step I would check if you can get a connection using Ubuntu LiveCd.
If yes then do not reboot the system, but do a shutdown. It is very important.

We need to find a way to establish a connection with that ethernet card.

---

### Post by jgw on 2021-09-02
thanks for the responses!

I put 21.04 over 20.04 and suspect that screwed things up.  I am going re-install 20.04.3 and see if that is the problem as I have read that might be a problem.  I shojuldn't have gone to 21.04 but I didn't pay attention and 21.04 not a long term thing so reinstalling hurts nothing.  I will put the results here when I finish.

---

### Post by jgw on 2021-09-02
Yep, that was the problem.  There is a problem with the ethernet connect when moving to 21.04

I will mark this one as solved!

---

