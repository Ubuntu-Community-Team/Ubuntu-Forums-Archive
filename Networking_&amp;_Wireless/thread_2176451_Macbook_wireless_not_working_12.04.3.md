---
title: "Macbook wireless not working 12.04.3"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by Kopkins on 2013-09-24
I just installed 12.04.3 on my macbook, but I can't get the wireless working. 

```
lspci -vnn | grep -i network
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
```

According to [http://wireless.kernel.org/en/users/Drivers/b43#supported](http://wireless.kernel.org/en/users/Drivers/b43#supported) I need the b43 driver, or I can use the broadcom wl driver. 

So I installed b43 for mac,
```

sudo add-apt-repository ppa:mpodroid/mactel
sudo aptget update && sudo apt-get install firmware-b43-installer
```

Add b43 to /etc/modules

Reload b43 module. ```
rmmod b43
modprobe b43
```

Now the wireless is activated.

```
sudo lshw -c network

  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: e4:ce:8f:1b:66:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-30-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg

```

And it shows in networkmanager. But there are no networks listed, 

Rebooting doesn't help. 

Blacklist b43 module.

Install proprietary driver.

```
sudo apt-get install bcmwl-kernel-source
```

It builds fine. Make sure b43 isn't loaded. And load wl.```
rmmod b43 
modprobe wl
```
Module loads fine. Same thing, no networks, but the wireless card is activated and broadcasting.

I don't know if I missed something or what. I just need my wireless to work. And it works in MacOS and in Arch Linux.

Thanks,

Kopkins

---

### Post by Jonathan Precise on 2013-09-24
Try:

[http://ubuntuforums.org/showthread.php?t=2174511](http://ubuntuforums.org/showthread.php?t=2174511).

---

### Post by Kopkins on 2013-09-24
Interestingly enough, I can only connect to a network if I try connecting to it being hidden..

---

### Post by Jeevantha_Kule on 2013-09-24
thanks man

---

### Post by Kopkins on 2013-09-24
This actually doesn't work. It looks like it works at first, but every time I want to connect to a network I have to try to connect to some hidden network before any will appear, which is wrong. Does anyone have any more ideas?

---

### Post by Kopkins on 2013-09-26
Anyone?

---

### Post by Kopkins on 2013-09-27
I really need some help.

---

### Post by Jonathan Precise on 2013-09-27
> **Jonathan Precise said:**
> Try:

[http://ubuntuforums.org/showthread.php?t=2174511](http://ubuntuforums.org/showthread.php?t=2174511).

Try that.

---

### Post by Kopkins on 2013-09-27
Did you read through that thread? The OP settled for a fix that is really a workaround. I've had this work before, I don't know what's wrong now.

---

### Post by Kopkins on 2013-10-02
I'd really like to get this fixed. I have to reconnect to wifi several times a day and I hate having to wait 5 minutes to connect.

---

