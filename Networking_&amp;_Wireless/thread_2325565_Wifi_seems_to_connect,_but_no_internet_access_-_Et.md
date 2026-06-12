---
title: "Wifi seems to connect, but no internet access - Ethernet works fine"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by snckrs on 2016-05-23
My problem is  pretty much in  the title already. Here are some infos:

```
snckrs@sculptor:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr 40:16:7e:34:1c:84  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19768 errors:0 dropped:106 overruns:0 frame:0
          TX packets:13639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17754997 (17.7 MB)  TX bytes:1849751 (1.8 MB)
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:582793 (582.7 KB)  TX bytes:582793 (582.7 KB)

wlp3s0    Link encap:Ethernet  HWaddr 54:27:1e:7a:1c:9d  
          inet addr:192.168.178.61  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::8ac7:50ce:506d:5c4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87925 (87.9 KB)  TX bytes:114574 (114.5 KB)

snckrs@sculptor:~$ 


```

```
snckrs@sculptor:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8062ms

snckrs@sculptor:~$ ping 192.168.178.1
PING 192.168.178.1 (192.168.178.1) 56(84) bytes of data.
^C
--- 192.168.178.1 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7054ms

snckrs@sculptor:~$ 


```

```
   *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f7100000-f71fffff
           *-network
                description: Wireless interface
                product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: 54:27:1e:7a:1c:9d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8821ae driverversion=4.4.0-22-generic firmware=N/A ip=192.168.178.61 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:30 ioport:d000(size=256) memory:f7100000-f7103fff


```

---

### Post by prahladyeri on 2016-05-23
> My problem is  pretty much in  the title already. Here are some infos:

Are you sure that the wifi AP you are trying to access (via interface **wlp3s0**) is connected to internet and works properly? If yes, then it could likely be a firewall issue - post the output of **sudo iptables -L** and **sudo ip6tables -L** in that case.

---

### Post by snckrs on 2016-05-23
> **prahladyeri said:**
> Are you sure that the wifi AP you are trying to access (via interface **wlp3s0**) is connected to internet and works properly?

Since I am writing   to you over that AP (connected   by Ethernet) while my notebook is connected to it via wifi and in a chatroom, I am sure. Also my phonne is connected to it, everything works fine.

```
snckrs@sculptor:~$ sudo iptables -L
[sudo] password for snckrs: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
snckrs@sculptor:~$ 


```

```
snckrs@sculptor:~$ sudo ip6tables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
snckrs@sculptor:~$ 


```

---

### Post by snckrs on 2016-05-23
I got it fixed by installing this:
[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) 
found that workaround here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528005](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528005)

---

### Post by simonn on 2016-05-27
> **snckrs said:**
> I got it fixed by installing this:
[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) 
found that workaround here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528005](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528005)

Also see "Wifi fails after suspend/sleep."

[http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037](http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037)

---

