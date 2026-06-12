---
title: "Card recognized, Ethernet not working [14e4:165b]"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by only.tiki on 2014-03-31
Hello. I did a fresh install of Xubuntu from a minicd. The wired connection worked fine during installation (I only had a minor problem with DNS). However, once in the graphic environment, the wired connection doesn't show up at all - the "Wired connection" text is grayed out when I click on the network icon.

Really strange since it worked fine during installation.. however, I think the system correctly recognizes the card but somehow doesn't "manages" it. I also tried to set "managed=true" in /etc/NetworkManager/NetworkManager.conf. 

Another strange thing is that the connection is recognized as "em1", not as "eth0". Any idea?

Useful commands:

ifconfig (don't mind the wlan0, it's only a usb wireless adapter I am using to connect)
```
em1       Link encap:Ethernet  IndirizzoHW 28:92:4a:2d:56:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:3280 (3.2 KB)  Byte TX:3280 (3.2 KB)

wlan0     Link encap:Ethernet  IndirizzoHW 00:1e:2a:b3:98:29  
          indirizzo inet:192.168.1.119  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21e:2aff:feb3:9829/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3302 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:2783468 (2.7 MB)  Byte TX:538266 (538.2 KB)


```

lshw -c Network
```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: em1
       version: 10
       serial: 28:92:4a:2d:56:6f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=5723-v3.35 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fe9f0000-fe9fffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1e:2a:b3:98:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.8.0-35-generic firmware=N/A ip=192.168.1.119 link=yes multicast=yes wireless=IEEE 802.11bg
```

cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
    address 192.168.1.185
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 8.8.8.8

```

lspci -nn | grep Ethernet
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)

```

cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=28:92:4A:2D:56:6F,

[ifupdown]
managed=true

```

Thank you in advance.

---

### Post by chili555 on 2014-03-31
I suggest you streamline your i*nterfaces* file; in this case, less is more:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
    address 192.168.1.185
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 192.168.1.1
```After you proofread, save and close the text editor, detach the USB wireless and reboot so we have a clean slate. Then run:```
dmesg | grep -e tg3 -e eth0 > ether.txt
cat /var/log/syslog | grep -e eth0 -e etwork | tail -n25 >> ether.txt
ifconfig >> ether.txt
```Hook up the USB wireless and connect. Find the file ether.txt in your user directory and paste it here; give me the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Thanks.

---

### Post by only.tiki on 2014-04-01
I removed the Wireless adapter. restarted and then ran the commands.

Here's the result:
[http://paste.ubuntu.com/7188798/](http://paste.ubuntu.com/7188798/)

Thank you for your time chili555.

---

### Post by chili555 on 2014-04-01
I wonder if this is a managed=true or false problem. What is the result of:```
nm-tool
sudo ifdown em1 && sudo ifup -v em1
```Thanks.

---

### Post by only.tiki on 2014-04-03
Same procedure as last time - no wireless adapter and restarted:

[http://paste.ubuntu.com/7197485/](http://paste.ubuntu.com/7197485/)

Still no result, the ethernet port isn't even blinking.

Thank you for your time chili, and sorry for my late response but we are on two different time zones. :P

---

### Post by chili555 on 2014-04-03
I'm more confused than ever. Your earlier paste refers to the tg3 interface as eth0:>  
[    3.235184] tg3.c:v3.128 (December 03, 2012)
[    3.307031] [COLOR="#FF0000"]tg3[/COLOR] 0000:02:00.0 [COLOR="#FF0000"]eth0[/COLOR]: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 28:92:4a:2d:56:6f
[    3.307037] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    3.307041] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.307043] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.109605] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not readyBut in interfaces, it is referred to as em1. I wonder where em1 comes from. Please comment out all of the em1 settings like this:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto em1
#iface em1 inet static
#    address 192.168.1.185
#    netmask 255.255.255.0
#    gateway 192.168.1.1
#    dns-nameservers 8.8.8.8 192.168.1.1
```Reboot and then post:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Weird!

---

