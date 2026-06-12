---
title: "Wifi not working (Ubuntu Desktop 14.04.3)"
date: 2015-12-30
forum: Networking &amp; Wireless
---

### Post by sim085 on 2015-12-30
Hello,

I have installed Ubuntu Desktop 14.04.3 on an HP Laptop Compaq 6710b. The first thing I noticed is that the WiFi button on the laptop does nothing (on Windows7 the WiFi button turns the WiFi on/off and a blue LED shows if WiFi is on or off, I confirmed this by installing Windows7 on the same machine). I had a look on the forum to see if I can find a solution but so far I failed.  

If from terminal I type "rfkill list all" I get nothing. 
If from terminal I type "ifconfig" I get the following:

```

eth0      Link encap:Ethernet  HWaddr 00:1f:29:81:ca:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12513 (12.5 KB)  TX bytes:12513 (12.5 KB)

```

If from terminal I type "iwconfig" I get the following:

```

eth0      no wireless extensions.

lo        no wireless extensions.

```

If from terminal I type "lshw -C network" (after a couple of seconds) I get the following:

```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:e4100000-e4103fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:81:ca:7d
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:e4000000-e400ffff

```

Most threads over here point to rfkill unblock all. However rfkill commands gives me nothing. 

I do not know what the problem might be. Can anyone help?

Wired connection works fine (although takes some time to establish) and needless to say there is a Wirelss network as I am posting this from another laptop connected to the Wireless network.

Ok, I seem to be getting somewhere...

I had followed this video before but I was not getting anything under "Additional Drivers" (even with ethernet connection). I then did an apt-get update and apt-get upgrade, restart, and I got the propriety driver listed. I now have (after another restart after installing the driver) "Wi-Fi disabled by hardware switch" (no the button on laptop still does not work).

I have seen some posts here about it so going to try and follow those.

The video is this one...
[https://www.youtube.com/watch?v=4VVosf9p5GM](https://www.youtube.com/watch?v=4VVosf9p5GM)

---

### Post by sim085 on 2015-12-30
rfkill list all now gives me;

```

1: brcmwl-0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes

```

From what I read hard blocked means blocked from the hardware. Gone to BIOS; reset to default and now Wi-Fi works.

---

### Post by sim085 on 2015-12-30
Does anyone know how I can install propriety drivers on Ubuntu server? i.e. - without gui from command prompt?

---

