---
title: "wired connection problems"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by iwbishop on 2011-08-22
hi, 
i'm just getting back to ubuntu after a 2yr long hiatus and i'm having trouble with my ethernet connection. info that might help:

- i'm running koala
- i'm connecting via ethernet directly from my modem to my laptop, with no router in between.

any help would be great!

ian

---

### Post by lmarmisa on 2011-08-22
> **iwbishop said:**
> hi, 
i'm just getting back to ubuntu after a 2yr long hiatus and i'm having trouble with my ethernet connection. info that might help:

- i'm running koala
- i'm connecting via ethernet directly from my modem to my laptop, with no router in between.

any help would be great!

ian

Hi Ian and welcome to the forums. :D

Could you post the output of these commands?:

```

sudo lshw -C network
nm-tool
ifconfig

```

Best regards,

Luis

---

### Post by iwbishop on 2011-08-22
*-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:37:e8:7f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:20 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:de:4b:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:3000(size=256) memory:b0109400-b01094ff

---

### Post by lmarmisa on 2011-08-22
The previous post shows the result of the first command. Try to use the CODE tags (icon **#**) for a correct formatting of the information.

Please, post the other outputs too.

---

### Post by iwbishop on 2011-08-22
NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unavailable
  Default:           no
  HW Address:        00:15:00:37:E8:7F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             disconnected
  Default:           no
  HW Address:        00:0A:E4:DE:4B:11

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on





eth0      Link encap:Ethernet  HWaddr 00:0a:e4:de:4b:11  
          inet6 addr: fe80::20a:e4ff:fede:4b11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:531663 (531.6 KB)  TX bytes:17568 (17.5 KB)
          Interrupt:20 Base address:0x3000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by garvinrick4 on 2011-08-22
@lmarmisa
 That driver 8139too is there not a problem at times with trying to load 2 drivers and
one had to be blacklisted. 8139cp
Reading about it the other day I believe, just a thought.

---

### Post by lmarmisa on 2011-08-23
**@iwbishop:**

Your Ethernet cable is connected and the carrier is detected. I suppose that this cable is connected to your modem. Is that supposition correct?.

Some incoming (8300 packets) and outgoing (56 packets) traffic is reported but the interface has no IPv4 address. You need an IP address for connecting to internet.

Do you know if your modem supports automatic configuration by DHCP?. Or perhaps does it require a manual configuration of the network interface parameters?.

**@garvinrick4:**

Sorry. I am not an expert at all in drives.

---

