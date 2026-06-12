---
title: "[SOLVED] Server with crude desktop - How to enable wireless?"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by sipickles on 2008-10-10
Hi,

I've a dev server running Ubuntu Intrepid Server Beta.

I've installed gnome-core and gdm to give me a lightweight desktop to use.

I've installed wicd for network access, since network-manager is still immature imho.

wicd connects with wired connection. However it says, no wireless networks found.

I know this is wrong since I have just reinstalled after loading Inptrepid server, then Ubuntu-desktop. This gave me so much junk I started again, but the wireless DID work with wicd.

So what packages am I missing for the server to see my wireless card?

Many thanks

Si

---

### Post by cariboo on 2008-10-10
What is the output of:

```
sudo iwconfig
```

and 

```
sudo lshw -C network
```

Post the output of the above commands in your next post. Also make sure the network manager is completely removed.
A server should have a static IP address so you really don't even need wicd. 

Remember too that Intrepid is still in beta so you have expect the things will be broken.

JIm

---

### Post by sipickles on 2008-10-11
Hi Jim,

Here is the output:

```
simon@server:~$ sudo iwconfig
[sudo] password for simon: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

simon@server:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:c0:49:63:58:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.199 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:86:82:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
simon@server:~$
``` 


I've installed the b43-fwcutter which I know it needed last time it worked.

---

### Post by sipickles on 2008-10-11
So it suddenly works today.... thought it was only windows which needed constant reboots? ;)

Thanks anyway

---

### Post by superprash2003 on 2008-10-11
please mark thread as SOLVED.. you can find it under "Thread Tools"

---

