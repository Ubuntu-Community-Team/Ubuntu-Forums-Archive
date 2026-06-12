---
title: "Atmel at76c506 can see networks, dhcp times out"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by brandon_r87 on 2007-02-19
Hi,

I'm using Xubuntu on a Compaq TC1000 and have almost everything I want working except the wireless.  It has an Atmel at76c506 and I have installed the atmel_firmware package.  I *was* able to see different wireless networks using wifi-radar, but I've messed up wifi-radar.  Even though it can see the networks though, DHCP always times out and I get no IP.  What I find weird is that iwconfig sees the card as eth1, but dmesg shows it at eth0 and my wired connection (e100) as eth1.  I'm just confused and almost ready to just upgrade the card and hope it works...

```
lspci
00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)
```

```
iwconfig
eth1      IEEE 802.11-DS  ESSID:"FAMICOM"  
          Mode:Managed  Frequency:2.422 GHz  Access Point:  00:15:E9:1A:84:30  
          Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:328  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
dmesg | grep eth0
[17179606.640000] eth0: Atmel at76c50x. Version 0.98. MAC 00:08:02:d2:dd:26
[17180007.844000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180053.852000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17180053.856000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180064.076000] eth0: no IPv6 routers present
[17180802.840000] device eth0 entered promiscuous mode
[17180802.840000] audit(1171909380.853:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[17180819.044000] device eth0 left promiscuous mode
[17180819.044000] audit(1171909397.058:5): dev=eth0 prom=0 old_prom=256 auid=4294967295

```

```
dmesg | grep eth1
[17179607.244000] e100: eth1: e100_probe: addr 0xe8020000, irq 9, MAC addr 00:08:02:92:FC:25
[17180007.844000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180802.904000] device eth1 entered promiscuous mode
[17180802.904000] audit(1171909380.917:3): dev=eth1 prom=256 old_prom=0 auid=4294967295
[17180819.060000] device eth1 left promiscuous mode
[17180819.060000] audit(1171909397.074:6): dev=eth1 prom=0 old_prom=256 auid=4294967295
[17180819.668000] device eth1 entered promiscuous mode
[17180819.668000] audit(1171909397.682:8): dev=eth1 prom=256 old_prom=0 auid=4294967295
[17180824.616000] device eth1 left promiscuous mode
[17180824.616000] audit(1171909402.630:9): dev=eth1 prom=0 old_prom=256 auid=4294967295

```

Brandon

---

### Post by greshamp on 2007-03-10
Hey Brandon,
Its been a few weeks since your post, but just in case anyone else is looking for the info, here's how I solved the problem on my box.

Also with a TC1000. Now I'm not familiar with Ubuntu, but this worked for me ... however my devices are appearing slightly different to yours:-
```

:~$ sudo lspci | grep Atmel
00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)

:~$ sudo dmesg | grep eth1
[17179604.472000] eth1: Atmel at76c50x. Version 0.98. MAC 00:08:02:d2:3e:b5
[17179628.144000] eth1: no IPv6 routers present


```

So I'm working with my wireless card on eth1, however we have exactly the same versions. 

The fact that your cards are going into promiscuous mode is spooky. You need to check that out.

Next you need to load the atmel_cs driver. I did this by creating a modules.conf

```

:~$ sudo cat /etc/modules.conf 
alias eth1 atmel_cs

```

Then ensure the module is loaded at boot time by adding it to my modules file

```

:~$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
atmel_cs

```

Load the driver manually this time:

```

:~$ sudo modprobe -v atmel_cs

```

Now the fun part is this. The driver atmel_cs was written by Simon Kelley ([www.thekelleys.co.uk](www.thekelleys.co.uk)) and you installed that when you installed the atmel_firmware package. You also installed some firmware libraries into /lib/firmware as well as a utility called atmel_fwl. The firmware bin needs to get onto your device. This is usually done by a subsystem called hotplug and is automatic provided hotplug is compiled into the kernel. Unfortunately out of the box ubuntu doesnt have this. This is where the atmel_fwl utility comes in. Use it to load up the correct bin just before initialising the device. The easy way to do this is add a script as follows:

```

:~$ cat /etc/network/if-pre-up.d/atmel-firmware 
#!/bin/sh
/usr/sbin/atmel_fwl eth1 /lib/firmware/atmel_at76c506.bin
echo *Atmel firmware loaded*

```

Double check the above file has the correct execute permissions and also that after all the messing around you do have the correct essid and key in your /etc/network/interfaces file.

You may need to reboot and completely power off, but I think I had to do this as I loaded the incorrect bin the first time around

Best of luck
Paul

---

