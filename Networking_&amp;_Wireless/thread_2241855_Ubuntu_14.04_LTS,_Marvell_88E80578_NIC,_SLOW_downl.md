---
title: "Ubuntu 14.04 LTS, Marvell 88E80578 NIC, SLOW download, but not upload."
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by Stian_Blindheim on 2014-08-28
Hi there everyone :)

First time posting at the forum, but a long timer(sort of) reader. 

I was running ubuntu 12.04 LTS up until a week ago, where I decided to upgrade to 14.04 LTS. The upgrade from within 12.04 failed miserably so I had to install from scratch. This doesn't mean anything other than to tell you I have a clean system with only a few programs installed.

When running speedtest.net on my wifi-connection i get this:
[IMG]http://www.speedtest.net/result/3720972402.png[/IMG]

When running the same test on my integrated NIC, Marvell 88E8057 I get this:
[IMG]http://www.speedtest.net/result/3720995415.png[/IMG]

I pay for a 50/50 line. On the old 12.04 LTS I got 25/25 at speedtest.net (just recently upgraded to 50/50). Something fishy is happening. I've tried, but not been able to, install upgraded driver from marvell (dated from 2012). I've read about something kalled msk on ubuntu manual, but not figured out how to change to that driver. The module currently loaded is named sky2.ko. 

The computer is a Sony Vaio VPcf13soe. 

Can anyone help me to utilize my 50/50 fibreoptic line? 

Thank you! 

regards, 
Stian Blindheim

---

### Post by varunendra on 2014-08-29
Hi Stian, Welcome to the forums!

> **Stian_Blindheim said:**
> I've read about something kalled msk on ubuntu manual, but not figured out how to change to that driver. The module currently loaded is named sky2.ko.

You have probably seen the "disable_msi" parameter, which can be used as follows -

Open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
sudo modprobe -rv sky2
[s]sudo modprobe -v sky2 disable_msi=2[/s]
sudo modprobe -v sky2 disable_msi=1
```
The first command will remove the driver thus disabling the Ethernet, the second one will reload it with the desired parameter. It will be a temporary change that will be lost at next boot.

If it helps, we can make it permanent. If not, please post the outputs of -
```
sudo lshw -C network
nm-tool
```

---

### Post by Stian_Blindheim on 2014-08-29
> **varunendra said:**
> 
If it helps, we can make it permanent. If not, please post the outputs of -
```
sudo lshw -C network
nm-tool
```

Hi, thanks for the reply. Unfortunately this doesn't work :( 

the output of sudo lshw -C network is:
```
  *-network DISABLED             description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:6c:7a:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-34-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:55 memory:e8e00000-e8e01fff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 54:42:49:74:3d:01
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.0.0.82 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:e6620000-e6623fff ioport:a000(size=256) memory:e6600000-e661ffff

```

The output from nm-tool is:
```
NetworkManager Tool

State: connected (global)


- Device: eth0  [Kabeltilkobling 1] --------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        54:42:49:74:3D:01


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.0.0.82
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138


    DNS:             130.67.15.198
    DNS:             193.213.112.4
    DNS:             10.0.0.138




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        00:27:10:6C:7A:F8


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 

```

Thanks!

-Stian

---

### Post by varunendra on 2014-08-29
Sorry, I made a mistake with the modprobe command in my previous post. Just corrected it (changed parameter value '2' to '1'). Could you try the changed value please? Does it change the behaviour in any way? (does it let you connect at all?)

If not, please test how it behaves if we limit the speed to 100 Mbps -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Test the connection in this state and report back the performance.

To reset it to default -
```
sudo ethtool -s eth0 speed 1000 duplex full autoneg on
```

---

### Post by Stian_Blindheim on 2014-08-30
Still no luck. With disable_msi=1 there was no difference. Speed just about the same. 

When limited to 100 the speed increases to 6-7 (instead of 5) but still nothing close to the 50 it's supposed to be :(

I tried to change the speed to 100 with and without the disable_msi parameter, but no differece there either. 

-Stian

---

### Post by varunendra on 2014-09-01
Sorry for the delay, more work, less time etc..

I don't know, neither is there any hint in the module info (modinfo sky2) about the default value of 'disable_msi' parameter. So assuming it could already be '1', please also try value '0' this time -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 disable_msi=0
```

There is another parameter "legacy_pme" that may click (frankly, I have no experience with this driver and don't have a clear idea what these parameters are supposed to do). You may try it in place of "disable_msi" or along with it. For example -
```
sudo modprobe -rv sky2
sudo modprobe -v sky2 disable_msi=0 legacy_pme=1
```

As a different blind shot, I think you should also try MTU values (from Network Manager) 1492 or 1392 instead of 'Automatic' which defaults to 1500. Although this is probably a far cry since 1500 has been default MTU value in Ubuntu since ever, and you mentioned it was working before. But testing with it won't hurt, so..

As you can tell by now, I'm just trying random things now, no hints or clues to pick up a definite direction to work in. If the above don't help, please also post the output of -
```
modinfo sky2
uname -mr
```

---

### Post by Stian_Blindheim on 2014-09-10
Hi again, and sorry for the delay. 

I tried various values of the disable_msi and legacy_pmi both together and nothing worked. So I took Ubuntu 12.04.5 and threw on an USB-stick and live booted. By cable the speed still sucks. No difference what so ever. Then I tried Linux mint. Still no difference. 

So naturally I'm running out of ideas. My last attempt was to change the cable, the port on my router AND force a IP renew. STILL NO DIFFERENCE. 

Right now I can't remember if I did a speed test on my other computer running Linux in my living room, but I'm going to test that when I get home.  

I'm starting to think it's my router that's causing this, alternative some of my equipment is acting up. 

I'm really frustrated!!! 

Thanks for your help so far! (I'm not marking the thread as solved yet, I have to test some more first.) 


Best regards,
Stian

---

