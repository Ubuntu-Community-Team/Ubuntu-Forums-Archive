---
title: "can't get my wifi to work"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by guy_mograbi on 2014-09-30
I have pasted a lot of details at : [http://askubuntu.com/questions/529812/wifi-does-not-work](http://askubuntu.com/questions/529812/wifi-does-not-work)

following some threads here I also tried the following 

```
sudo lshw -C network
```

and got 
```

 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:0b:6d:36
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=85.64.169.225 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:feaff000-feafffff memory:faffc000-faffffff memory:feac0000-feadffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
       vendor: Qualcomm Atheros
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=160 maxlatency=28 mingnt=10
       resources: memory:febf0000-febfffff



```


I also ran 
```
dmesg | grep ath
```

and got 
```
[149330.288830] ath5k 0000:04:01.0: registered as 'phy0'
[149330.296960] ath5k: phy0: POST Failed !!!
[149330.297040] ath5k: probe of 0000:04:01.0 failed with error -11



```


Can someone help me resolve this?

---

### Post by varunendra on 2014-10-01
Hello guy_mograbi, Welcome to the forums!

Do you have any way to verify that the card itself is not broken?

For example, if it is a dual-boot system, is it working on the other OS?
Or some other Live CD using relatively older or newer Linux kernel?

Just want to rule out that possibility, after which you should file a bug report with the above error against ath5k driver, while we try to troubleshoot it here.

---

