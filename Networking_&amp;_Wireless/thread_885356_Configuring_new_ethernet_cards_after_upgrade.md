---
title: "Configuring new ethernet cards after upgrade"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by markdavidoff on 2008-08-10
I am running ubuntu server and i just upgraded my hardware.
As a result, my ethernet cards aren't being set up.

I typed in:

```
lspci | grep net
```

and it gave me:

```
00:04.0 Ethernet Controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
01:06.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

I also typed ```
ifconfig
```

and it only gave me a loopback device (no eth0 or eth1)

Help?

Also, as a side not, which ethernet device will perform better? The integrated nVidia one or the Realtek PCI Card?

thanks

---

### Post by cariboo on 2008-08-10
Pull the network card and use the nvidia on board network interface, it should work right out of the box. I beleive it uses the forcedeth module. To check to see if it is loaded, in a terminal type:

```
lsmod | grep force
```

If it is not loaded, try in a terminal:

```
sudo modeprobe forcedeth
```

Note: when inserting modules, if it is inserted correctly it will not echo anything back.

Jim

---

### Post by markdavidoff on 2008-08-10
forcedeth is loaded

I tried pulling the realtek card out anyways with no luck

the only eth device is still loopback

im gonna plug the realtek in again, as that didnt help

anything else to try?

---

### Post by markdavidoff on 2008-08-10
i fixed it temporarily:

I typed in
```
ifconfig -a
```

it listed 2 devices:
eth1
eth2

I typed:
```
ifconfig eth1 up
ifconfig eth2 up
```

to activate both devices

I then assigned IP Addresses:

```
ifconfig eth1 192.168.0.106
ifconfig eth2 192.168.0.107
```

I was then able to ping from the nVidia ethernet controller but not the realtek controller (after plugging in the cables, of course)

so I still have 3 questions:

1. how do i let the devices use DHCP instead of static addresses?
2. how can i get the realtek device to work?
3. It seems to undo everything i just did when I reboot. How do i get it to work properly?

EDIT:

After a re-install of ubuntu server, it worked out of the box, but i'm disappointed it didn't work straight after the upgrade

---

