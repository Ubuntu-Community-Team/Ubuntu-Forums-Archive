---
title: "Need wireless lan driver for HP PAVILION DV5215US"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by hyg71886 on 2007-08-09
I just erased windows and installed Ubuntu Linux 6.06:). My Notebook is the HP PAVILION DV5215US, It has a wireless router built into it by broadcom called Broadcom 54g 54Mbps Wi-Fi IEEE 802.11b/g. My ethernet port messes up alot, does anyone know where i can get the driver for this?

---

### Post by noob12 on 2007-08-09
Post these for starters
```

lspci -nn
lshw -C network

```

---

### Post by hyg71886 on 2007-08-09
> **noob12 said:**
> Post these for starters
```

lspci -nn
lshw -C network

```

ok i put it in and this is what i got back

hyg71886@Vanessa:~$ lspci -nn
0000:00:00.0 0600: 1002:5950 (rev 01)
0000:00:01.0 0604: 1002:5a3f
0000:00:05.0 0604: 1002:5a37
0000:00:13.0 0c03: 1002:4374
0000:00:13.1 0c03: 1002:4375
0000:00:13.2 0c03: 1002:4373
0000:00:14.0 0c05: 1002:4372 (rev 11)
0000:00:14.1 0101: 1002:4376
0000:00:14.3 0601: 1002:4377
0000:00:14.4 0604: 1002:4371
0000:00:14.5 0401: 1002:4370 (rev 02)
0000:00:14.6 0703: 1002:4378 (rev 02)
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:01:05.0 0300: 1002:5955
0000:06:02.0 0280: 14e4:4318 (rev 02)
0000:06:04.0 0607: 104c:8031
0000:06:04.2 0c00: 104c:8032
0000:06:04.3 0180: 104c:8033
0000:06:04.4 0805: 104c:8034
0000:06:06.0 0200: 10ec:8139 (rev 10)
hyg71886@Vanessa:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:ba:7d:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:233
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:38:4f:30
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=192.168.0.13 multicast=yes       resources: ioport:a000-a0ff iomemory:c020a400-c020a4ff irq:50
hyg71886@Vanessa:~$

What do i do know?

---

### Post by noob12 on 2007-08-09
I suggest you try to follow the instructions in this thread [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by hyg71886 on 2007-08-09
> **noob12 said:**
> I suggest you try to follow the instructions in this thread [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Ok, I followed it and now my wireless card works. I entered the wep key but i still cant connect wirelessly. Do i need to manually enter my ip address, subnet mask, and gateway address?

---

### Post by noob12 on 2007-08-10
No.  I'd suggest using NetworkManager or wicd.  NetworkManager ships with Ubuntu, so I'd try that first.  Usually you'll have a little dual-computer NetworkManager icon in the notification area in the upper right.  If you install the wpasupplicant package you can get WPA functionality as well.

For what you want now, left click on the Network Manager icon, select Manual Configuration.  Then find your wireless connection, select it, click Properties and put the connection in Roaming Mode.
OK.  Close.  Now right click on Network Manager, and select Enable Wireless.

Then one more left click and you should see your available nearby signals.  Select yours, you'll be prompted for the authentication information.

You may also be prompted for a "keyring" password.  This is not your WEP key.  It is a password that protects all of your various network keys.  If you are choosing a keyring password for the first time, I recommend choosing a password that is the same as your login password.

---

