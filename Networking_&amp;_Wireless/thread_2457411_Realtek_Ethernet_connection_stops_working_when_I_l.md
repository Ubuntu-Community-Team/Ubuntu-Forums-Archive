---
title: "Realtek Ethernet connection stops working when I leave it plugged in"
date: 2021-02-01
forum: Networking &amp; Wireless
---

### Post by New_buntu_89 on 2021-02-01
This is a weird issue that I've had for years, except now I kind of need to be able to leave my LAN wire plugged in.

I have a Toshiba Satellite P755. I have a dual boot with Windows. This issue doesn't happen with Windows.

When I turn it on, if the cable is plugged in, the ethernet port won't even be recognized by Ubuntu. I've tried plugging the cable in and out, and nothing changes. If I unplug the wire, turn the computer off completely, and then boot up, the ethernet port will be there, and I can get a wired connection by just plugging it back. 

I can plug it in without issues after the Mate logo goes away during bootup. At that point, it shows what looks like a console screen with a few short messages, saying that it's already loaded drivers and it's executing something like "*script/init-premount*". However, I can't leave it plugged in during shutdown.

This is the normal output of   **sudo lshw -C network**:

```

  *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 05
       serial: b8:70:f4:69:5b:4c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.54 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 74:e5:0b:06:f2:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-65-generic firmware=39.31.5.1 build 35138 ip=192.168.0.53 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:40 memory:f7e00000-f7e01fff

```


When it's failing, the output is the same for the Wireless interface, but the Ethernet block doesn't show up.

This looks to me like a driver issue, but I'm not sure. The Additional Drivers application doesn't show any new drivers, and "Install Firmware Package" didn't help either. Has anyone encountered this before? Is there a solution?

I'm hoping it can be solved with something like changing how or when the drivers are loaded, or adding a couple of lines to a script that runs during bootup. Any ideas to what that script is at the beginning?

---

### Post by kreon28 on 2021-02-03
I am using slightly different ethernet card ([FONT=monospace][COLOR=#000000]RTL8111/8168/8411[/COLOR]), [/FONT]but I have been using same driver as you. - r8169

I did notice similar errors. Although, I didn't unplugged the wire, my ethernet card sometimes did not connect to internet.
I had to reboot and try again.
Anyway, it did bother me a lot, so I installed by myself proper Realtek driver r8168 and the issue stopped.
Maybe that built-in r8169 driver is a problem?

---

### Post by slickymaster on 2021-02-03
*Thread moved to **Networking & Wireless**.*

---

### Post by New_buntu_89 on 2021-02-08
Sorry I disappeared, I was dealing with other issues from the new install.

> **kreon28 said:**
> 
Anyway, it did bother me a lot, so I installed by myself proper Realtek driver r8168 and the issue stopped.
Maybe that built-in r8169 driver is a problem?

How do you do that??

---

### Post by kreon28 on 2021-02-08
> **New_buntu_89 said:**
> How do you do that??

[https://askubuntu.com/a/1211166](https://askubuntu.com/a/1211166)

So i did:

[LIST=1]
[*]sudo apt-get install build-essential linux-headers-$(uname -r) 
[*]sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf' 
[*]Download latest tar.gz from [https://github.com/mtorromeo/r8168/releases](https://github.com/mtorromeo/r8168/releases) 
[*]tar xfvz r8168-X.XXX.XX.tar.gz (replace XXs with name of file you downloaded) 
[*]cd r8168-8.XXX.XX 
[*]sudo ./autorun.sh




These steps I had to run again after another kernel update.
Looks like that it is a permanent problem with that driver. 
You have different card that mine, so I suggest to backup the system if something would go wrong. 
[/LIST]

---

### Post by jeremy31 on 2021-02-08
> **kreon28 said:**
> [https://askubuntu.com/a/1211166](https://askubuntu.com/a/1211166)

So i did:

[LIST=1]
[*]sudo apt-get install build-essential linux-headers-$(uname -r) 
[*]sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf' 
[*]Download latest tar.gz from [https://github.com/mtorromeo/r8168/releases](https://github.com/mtorromeo/r8168/releases) 
[*]tar xfvz r8168-X.XXX.XX.tar.gz (replace XXs with name of file you downloaded) 
[*]cd r8168-8.XXX.XX 
[*]sudo ./autorun.sh




These steps I had to run again after another kernel update.
Looks like that it is a permanent problem with that driver. 
You have different card that mine, so I suggest to backup the system if something would go wrong. 
[/LIST]

This will likely cause ethernet to not work at all as the r8168 driver only works with a few chipsets the r8169 driver supports and they will likely need to do ```
sudo modprobe r8169
```
To have any ethernet at all

---

### Post by New_buntu_89 on 2021-02-09
So, here's what I've done so far. 

I tried installing the exact driver that kreon28 suggested, and it wasn't compatible, as jeremy31 said.

However,  I found Realtek's website, and I found a driver that had a more similar  model name (FE Ethernet LINUX driver r8101 for kernel up to 5.6) here:

  [https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)

The procedure was basically the same, and driver r8101 was compatible, but it didn't fix anything. 

This  page also has a similar model name, but it seems to be for a different  OS, and I couldn't find a way to install these drivers. If you guys know  a good way to test them, I'll give it a shot:

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100m-fast-ethernet-pci-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100m-fast-ethernet-pci-software)


So, what if the driver is *not* the issue? I did lshw without specifications, and found this:
```

        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL810xE PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 05
                serial: b8:70:f4:69:5b:4c
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169  duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.53 latency=0  link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:16 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

My (limited) understanding is that this means that the Ethernet port depends on that PCI bridge. Is there a way to reset that particular PCI bridge? Could there be a problem with its driver? Is it possible to send any commands to it to have it re-check its connections?

---

