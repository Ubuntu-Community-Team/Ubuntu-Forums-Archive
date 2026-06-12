---
title: "No wifi networks appear in new install."
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by kainau on 2016-08-01
I just built a new computer using the Asus H110T and an Intel 7260 Network card, and no wifi networks appear in the Network Manager. (yes there are wifi networks in range) The ethernet ports do work though.  I only have Ubuntu installed on it, and I've fully upgraded everything. Here is some diagnostic code I thought you might like to see based on other posts I've looked at while trying to figure this out.  Is there any other information I should provide you?

```
~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: bb
       serial: cc:3d:82:a7:58:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=16.242414.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:126 memory:f7100000-f7101fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 15
       serial: 34:97:f6:87:f3:e5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:122 ioport:e000(size=256) memory:f7004000-f7004fff memory:f7000000-f7003fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 34:97:f6:87:f3:e4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.1.109 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:123 memory:f7200000-f721ffff
```
```
~$ sudo iwconfig
lo        no wireless extensions.

enp0s31f6  no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
```

Any other diagnostic code I should run for you guys?

---

### Post by speartip on 2016-08-01
This might sound silly, but try shutting down your computer fully, then start it up & see if you have networks available now?

---

### Post by jeremy31 on 2016-08-01
See the wireless script link in my signature and post your results

The iwconfig results showing TX Power=0 is a bit strange

---

### Post by kainau on 2016-08-01
> This might sound silly, but try shutting down your computer fully, then  start it up & see if you have networks available now?
Already tried that, didn't work.

Going to run the script now.

UPDATE: Here are the results: [ATTACH]270521[/ATTACH]

---

### Post by kainau on 2016-08-02
Does anyone have any ideas? I've been looking at the results, and I have no idea what to make of it.

Thanks for any help you can give.

---

### Post by kingsleyfhk65 on 2016-08-04
I am having issue like that for the past few months and purchase 3 difference brands/model(AC7260, AC3160 & AR5B22) of wifi modules to get it working in my HP Envy-4. Finally, i found a very simple solution from the forum and it just ask you to go back to your Bios setup and do a default setup(My notebook is F9). Reboot my notebook and all 3 brands of wifi just works perfectly. 1st command to check before the Bios setup is "sudo rfkill list". If you see hardware is blocked. Do the Bios default setting. If it is software "blocked" command is "sudo rfkill unblock all". Hope this can help.

---

### Post by kainau on 2016-08-10
I ran:
```
kai@DIYTop ~ $ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Weird.

Anyways, I checked the BIOS and it looked fine. I also ran ```
sudo rfkill unblock all
``` and reinstalled the OS for good measure, none of those worked.  Of course checking after each change.

---

### Post by jeremy31 on 2016-08-10
You have installed backports, please uninstall

---

