---
title: "Broadcom BCM4306 wireless card -- help needed"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by ultim8 on 2008-11-29
Hey guys,

I have a HP Pavilion zv5000 running on Intrepid.  My wireless card is a Broadcom BCM4306:
```
jason@toby:~$ lspci | grep Broadcom
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I have gone to the Hardware Drivers GUI to activate my card, I have also installed my cards driver from [http://ubuntu.cafuego.net/]("http://ubuntu.cafuego.net/")

I can see my wireless card when I run ifconfig:
jason@toby:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:4b:c9:d0  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe4b:c9d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1044914 (1.0 MB)  TX bytes:200016 (200.0 KB)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15240 (15.2 KB)  TX bytes:15240 (15.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:9e:83:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-9E-83-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

But the network manager does not show any available networks (yes I know for a fact that there are atleast 6 viewable networks within range).

Running iwlist wlan0 accesspoints gives me the same results:
```
jason@toby:~$ iwlist wlan0 accesspoints
wlan0     Interface doesn't have a list of Peers/Access-Points
```

I'm not sure what to do from here.  The driver seems to be working well enough to atleast see it from ifconfig...  Does anyone have any pointers?

I would love some help,

Thanks,
-Jason

---

### Post by Flare183 on 2008-11-29
Install the BCM43xx Driver, I think that it is in the repos.

---

### Post by Hydrohs on 2008-11-29
If that doesn't work you could also try installing ndiswrapper.

You might need to use your Ubuntu CD for it though.

---

### Post by Ayuthia on 2008-11-29
Can you post the results of lshw -C network?  It will help us see if the firmware was downloaded properly after running Hardware Drivers.

---

### Post by ultim8 on 2008-11-30
> **Ayuthia said:**
> Can you post the results of lshw -C network?  It will help us see if the firmware was downloaded properly after running Hardware Drivers.

```
jason@toby:~$ sudo lshw -C network
[sudo] password for jason: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4b:c9:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.47 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:9e:83:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:ae:7e:ed:21:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

The BCM43XX driver is not in the repos... atleast I can't find it.  I'll use ndiswrapper if I need to... but I was hoping the new support for the b43 driver in Intrepid would just work.  Besides, I'm not really sure how to go about using ndiswrapper.

---

### Post by Ayuthia on 2008-11-30
You are correct about bcm43xx.  It is not in Intrepid because it has been removed from the kernel (the kernel developers removed it in 2.6.27).

Can you check:
```
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
```
and see that only b43 and ssb show up and not wl or ndiswrapper?  Most likely that is all that is showing.  It looks like b43 and ssb are the only ones that are loaded and the firmware is in place. 

Can you also check:
```
ls /lib/firmware
dmesg | grep -e b43 -e wlan
sudo iwlist scan
```
I just want to confirm that there is a b43 folder in /lib/firmware and that there are no error messages that are currently logged.  I also would like to see if the system can just do the typical wireless scan.

---

### Post by ultim8 on 2008-12-02
Sorry for my delayed reply....  apparently a new born baby sometimes takes precedent over getting wireless working on my laptop ;-).

```
jason@toby:~$ lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  1 b43
```

```
jason@toby:~$ ls /lib/firmware | grep b43
b43
b43legacy
```

```
jason@toby:~$ dmesg | grep -e b43 -e wlan
[    7.397792] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   30.435538] b43-phy0: Broadcom 4306 WLAN found
[   73.829639] input: b43-phy0 as /devices/virtual/input/input10
[   73.960052] firmware: requesting b43/ucode5.fw
[   74.038876] firmware: requesting b43/pcm5.fw
[   74.043211] firmware: requesting b43/b0g0initvals5.fw
[   74.121455] firmware: requesting b43/b0g0bsinitvals5.fw
[   74.360048] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   74.514486] Registered led device: b43-phy0::tx
[   74.514843] Registered led device: b43-phy0::rx
[   74.515342] Registered led device: b43-phy0::radio
[   74.536278] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

```
jason@toby:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```

---

### Post by Ayuthia on 2008-12-02
Congratulations!  I am surprised that you have made it back so early.  I don't know if my wife would let be back to work on my laptop after a couple of days.

Unfortunately, I don't know if I am going to be much help here.  You might try using ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This is the second 4306 rev 03 card that I have seen in Intrepid that does not seem happy with b43.

Can help me out and post your lspci -nnm information so that I can see the subvendor information?  Hopefully it will help track down if the issue is with a specific card.

---

