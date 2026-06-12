---
title: "Intel PCIe card not showing any WiFi Networks"
date: 2020-12-13
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2020-12-13
I have a system running 20.04 LTS it currrently has a US WiFi dongle and a PCIE WiFi card. The USB dongle works ok. The Pcie card does not find any WiFi netwrks, but the USB one find a bunch.

I originally thought the problem was hardware related to the realtek chipset on the card. 
[RTL8812AE drivers in 18.04 and 20.04]("https://ubuntuforums.org/showthread.php?t=2453352")

I replaced the card with another card with an Intel chipset, the problem persists.

I ran the Wifiinfo script and posted it in pastbin [https://paste.ubuntu.com/p/jvGvJ5JTwT/](https://paste.ubuntu.com/p/jvGvJ5JTwT/)

I loaded a live session and the Intel WiFi card worked just fine.

ifconfig sees both interfaces:
```
# ifconfig -a
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5941  bytes 597065 (597.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5941  bytes 597065 (597.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9c:29:76:0c:e2:cf  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx00173f1d449a: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.59  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5060:15d9:577:c952  prefixlen 64  scopeid 0x20<link>
        inet6 2601:c2:c380:8d90:a8fc:cfb8:6a39:8974  prefixlen 64  scopeid 0x0<global>
        inet6 2601:c2:c380:8d90:5d0d:8682:ed26:8962  prefixlen 64  scopeid 0x0<global>
        inet6 2601:c2:c380:8d90::1  prefixlen 128  scopeid 0x0<global>
        ether 00:17:3f:1d:44:9a  txqueuelen 1000  (Ethernet)
        RX packets 75165  bytes 63182264 (63.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 70660  bytes 13884942 (13.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

But the PCIe card wlp3s0 does not connect and has no traffic.

The correct driver seems to be loading.

```
# lshw -C network
  *-usb:0                   
       description: Wireless interface
       product: USB2.0 WLAN
       vendor: Belkin
       physical id: 1
       bus info: usb@2:1
       logical name: wlx00173f1d449a
       version: 48.10
       serial: 00:17:3f:1d:44:9a
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=5.4.0-58-generic firmware=4725 ip=192.168.0.59 link=yes maxpower=500mA multicast=yes speed=12Mbit/s wireless=IEEE 802.11  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 61
       serial: 9c:29:76:0c:e2:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-58-generic firmware=29.1654887522.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:27 memory:dfffe000-dfffffff

```

```
# rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

not sure what this means:

```
dmesg | grep wl
[    9.796594] , Hewlett-Packard OfficeJet Series 700
[   22.291389] iwlwifi 0000:03:00.0: Found debug destination: EXTERNAL_DRAM
[   22.291392] iwlwifi 0000:03:00.0: Found debug configuration: 0
[   22.291807] iwlwifi 0000:03:00.0: loaded firmware version 29.1654887522.0 op_mode iwlmvm
[   23.821145] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[   23.834273] iwlwifi 0000:03:00.0: Applying debug destination EXTERNAL_DRAM
[   23.835519] iwlwifi 0000:03:00.0: Allocated 0x00400000 bytes for firmware monitor.
[   23.839827] iwlwifi 0000:03:00.0: base HW address: 9c:29:76:0c:e2:cf
[   23.907752] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   26.588202] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   26.748202] zd1211rw 2-1:1.0 wlx00173f1d449a: renamed from wlan1
[   39.716595] iwlwifi 0000:03:00.0: Applying debug destination EXTERNAL_DRAM
[   39.801219] iwlwifi 0000:03:00.0: Applying debug destination EXTERNAL_DRAM
[   39.802280] iwlwifi 0000:03:00.0: FW already configured (0) - re-configuring
[   87.691856] wlx00173f1d449a: authenticate with 1c:49:7b:99:ee:9e
[   87.779386] wlx00173f1d449a: send auth to 1c:49:7b:99:ee:9e (try 1/3)
[   87.782292] wlx00173f1d449a: authenticated
[   87.786273] wlx00173f1d449a: associate with 1c:49:7b:99:ee:9e (try 1/3)
[   87.790335] wlx00173f1d449a: RX AssocResp from 1c:49:7b:99:ee:9e (capab=0x1411 status=0 aid=5)
[   87.791244] wlx00173f1d449a: associated
[   88.044636] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00173f1d449a: link becomes ready
[ 1853.844538] wlx00173f1d449a: deauthenticating from 1c:49:7b:99:ee:9e by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1856.075671] wlx00173f1d449a: authenticate with 1c:49:7b:99:ee:9e
[ 1856.146505] wlx00173f1d449a: send auth to 1c:49:7b:99:ee:9e (try 1/3)
[ 1856.149444] wlx00173f1d449a: authenticated
[ 1856.150014] wlx00173f1d449a: associate with 1c:49:7b:99:ee:9e (try 1/3)
[ 1856.153401] wlx00173f1d449a: RX AssocResp from 1c:49:7b:99:ee:9e (capab=0x1411 status=0 aid=5)
[ 1856.154393] wlx00173f1d449a: associated
[ 1857.008067] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00173f1d449a: link becomes ready

```

HELP

---

### Post by jeremy31 on 2020-12-13
in terminal ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if the internal works with wifi power management disabled

---

### Post by rsteinmetz70112 on 2020-12-13
OK I tried that suggestion and it didn't do anything.

After some research I  also edited the file: 
```
/etc/NetworkManager/conf.d/10-globally-managed-devices.conf
```
to add 
```
[keyfile]
unmanaged-devices=none
```

That caused the networks to be visible, but it still didn't work. The configuration of the PCIe card wasn't right.

I looked at the file /etc/netplan 
```
01-netcfg.yaml
```
the .yaml file seemed to be incorrect so I edited it to this:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp3s0:
      dhcp4: yes
      gateway4: 192.168.0.1
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
```

It kind of works but I'm not sure I got the .yaml file correct.

---

### Post by rsteinmetz70112 on 2020-12-14
It's been overnight and it's still working, in fact it's working better than ever. I'm marking thsi Solved.

---

