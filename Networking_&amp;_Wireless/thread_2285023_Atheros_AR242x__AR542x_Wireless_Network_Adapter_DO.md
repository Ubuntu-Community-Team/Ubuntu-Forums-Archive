---
title: "Atheros AR242x / AR542x Wireless Network Adapter DO NOT Connect"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by xulsolar on 2015-07-02
Hi-- I am seeking the help of the linux experts here.
Ubuntu doesn't automatically get the wireless cards going right away.
I seek answers on the forums but none of them works
I have even reinstalled 2 Ubuntu versions 12 and 14 without luck.
I am working with a HP Pavillon dv6000 laptop.

Here's some info to use in helping diagnose. Thanks for any insights you can provide.

uname -r
3.13.0-55-generic

lshw -C network
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:29:f8:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.13.0-55-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:f6000000-f600ffff

lsmod | grep -e ath -e 80211
ath5k                 152486  0 
ath                    29145  1 ath5k
mac80211              658200  1 ath5k
cfg80211              502970  3 ath5k,ath,mac80211

dmesg | grep -i -e warn -e error
8.884758] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

dmesg | grep -e ath5 -e wlan
[    8.635695] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    8.636041] ath5k 0000:03:00.0: registered as 'phy0'
[   13.963000] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.718628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.719032] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by xulsolar on 2015-07-02
Thanks I just follow this thread.

[http://ubuntuforums.org/showthread.php?t=2166532&highlight=ath5k+0000%3A03%3A00.0%3A+can%27t+find+IRQ+PCI](http://ubuntuforums.org/showthread.php?t=2166532&highlight=ath5k+0000%3A03%3A00.0%3A+can%27t+find+IRQ+PCI)

---

