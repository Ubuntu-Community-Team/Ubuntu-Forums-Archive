---
title: "In wired connection&gt;DNS Servers only my router-address is present"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by offline on 2007-10-26
In my **Feisty,** Wired Connection--Automatic DHCP configuration is on. In the general tab, only host name is present(no domain name).

Under DNS TAB as DNS SERVERS, there is only one entry: my router address 10.0.0.2**(microcom AD2636)**

Under HOSTS tab is a list where the first entry is localhost with IP no 127.0.0.1. The second entry is computer;s name with an IP no 127.0.1.1 . 

Location drop-down list in network settings window is blank(no choice).

```
~$ lshw -C network
        WARNING: you should run this program as super-user.
          *-network               
               description: Ethernet interface
               product: RTL-8139/8139C/8139C+
               vendor: Realtek Semiconductor Co., Ltd.
               physical id: b
               bus info: pci@00:0b.0
               logical name: eth1
               version: 10
               serial: 00:11:6b:94:dc:bd
               width: 32 bits
               clock: 33MHz
               capabilities: bus_master cap_list ethernet physical
               configuration: broadcast=yes driver=8139too
        driverversion=0.9.28 ip=10.0.0.7 latency=32 maxlatency=64
        mingnt=32 multicast=yes
               resources: ioport:dc00-dcff iomemory:df000000-df0000ff
        irq:11



```

So when I mouse-over the network icon(near the clock) or click on it there is one phrase "manual network configuration" and not any info about my internet connection or ethernet card.

I also experience this: when opening my router feisty may not recognize it and so I close and open it 2 or three times.

Some difficulties when browsing with firefox too( reloading 1-2 times to get to the page). 

As a conclusion I have internet in my linux partitition as in my windows but in ubuntu I believe something is wrong with the configuration.

---

### Post by offline on 2007-10-26
Any help or link?

---

