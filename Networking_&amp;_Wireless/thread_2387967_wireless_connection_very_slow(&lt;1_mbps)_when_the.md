---
title: "wireless connection very slow(&lt;1 mbps) when the phone connection works"
date: 2018-03-26
forum: Networking &amp; Wireless
---

### Post by sagi212 on 2018-03-26
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]I did a speed test for my ubuntu 16.04and the wifi connection is capable of speeds up to 55 mbps but usually, it stays less than 1 mbps. My phone which is on the same wifi has speeds of about 50 mbps. I've tried disabling ipv6, it made no difference so I enabled it. I tried to force disable the 802.11n protocol with[/FONT]
```
[FONT=inherit]sudo rmmod iwlwif[/FONT]
```
[FONT=inherit]but I get this 
```
error: rmmod: ERROR: Module iwlwif is not currently loaded
```[/FONT]
[FONT=inherit]So i am guessing 802.11n is disabled already? my wireless card is[/FONT]
```

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: d0:17:c2:1c:83:10
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:d000(size=256) memory:dfb04000-dfb04fff memory:dfb00000-dfb03fff
  *-network
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: b0:c0:90:68:76:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.13.0-37-generic firmware=N/A ip=192.168.50.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 ioport:c000(size=256) memory:dfa00000-dfa03fff

```[FONT=inherit]

Keep in mind that at home, my internet wifi works fine after hours of finding the right drivers for my realtek wireless card. But at work it is barely working. I got the drivers from this page[/FONT]
[FONT=inherit][URL="https://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/"]
Realtek Wifi Card RTL8723be Not Working Properly[/URL][/FONT]
[FONT=inherit]
but instead of pulling from rtlwifi_new I pulled from rtlwifi_new-master. It gave me errors when I pulled from rtlwifi_new[/FONT]

```

cd Desktop
cd rtlwifi_new-master
make
sudo make install
sudo modprobe -rv rtl8821ae
sudo modprobe -v rtl8821ae ant_sel=2
sudo ip link set wlp3s0 up
sudo iw dev wlp3s0 scan
echo "options rtl8821ae ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8821ae.conf

```[FONT=inherit]

after some more research i realize the rtl8821ae driver does not ant_sel as a parameter so i deleted the file with "options ant_sel=2"

Then i attempted to pull extended instead of the master branch to get the latest drivers. 

[/FONT]```

cd rtlwifi_new-master
sudo make uninstall
sudo modprobe -r rtl8821ae
cd ..
sudo rm -rf rtlwifi_new-master
git clone -b extended [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
cd rtlwifi_new
make
sudo make install
sudo modprobe rtl8821ae[FONT=inherit]
[/FONT]
```[FONT=inherit]

[/FONT][/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Still no luck. I was told to not rule out the possibility that this has more to do with the workplace router than my drivers, since this laptop works fine at home.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu][FONT=inherit]
 But if that is the case, why does my phone work perfectly on my work connection?[/FONT]
[/FONT][/COLOR]

---

