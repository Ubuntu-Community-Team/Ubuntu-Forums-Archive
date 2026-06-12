---
title: "[Ubuntu 14.04] Wireless Adapter UNCLAIMED, not recognized. Drivers not linking?"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by amos5 on 2016-02-10
Hello All,

I am a newbie here, and very thankful for any and all assistance.

I have recently performed a fresh install of Ubuntu 14.04 on a Brix mini-computer which comes with a Realtek 8821ae Wireless network adapter. Out of the box drivers seemed to hook up seamlessly and things worked fine - but I began having major trouble with my wireless connection, and began looking for any possible driver updates. I hastily found one forum where users were experiencing similar issues, and without thinking I ended up cloning and installing a totally wrong driver with the following commands:


```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)
cd rtl8188ce-linux-driver
sudo make
sudo make install [COLOR=#111111][FONT=Consolas]sudo cp -r firmware/* /lib/firmware
[/FONT][/COLOR]
```

After this I found that my wireless adapter wasn't recognized by the Network Manager and I realized I needed to undo my mess. I ran 'sudo make uninstall' on the new driver, which gave me an output that it will recognize my previous driver, and then I deleted the cloned repo. But still after this my wireless adapter is not recognized at all by my machine. I ran the wireless_script below is my output:



```
########## wireless info START ##########


Report from: 10 Feb 2016 13:17 EST -0500


Booted last: 10 Feb 2016 12:45 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0781:5583 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:128.173.148.243  Bcast:128.173.149.255  Mask:255.255.254.0
          inet6 addr: 2001:468:c80:a107:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2001:468:c80:a107:4488:fe6d:8f02:ba7d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10233677 (10.2 MB)  TX bytes:560523 (560.5 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         128.173.148.1   0.0.0.0         UG    0      0        0 eth0
128.173.148.0   0.0.0.0         255.255.254.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       792     1  0 12:45 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         128.173.148.243
    Prefix:          23 (255.255.254.0)
    Gateway:         128.173.148.1


    DNS:             198.82.247.66
    DNS:             198.82.247.34


  IPv6 Settings:
    Address:         2001:468:c80:a107:4488:fe6d:8f02:ba7d
    Prefix:          64
    Gateway:         fe80::2d0:1ff:feab:1800


    Address:         2001:468:c80:a107:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::2d0:1ff:feab:1800


    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::2d0:1ff:feab:1800


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/belkin.e3f 1]] (600 root)
[connection] id=belkin.e3f 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=belkin.e3f | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC address>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CONNECTtoVT-Wireless]] (600 root)
[connection] id=CONNECTtoVT-Wireless | type=802-11-wireless
[802-11-wireless] ssid=CONNECTtoVT-Wireless | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/belkin.e3f]] (600 root)
[connection] id=belkin.e3f | type=802-11-wireless
[802-11-wireless] ssid=belkin.e3f | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8188ee.conf]
options rtl18188ee ips=0 fwlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    2.864480] r8169 0000:03:00.0 eth0: link down (repeated 2 times)
[    2.864517] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.474239] r8169 0000:03:00.0 eth0: link up
[    4.474247] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############

```




Running lshw -C network I get the following output:

```
*-network UNCLAIMED     
       description: Network controller
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: 40:8d:5c:6c:16:01
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=128.173.148.243 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:31 ioport:d000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
```


So I have learned that this means my drivers are currently not claiming my adapter, and I wondered what must be done to repair this? 

Thanks so much

---

### Post by amos5 on 2016-02-11
okay, the problem was that I upgraded my kernel to 3.19.0-49 which doesn't appear to have support for the Realtek 8821ae driver. I didn't want to delete anything so I've just configured grub to boot into my older kernel by default and that gives me back my wireless adapter.......still gotta do something about that spotty connection...

---

