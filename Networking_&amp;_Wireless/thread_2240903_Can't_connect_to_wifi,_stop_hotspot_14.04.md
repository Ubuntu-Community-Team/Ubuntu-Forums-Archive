---
title: "Can't connect to wifi, stop hotspot 14.04"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by rene13 on 2014-08-22
Hi all!,

I recently switched my HP laptop from Win7 to Ubuntu 14.04. Everything seems to run smooth except for one thing, I can't connect to wifi... sort of. When I installed Ubuntu it asked me to connect to a wifi network and I connected to my home wifi. The other day I went out and couln't connect to wifi. I turn on Hotspot in **All Settings > Network** and now **I can't turn it off**. When I'm at home I can connect automaically to my home network and I see other networks but when I'm at another location when **I turn on the computer Hotspot is enable and when I try to stop it the window crashes?** is there a way I can turn this off and be able to detect wifi networks?

Thanks for your help.

---

### Post by Rob Sayer on 2014-08-23
Be careful what you read ... I look here or on askubuntu before anywhere else.  Don't just so something that sounds more or less right.  I haven't actually set up a wifi node but here's something maybe useful:

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

I can't diagnose your wifi problem with some wifi nodes but I've had a very similar problem on my netbook previous to 14.04.  There are some *real* communications experts here though.

But no one can diagnose your issue without knowing what wireless hardware you have.  Paste this into terminal:

sudo lshw -C network

and post the output here.  Wrap it in [CODE] tags for readability.  While there are serious experts here, they're not paid to do this ...

---

### Post by jeremy31 on 2014-08-23
Lets see what is here ```
ls /etc/NetworkManager/system-connections
```

---

### Post by rene13 on 2014-08-24
Hi Rob,

Thanks for your response. I undersatnd that no one gets paid fro their advice and its from their own free will and for that I'm very thankfull.

I ran the command  in terminaland I got this. Also now my wifi wont connect at home too. :confused:

```

*-network
    description: Wireless interface
    product: Centrino wireless-N + WiMAX 6150
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: wlan0
    version: 67
    serial: 40:25:c2:b4:1c:a4
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver:iwlwifi driverversion=3.13.0-34-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
    resources: irq:49 memory:c0700000-c0701fff
*-network
    description: Ethernet interface
    product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 0
    bus info: pci@0000:04:00.0
    logical name: eth0
    version: 06
    serial: 10:1f:74:6a:4f:59
    size: 10Mbit/s
    capacity: 1Gbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000tb 1000tb-fd autonegotiation
    configuration: autonegoriation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
    resources: iqr:46 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
*-network
    description: Ethernet Interface
    physical id: 3
    logical name: wmx0
    serial: 64:d5:da:6b:29:5a
    capabilities: ethernet physical
    configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no

```

> **Rob Sayer said:**
> Be careful what you read ... I look here or on askubuntu before anywhere else.  Don't just so something that sounds more or less right.  I haven't actually set up a wifi node but here's something maybe useful:

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

I can't diagnose your wifi problem with some wifi nodes but I've had a very similar problem on my netbook previous to 14.04.  There are some *real* communications experts here though.

But no one can diagnose your issue without knowing what wireless hardware you have.  Paste this into terminal:

sudo lshw -C network

and post the output here.  Wrap it in [CODE] tags for readability.  While there are serious experts here, they're not paid to do this ...

---

### Post by rene13 on 2014-08-24
Hi Jeremy31,

When I ran this I got this

```

AmayaMedia Hotspot Wired connection 2

```

> **jeremy31 said:**
> Lets see what is here ```
ls /etc/NetworkManager/system-connections
```

---

### Post by varunendra on 2014-08-25
Welcome to the forums rene13! :)

Please try deleting the "Hotspot" file from your 'system-connections' directory -
```
sudo rm /etc/NetworkManager/system-connections/Hotspot
```
If it returns some error, post back the exact error message. If not, it means the file got deleted, and you should no more see the Hotspot connection in the Network Manager.

It should solve your hotspot mode problem, but if the connectivity problem remains, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by rene13 on 2014-08-26
Hi Varunendra,

I deleted the Hotspot file and this solved that issue.

Thank you all for your help. :p

---

### Post by varunendra on 2014-08-26
You're welcome!

Credit goes to jeremy31 who pointed us to the right direction. :)

---

### Post by bobyy747 on 2015-01-23
Thank You. this helped me a lot :-);-)

---

