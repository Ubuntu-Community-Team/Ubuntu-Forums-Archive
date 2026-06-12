---
title: "RTL8188CE not working on 13.04, worked on 12.10"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by sybren-stuvel on 2013-09-27
Hi folks,

I've just updated Kubuntu from 12.10 to 13.04, on an ASUS X75A laptop. On 12.10 the wireless card worked just fine. However, after the update to 13.04 it stopped working. Dual-booting to Win8 shows that the card is physically still fine (it works there). I have disabled the "Windows is allowed to turn this device off" setting and rebooted to Kubuntu while wifi was enabled, but to no avail.

"lshw -C network" shows:

```
  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 20:68:9d:75:b5:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:e000(size=256) memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 74:d0:2b:4b:59:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=172.27.0.215 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:f7c00000-f7c3ffff ioport:d000(size=128)

```

The output of "rfkill list" is:

```
0: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

Pressing FN+F2 doesn't change anything.  The BIOS settings show everything as UnLocked (sic); with identical settings Kubuntu 12.10 worked, so it's not that.
The kernel module in use is rtl8192ce. I've tried loading with different values for the ips, swlps and fwlps options, to no avail.

All in all, this seems to be a driver issue. I've tried to compile the drivers from the [Realtek site]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE"), but those failed:

```

$ make
make -C /lib/modules/3.8.0-31-generic/build M=/home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  CC [M]  /home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/sybren/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'
make: *** [all] Error 2

```

Besides that, I'm preparing this laptop for my mother's use; she's used to Kubuntu but I don't want to have her recompile her own driver whenever a kernel upgrade is pushed.

**UPDATE:** Just after I posted this, I experimented with going to standby. Lo and behold, when the laptop comes back from its sleep, wifi works and "rfkill list" shows:

```
0: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

Still, I would very much like to have this working without having to go to standby. When turning off the laptop and turning it on again, the card is hard blocked again, and I have to do another standby-trick.

Regards,
Sybren

---

### Post by peboettch on 2013-11-09
Hey guys,

I have exactly the same problem as the TO... Is there no fix for this bug? It is extremely annoying.
Greets from Germany,
Peter :)

---

### Post by sybren-stuvel on 2013-11-09
I hope there is a fix somewhere!

Sybren

---

### Post by peboettch on 2013-11-13
Good News!
After Upgrading to Xubuntu 13.10 the Problem is solved, wireless is now working completely... But a next bug appeared: Something is wrong with the audio/sound management. The icon in the taskbar is disabled. But because you can still set our volume with the Fn Keys it don't matter to me.
Regards,
Peter

---

### Post by sybren-stuvel on 2013-11-14
Thanks, Peter, for the update. I'll test with Kubuntu 13.10 and see if that works too.

---

