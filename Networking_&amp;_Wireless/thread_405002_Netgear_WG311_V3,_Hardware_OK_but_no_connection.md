---
title: "Netgear WG311 V3, Hardware OK but no connection"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by Snowin on 2007-04-09
Hi,

I've been playing with Ubuntu for a little while, resolved a few issues with my hardware but i've come accrooss something that I can't get to the bottom of on my own.

I'm using a Netgear WG311 V3 wireless card.  Using NDISWrapper, I've got my feisty fawn isntallation to see the card.  I've done this by the following method:

1. Install ndiswrapper from repositry
2. ndiswrapper -i /path/to/driver
3. ndiswrapper -l showed the hardware present, and the driver present
4. modprobe -i ndiswrapper (straight in, no errors in /var/log/syslog or from dmesg)
```

dmesg:
[ 2009.340000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 2009.440000] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[ 2009.444000] ndiswrapper: using IRQ 5
[ 2009.996000] wlan0: ethernet device 00:14:6c:c4:5c:a0 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
[ 2009.996000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2011.832000] usbcore: registered new interface driver ndiswrapper
[ 2013.640000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

/var/log/syslog:
```

Apr  9 11:06:16 owen-desktop kernel: [ 2009.340000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Apr  9 11:06:16 owen-desktop kernel: [ 2009.440000] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Apr  9 11:06:16 owen-desktop kernel: [ 2009.444000] ndiswrapper: using IRQ 5
Apr  9 11:06:17 owen-desktop kernel: [ 2009.996000] wlan0: ethernet device 00:14:6c:c4:5c:a0 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
Apr  9 11:06:17 owen-desktop kernel: [ 2009.996000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr  9 11:06:17 owen-desktop NetworkManager: <debug info>^I[1176113177.301500] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_14_6c_c4_5c_a0'). 
Apr  9 11:06:19 owen-desktop kernel: [ 2011.832000] usbcore: registered new interface driver ndiswrapper
Apr  9 11:06:20 owen-desktop kernel: [ 2013.640000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  9 11:06:20 owen-desktop NetworkManager: <information>^Iwlan0: Device is fully-supported using driver 'ndiswrapper'. 
Apr  9 11:06:20 owen-desktop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Apr  9 11:06:20 owen-desktop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Apr  9 11:06:20 owen-desktop NetworkManager: <information>^INow managing wireless (802.11) device 'wlan0'. 
Apr  9 11:06:20 owen-desktop NetworkManager: <information>^IDeactivating device wlan0. 
Apr  9 11:06:22 owen-desktop NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 

```

At this point I can see the card from lshw -C network:
```

  *-network               
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 6
       bus info: pci@01:06.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:c4:5c:a0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=NETGEAR,02/22/2005,3.1.1.7 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fdff0000-fdffffff iomemory:fdfe0000-fdfeffff irq:5

```

The card shows up in iwconfig as well:
```

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=24 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So as far as I can see, the kernel knows about the hardware (as does everything else) and the hardware is working.

So I'm thinking that I'm on a roll, and that my linux skills are actually better than they are, since there is loads of stuff out there saying that you can't do this.

NetworkManager sees the card, and can even see the wireless network that i want to connect to.  

iwlist wlan0 scan even returns:
```

wlan0     Scan completed :
          Cell 01 - Address: 00:14:7F:5C:DD:29
                    ESSID:"BTHomeHub-EAE5"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:09:5B:5E:9C:03
                    ESSID:"Ceres"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

```
so the machine can see my access ESSID (Ceres) and someone else's a bit further down the road.  

I then get NetworkManager to try and hook into the network, with the correct WPA-PSK, and it bombs.

dmesg contain the following information:
```

[ 2092.788000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2103.716000] wlan0: no IPv6 routers present
[ 2116.440000] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 2154.616000] ndiswrapper (set_essid:60): setting essid failed (C0000001)
[ 2163.412000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.928000] eth0: no IPv6 routers present

```
and /var/log/syslog has more, see the attached .txt.gz file

Anybody got any ideas where I went wrong?

---

### Post by sonicmaker on 2008-07-20
I know this post was made a while ago but I am having the exact same problem... but in Hardy. Has anyone made any progress on this?

Something else interesting I've noted is that when the computer tries to connect to the internet, it boots my other wirelessly-connected computer off the network... but only until I give up trying to connect with the first one. After that the second one connects again with no worries. I've got the latest firmware update for my router, and it hasn't always been a problem, possibly just since kernel 2.6.24-19 was released to the repositories...

---

