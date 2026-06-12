---
title: "there has got to be a better network manager"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-26
network manager takes forever to connect after startup and suspend and wicd won't connect at all after coming from windows is there anything better?

---

### Post by raul_ on 2009-01-26
Did you configure the connection before connecting with wicd? It doesn't prompt for passwords on anything, you have to enter them before connecting.

---

### Post by bodhi.zazen on 2009-01-26
Wicd is awesome and works for both wired and wireless.

Network manager has, IMO, a number of bugs, and the bugs vary by version of Ubuntu.

In 9.04 network manager will not allow me to set a static IP

There are tons of bug reports in Launchpad and I hope the Gnome / Ubuntu developers can work out the bugs fast.

With that said, wireless is complex and depends on what router and network card you are using as well as WEP / WPA.

When all fails, sometimes one can manually configure the wireless card.

---

### Post by mamamia88 on 2009-01-26
i know that wicd is great but whenever i boot out of windows and back into ubuntu i can no longer browse the web.  and i really don't want to use network manager is there something differnent?

---

### Post by bodhi.zazen on 2009-01-26
iwconfig 

/me runs

---

### Post by albinootje on 2009-01-26
> **mamamia88 said:**
> i know that wicd is great but whenever i boot out of windows and back into ubuntu i can no longer browse the web.  and i really don't want to use network manager is there something differnent?

Can you please check the following and see whether that applies to your computer ?
[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

If not, please post the output of :
```

sudo lshw -C network
route -n
ifconfig -a
cat /etc/resolv.conf

```

---

### Post by mamamia88 on 2009-01-26
*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:72:b5:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.67 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:a7:df:a6:0d:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by albinootje on 2009-01-26
> **mamamia88 said:**
> *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
--- cut ---
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.67 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg


You only have wifi, not ethernet ?
It shows that you have an ip-address with it : 192.168.1.67

If you always use the same connection in Ubuntu for your internet connection, you might as well set up /etc/network/interfaces manually.

See here : [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by mamamia88 on 2009-01-26
i have ethernet just not connected and i mihgt want to use it at school so i don't want to do that.  i guess ill just have to live with waiting 5 minutes after i wake from suspend to use the internet

---

### Post by andrew.46 on 2009-01-27
Hi mamaia,

> **mamamia88 said:**
>             
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation

Have you loaded the firmware for this? I run a BCM4312 quite successfully with Ubuntu but manually downloaded and extracte the required firmware.

Andrew

---

