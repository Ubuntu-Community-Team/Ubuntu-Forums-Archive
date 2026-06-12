---
title: "Hardy no network: intel 2200bg and marvell 88E8036"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by alesp on 2008-05-13
Hello.
Ok, here is the problem: 2 days ago I installed Ubuntu 8.04 in a Toshiba Satellite A105 S2716. Everything went fine with network detection and cnofiguration, but there were some problems with hibernation/fans. I thought that a BIOS update would fix the problem. I was right, I updated from version 1.3 to 2.0 and now I have hibernation and fn keys and the fans working properly. The surprise was that I lost network capability.
I did some google and ubuntuforums research, but there are MANY solutions and all (and none) of them seem to fit me.
This is my lspci output:
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```
So, an Intel 2200bg and a Marvell... and this is the output of dmesg | grep ipw
```

[  130.004387] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  130.004391] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  130.366115] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  131.166866] ipw2200: Failed to send TX_POWER: Command timed out.
[  131.288899] ipw2200: Failed to send TX_POWER: Command timed out.
[  131.410883] ipw2200: Failed to send TX_POWER: Command timed out.
[  131.532681] ipw2200: Failed to send TX_POWER: Command timed out.
[  131.654321] ipw2200: Failed to send TX_POWER: Command timed out.
[  131.654327] ipw2200: Unable to initialize device after 5 attempts.
[  131.654336] ipw2200: failed to register network device
[  131.654412] ipw2200: probe of 0000:05:04.0 failed with error -5


```

and dmesg | grep eth:

```

[  121.059709] Driver 'sd' needs updating - please use bus_type methods
[  121.059884]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  124.382802] sky2 eth0: addr 00:a0:d1:30:f6:6b
[  134.489246] sky2 eth0: enabling interface
[  300.563603] ADDRCONF(NETDEV_UP): eth0: link is not ready


```

... ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:30:f6:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:147769 (144.3 KB)  TX bytes:147769 (144.3 KB)

```

... iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

I don't know what to do because I can't connect to the internet to download stuff...

---

### Post by alesp on 2008-05-13
I tried booting with the radio switch off, and now I can see the wireless interface but still can't establish a connection...

---

### Post by alesp on 2008-05-14
A little detail: if I do that trick of booting with the radio turned off and  run ifconfig, then I see that **both** eth1 and eth0 have
```

Interrupt:11

```

---

### Post by alesp on 2008-05-14
Please people! I want to definitely uninstall Windows!

---

### Post by alesp on 2008-05-14
no help here? give a hand to a poor sinner trying to redeem... (by the way, my 1st language is not english)

---

### Post by Ph83drus on 2008-05-16
I have almost the exact same problem.

I bought an intel 2200bg wireless card for my dell d600 with Hardy.

Because the broadcom wireless was a NIGHTMARE.

and guess what, my new Intel wireless card doesn't work either!!

I can see the wireless networks that I COULD connect to, but it will not connect with Wicd.  Will not resolve ip.

phaedrus@phaedrus-laptop:~$ dmesg | grep ipw
[   25.547967] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   25.547972] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.255098] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   28.091135] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
phaedrus@phaedrus-laptop:~$ dmesg | grep eth
[   11.631809] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0d:56:77:6f:11
[   11.631818] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   11.631822] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[   12.702749] Driver 'sd' needs updating - please use bus_type methods
[   12.702975]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 1875.137422] eth1: no IPv6 routers present
[ 1619.425171] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3780.989125] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 3780.989137] tg3: eth0: Flow control is off for TX and off for RX.
[ 3780.993086] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1422.626310] eth0: no IPv6 routers present
[ 4278.637419] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4352.461685] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1867.041490] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1867.041497] tg3: eth0: Flow control is off for TX and off for RX.
[ 1867.043211] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4370.658150] eth0: no IPv6 routers present
phaedrus@phaedrus-laptop:~$ 
phaedrus@phaedrus-laptop:~$

---

### Post by alesp on 2008-05-28
Any idea? I haven't found a solution yet...

---

### Post by negativ on 2008-06-04
I realize this doesn't help, but I have exactly the same problem with a 2200BG card and a Toshiba A105-S2712.  So the configuration is very similar.

The frustrating thing is that I put the 2200BG card into my old Dell Inspiron 8200, and it works fine from the Hardy live CD.

Note that it also does not work properly with Gutsy, and I also tried openSUSE 10.3 on the Toshiba with no success.  Bah.

---

