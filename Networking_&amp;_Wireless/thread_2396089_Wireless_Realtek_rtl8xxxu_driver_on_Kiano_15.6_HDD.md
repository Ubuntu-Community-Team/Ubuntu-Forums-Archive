---
title: "Wireless Realtek rtl8xxxu driver on Kiano 15.6 HDD"
date: 2018-07-11
forum: Networking &amp; Wireless
---

### Post by mengagumkan on 2018-07-11
I installed Ubuntu 18.04 on laptop Kiano SlimNote 15.6 HDD with Intel N3350 CPU and everything works properly except wireless and bluetooth. Her is listing of relevant commands:

```
t@t-K:~$ sudo lshw -C network -numeric
[sudo] password for t: 
  *-network:0               
       description: Ethernet interface
       physical id: 1
       logical name: enp0s21f0u4u2
       serial: aa:6d:34:06:92:88
       size: 10Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=half link=no multicast=yes port=MII speed=10Mbit/s
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:7
       logical name: wlx8420962c707a
       serial: 84:20:96:2c:70:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-24-generic firmware=N/A ip=192.168.8.101 link=yes multicast=yes wireless=IEEE 802.11

```
```
t@t-K:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 0bda:8152 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 1ea7:0064  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
t@t-K:~$ dmesg | grep wlx8420962c707a
[   10.582871] rtl8xxxu 1-7:1.2 wlx8420962c707a: renamed from wlan0
[   10.647169] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   10.656747] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   10.691897] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   11.486212] wlx8420962c707a: authenticate with c4:07:2f:09:4e:79
[   11.489988] wlx8420962c707a: send auth to c4:07:2f:09:4e:79 (try 1/3)
[   11.491551] wlx8420962c707a: authenticated
[   11.492342] wlx8420962c707a: associate with c4:07:2f:09:4e:79 (try 1/3)
[   11.495896] wlx8420962c707a: RX AssocResp from c4:07:2f:09:4e:79 (capab=0x1411 status=0 aid=2)
[   11.497360] wlx8420962c707a: associated
[   11.538205] IPv6: ADDRCONF(NETDEV_CHANGE): wlx8420962c707a: link becomes ready
```

```
t@t-K:~$ dmesg | grep -i blue
[    8.351531] Bluetooth: Core ver 2.22
[    8.351566] Bluetooth: HCI device and connection manager initialized
[    8.351570] Bluetooth: HCI socket layer initialized
[    8.351573] Bluetooth: L2CAP socket layer initialized
[    8.351591] Bluetooth: SCO socket layer initialized
[    8.422167] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    8.422174] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    8.423036] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    8.423043] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    8.425156] Bluetooth: hci0: rom_version status=0 version=1
[    8.425172] Bluetooth: hci0: cfg_sz 0, total size 22496
[   10.094328] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.094330] Bluetooth: BNEP filters: protocol multicast
[   10.094336] Bluetooth: BNEP socket layer initialized
[   21.536254] Bluetooth: RFCOMM TTY layer initialized
[   21.536265] Bluetooth: RFCOMM socket layer initialized
[   21.536277] Bluetooth: RFCOMM ver 1.11
```

```
t@t-K:~$ uname -r
4.15.0-24-generic
t@t-K:~$
```

Wireless works, but only very close to the router. The level shows only 40% and it should be close to 100%. Few meters from the router and the connection drops off.
Wit the BT it seems to be working but does not discover any bt devices even on very close range.
All my other laptops and smartphones work fine with this router.

I tried everything I could on my own but to no avail. Please help.

---

### Post by praseodym on 2018-07-11
RTL8723bu  is the correct driver for that USB wireless device

```
sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
iwconfig
```

---

### Post by mengagumkan on 2018-07-12
praseodym, thanks very much for your reply. I done what you advised, unfortunately it did not change much. Here are codes after running the commands as above (which executed without errors) before rebooting:

t@t-K:~/rtl8723bu$ iwconfig
lo        no wireless extensions.

enp0s21f0u4u2  no wireless extensions.

wlx8420962c707a  IEEE 802.11  ESSID:"HUAWEI-B315-4E79" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:07:2F:09:4E:79  
          Bit Rate=1 Mb/s   Tx-Power=30 dBm  
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:0

t@t-K:~/rtl8723bu$ dmesg | grep wlx8420962c707a
[   10.750731] rtl8xxxu 1-7:1.2 wlx8420962c707a: renamed from wlan0
[   10.804601] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   10.811821] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   10.895066] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   11.654684] wlx8420962c707a: authenticate with c4:07:2f:09:4e:79
[   11.656802] wlx8420962c707a: send auth to c4:07:2f:09:4e:79 (try 1/3)
[   11.658286] wlx8420962c707a: authenticated
[   11.660074] wlx8420962c707a: associate with c4:07:2f:09:4e:79 (try 1/3)
[   11.663615] wlx8420962c707a: RX AssocResp from c4:07:2f:09:4e:79 (capab=0x1411 status=0 aid=3)
[   11.665198] wlx8420962c707a: associated
[   11.708412] IPv6: ADDRCONF(NETDEV_CHANGE): wlx8420962c707a: link becomes ready

And after rebooting:

t@t-K:~$ iwconfig
lo        no wireless extensions.

enp0s21f0u4u2  no wireless extensions.

wlx8420962c707a  IEEE 802.11  ESSID:"HUAWEI-B315-4E79"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:07:2F:09:4E:79   
          Bit Rate=1 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

t@t-K:~$ dmesg | grep wlx8420962c707a
[   11.432963] rtl8xxxu 1-7:1.2 wlx8420962c707a: renamed from wlan0
[   11.461672] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   11.471257] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   11.504837] IPv6: ADDRCONF(NETDEV_UP): wlx8420962c707a: link is not ready
[   12.262729] wlx8420962c707a: authenticate with c4:07:2f:09:4e:79
[   12.265053] wlx8420962c707a: send auth to c4:07:2f:09:4e:79 (try 1/3)
[   12.266531] wlx8420962c707a: authenticated
[   12.272142] wlx8420962c707a: associate with c4:07:2f:09:4e:79 (try 1/3)
[   12.276337] wlx8420962c707a: RX AssocResp from c4:07:2f:09:4e:79 (capab=0x1411 status=0 aid=3)
[   12.277693] wlx8420962c707a: associated
[   12.498401] IPv6: ADDRCONF(NETDEV_CHANGE): wlx8420962c707a: link becomes ready

t@t-K:~$ sudo lshw -C network -numeric
[sudo] password for t: 
  *-network:0               
       description: Ethernet interface
       physical id: 1
       logical name: enp0s21f0u4u2
       serial: aa:6d:34:06:92:88
       size: 10Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=half link=no multicast=yes port=MII speed=10Mbit/s
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:7
       logical name: wlx8420962c707a
       serial: 84:20:96:2c:70:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-24-generic firmware=N/A ip=192.168.8.101 link=yes multicast=yes wireless=IEEE 802.11

Looks like still rtl8xxxu is loaded?
I tried this laptop on Windows 10 as I have double booting and this wirelesa there works fine.

---

### Post by praseodym on 2018-07-12
Please show
```

lsmod
```

---

### Post by mengagumkan on 2018-07-12
Thanks praseodym. You really helped me. I had 8723bu blacklisted (residue from what I done previously trying). I removed that by editing /etc/modprobe.d/blacklist.conf and blacklisted rtl8xxxu instead then rebooted.
Now my wireless works like charm.

Yet, could you advise me about Bluetooth? (see the bt output in the first post)

---

### Post by mengagumkan on 2018-07-12
Bluetooth is working now too. Thanks again.

---

