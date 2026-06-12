---
title: "Trouble with wireless"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by bbbgscott on 2010-02-26
I just got Ubuntu installed, but for some reason, the system won't recognize my wireless card. I have a GeForce 8700M GT card, and I have the proprietary driver installed, but the card just doesn't work.

Any help would be greatly appreciated.

---

### Post by Peter09 on 2010-02-26
Can you post the output of the command
 
```
lshw -C network
```

---

### Post by bbbgscott on 2010-02-26
Code reads as follows
 
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0efc000-f0efffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:55:d3:2e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5754m-v3.23 ip=192.168.2.13 latency=0 multicast=yes
       resources: irq:30 memory:f0bf0000-f0bfffff
```

---

### Post by Peter09 on 2010-02-26
Go to synaptic package manager and search for BCM there are two installable apps in there which I think support your device. Also check in System->Admin->hardware drivers to see if there is a driver waiting to be enabled.

---

### Post by bbbgscott on 2010-02-26
The Broadcom STA driver is already enabled, and the only other package on Synaptic is for a different model.

---

### Post by spectralblue on 2010-02-26
> **bbbgscott said:**
> The Broadcom STA driver is already enabled, and the only other package on Synaptic is for a different model.

Does it say something like "The driver is currently activated but not in use"?

If it does, disable the driver, reboot, enable the driver, then reboot again, and see if that works out for you.

---

### Post by bbbgscott on 2010-02-26
That seemed to help, because the wireless showed up after reenabling after the first reboot, but I couldn't actually connect to any of my networks, and after the second reboot, the wireless card wasn't working again.

---

### Post by spectralblue on 2010-02-26
Does the broadcom sta say it's activated if you go to System - Administration - Hardware Drivers? You want it to say activated, but if it says "Activated but not in use" you have to so the steps I've mentioned. 

If it is activated though, is your wireless activated both in the network manager AND the wireless switch on your device (like some notebooks have a switch to enable or disable wireless)?

Go to the terminal and type iwconfig when your driver is activated and paste the results here if it's still not working.

---

### Post by sandyd on 2010-02-26
```

sudo apt-get --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source

```

---

### Post by marbertone on 2010-02-26
I don't know if it'll help, nevertheless I try to give a hand :)
Connect via cable and install wicd , it will automatically replace network-manager. I had a similar problem. After installing Ubuntu, network-manager worked well (I've got a sony vaio), but after rebooting no wireless network were present anymore. With wicd everything goes perfectly.
Perhaps it'll help!
Cheers,
Mario Alberto

---

### Post by spectralblue on 2010-02-27
> **marbertone said:**
> I don't know if it'll help, nevertheless I try to give a hand :)
Connect via cable and install wicd , it will automatically replace network-manager. I had a similar problem. After installing Ubuntu, network-manager worked well (I've got a sony vaio), but after rebooting no wireless network were present anymore. With wicd everything goes perfectly.
Perhaps it'll help!
Cheers,
Mario Alberto

I second that! Wicd works better than the default gnome network manager in my opinion.

---

