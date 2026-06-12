---
title: "rtl8187: RX process aborted due to explicit shutdown"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by tomolac on 2006-10-27
I'm trying to use my netgear WG111v2 usb dongle to connect to my router but it just wont do it?
I get

```

wlan0     802.11b/g  ESSID:"homeJON"
          Mode:Managed  Channel=2  Access Point: Not-Associated
          Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

when I do iwconfig, and the blue led lights up for a second when I try and activate it but nothing happens.
dmesg reports

```

[  475.446656] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  475.509492] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[  475.577442] rtl8187: Card MAC address is 00:14:6c:b1:10:5d
[  475.680045] rtl8187: Card reports RF frontend Realtek 8225
[  475.680049] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[  475.680052] rtl8187: WW:use it with care and at your own risk and
[  475.680054] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[  475.697942] rtl8187: This seems a legacy 1st version radio
[  475.698055] rtl8187: PAPE from CONFIG2: 0
[  475.698113] rtl8187: Driver probe completed
[  475.698114]
[  484.142828] rtl8187: Setting SW wep key
[  484.426618] rtl8187: Card successfully reset
[  490.052391] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  502.727597] rtl8187: RX process aborted due to explicit shutdown
[  502.727653] rtl8187: RX process aborted due to explicit shutdown
[  502.727709] rtl8187: RX process aborted due to explicit shutdown
[  503.282261] sky2 eth1: enabling interface
[  504.116706] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control none[  508.167830] eth1: no IPv6 routers present
[  892.635540] sky2 eth1: disabling interface
[  894.017317] rtl8187: Setting SW wep key
[  894.299258] rtl8187: Card successfully reset
[  899.831270] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  906.938106] rtl8187: RX process aborted due to explicit shutdown
[  906.938219] rtl8187: RX process aborted due to explicit shutdown
[  906.938333] rtl8187: RX process aborted due to explicit shutdown
[  907.675143] rtl8187: Card successfully reset
[  913.249279] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  917.239384] rtl8187: RX process aborted due to explicit shutdown
[  917.239497] rtl8187: RX process aborted due to explicit shutdown
[  917.239611] rtl8187: RX process aborted due to explicit shutdown
[  917.286166] rtl8187: Setting SW wep key
[  917.582991] rtl8187: Card successfully reset
[  922.920773] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

I've had a look through the forum and google but cant find any help?

---

### Post by emjotsh on 2006-12-17
Hallo tomolac,
please, see [http://ubuntuforums.org/showthread.php?t=132022](http://ubuntuforums.org/showthread.php?t=132022). This solution helped me :) and should also be the solution for your problem.
The modul r8187 must be removed if you are using ndiswrapper.
1. Add to /etc/modprobe.d/blacklist the line : blacklist r8187
2. Remove device Netgear
3. rmmod r8187 (if it exists)
4. Fit Netgear into USB

Consider bug #59983 in Edgy Eft: 
1. Install ndiswrapper-utils-1.8
2. Delete /usr/sbin/ndiswrapper
3. Set the symbolic link ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper

---

