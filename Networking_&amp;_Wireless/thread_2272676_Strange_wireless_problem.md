---
title: "Strange wireless problem"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by Anton_Hristov on 2015-04-08
Hello, I did my first ubuntu installation a few days ago and since then I have been struggling to get the wi-fi adapter to work. I have tried most of the guides which I found on the Internet but nothing has worked so far. The only thing which almost worked is this guide : [http://itsfoss.com/fix-no-wireless-network-ubuntu/](http://itsfoss.com/fix-no-wireless-network-ubuntu/) . I did everything just like the guide says and the wireless started working. The only problem is that after reboot, I have to go to System Settings>>Software & Updates>>Additional Drivers and disable the network driver and the re-enable it again. I don't know why but this is the only way to get it to work. Is there anything I can do to make this re-enabling happen automatically when I boot the system?

P.S There are no problems with hibernation, it only happens when I reboot.

Thank you in advance!

---

### Post by michi1983 on 2015-04-08
Hi,

maybe you find something [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").
You might look at the **blacklist **option.

greetz

---

### Post by Bucky Ball on 2015-04-08
Frustrating indeed. When the network is up please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Which driver are you choosing from Additional Drivers?

---

### Post by Bucky Ball on 2015-04-08
Frustrating indeed. When the network is up please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Which driver are you choosing from Additional Drivers?

---

### Post by Anton_Hristov on 2015-04-08
This is the output of the "sudo lshw -C network" ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 38:2c:4a:37:bd:cc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:62 ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff
  *-network
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 30:10:b3:cd:4d:01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.135 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f7800000-f7807fff


```
I am choosing the Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary) this is the only one available.

---

### Post by Bucky Ball on 2015-04-08
Yep, the wl driver appears to be the correct one. I'm guessing that works fine when the wireless is actually up? Problem is the proprietary driver you're choosing isn't sticking on reboot. Hmm. Maybe another is kicking it out at boot.

Could you boot the machine and run the same command again, grab the output when the machine is not online, go through the rigmarole of getting online, and post the output here? Let's see if it shows another driver there.

You could also try manually installing the STA driver following the procedure at the top of the page [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29"). Reboot the machine and do it prior to engaging the one from Additional Drivers. This will avoid what I'm thinking is possibly happening at boot because, from that link:

> The bcmwl-kernel-source package should automatically blacklist the open source drivers so that the STA driver is the only one in use.

---

### Post by michi1983 on 2015-04-08
> **Bucky Ball said:**
> Problem is the proprietary driver you're choosing isn't sticking on reboot. Hmm. Maybe another is kicking it out at boot.

I posted a link two posts above where it is explained how to blacklist the "standard" driver that the propietary gets picked instead.

greetz

---

### Post by Anton_Hristov on 2015-04-08
This is what I got before reapplying the driver ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 38:2c:4a:37:bd:cc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:62 ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7800000-f7807fff


```
Looks like its not picking up the driver. I am new to Linux so can you give me some more detailed instructions on how to fix it?

Thanks in advance!

---

### Post by michi1983 on 2015-04-08
I think [here ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers")is everything explained.

---

### Post by Anton_Hristov on 2015-04-08
I got the idea but which ones do I want to disable in my case and which one should I leave enabled?

---

### Post by michi1983 on 2015-04-08
Oh, Bucky Ball already posted something.

> [COLOR=#000000]*The bcmwl-kernel-source package should automatically blacklist the open source drivers so that the STA driver is the only one in use.*[/COLOR]

Hm, so this means your bcmwl-kernel should blacklist it automatically. Don't know why it doesn't stick at a reboot :/

---

### Post by Anton_Hristov on 2015-04-08
I played around in the terminal and found out that the wireless starts working after executing these commands
 ```

sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe -r wl
sudo modprobe wl

```
I tried blacklisting b43 and brcmsmac by manually editing the [COLOR=#333333][FONT=UbuntuMono]*/etc/modprobe.d/blacklist-broadcom-wireless.conf* [/FONT][/COLOR][FONT=UbuntuMono]but it did not work[/FONT]
Is there a way to make the computer execute them automatically after booting?

EDIT: I fixed it by adding the commands to the /etc/rc.local file.

---

### Post by michi1983 on 2015-04-08
In this thread there is also the solution for blacklisting:
[http://ubuntuforums.org/showthread.php?t=2272384](http://ubuntuforums.org/showthread.php?t=2272384)

Answer #8

---

